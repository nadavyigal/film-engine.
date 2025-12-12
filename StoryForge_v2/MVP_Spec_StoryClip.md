# MVP Spec — StoryClip (Weeks 3-6)
Goal: Deliver a minimal product that 10 pre-paid users can use to generate consistent, multi-scene clips and export a simple sequence.

## Scope (Must-Have)
1) **Auth + Credits**
- Email/password auth via Supabase.
- Credit counter (20 scenes per user for beta); manual top-ups by admin.

2) **Character Reference**
- Upload 3-5 reference images; store in Supabase Storage.
- Generate `character_id` and store metadata (file paths, created_at, user_id).
- Surface a reusable “character card” in the UI.

3) **Scene Generation**
- Prompt input + optional style preset selector (prompt fragment).
- Inject character reference into Runway Gen-4 API call (fallback: Pika).
- Return a single video option per request; allow up to 3 regenerations per scene.
- Store scene metadata (prompt, style preset, character_id, asset URL, render count).

4) **Timeline**
- Thumbnails of scenes in order; drag-drop reorder.
- Simple concatenated export to MP4 (serverless function with ffmpeg).
- Download link + basic progress state.

5) **Admin Panel (Lean)**
- View users, remaining credits, and scene counts.
- Manually add credits and toggle feature flags.

## Out of Scope (For V1)
- Custom ML Brains, marketplace, collaboration, mobile app, multi-format export, voice/lipsync, fine-grain sliders.

## Non-Functional
- Cost target: <$500/month infra at 50 users.
- Availability: acceptable to be single-region; graceful error messages > HA.
- Latency: <30s perceived per scene (queue UI with status).

---

## Unit Economics Model

### Cost Per Scene (Estimated)
| Provider | Cost/5s clip | Notes |
|----------|-------------|-------|
| Runway Gen-4 | ~$0.20-0.50 | Varies by resolution, API tier |
| Pika | ~$0.15-0.30 | Cheaper but lower consistency |
| Storage (Supabase) | ~$0.01 | Negligible at MVP scale |
| Export (ffmpeg) | ~$0.02 | Vercel serverless compute |
| **Total/Scene** | **~$0.25-0.55** | Use $0.40 for planning |

### Pricing Viability Check
| Plan | Price | Scenes | Cost @ $0.40/scene | Gross Margin |
|------|-------|--------|-------------------|--------------|
| Free | $0 | 5 | $2.00 | -$2.00 (marketing cost) |
| Creator | $20 | 50 | $20.00 | $0.00 (breakeven) |
| Pro | $50 | 200 | $80.00 | -$30.00 (PROBLEM) |

### ⚠️ PRICING RISK IDENTIFIED
At current estimates, **Pro tier loses money**. Mitigations:
1. **Negotiate volume pricing** with Runway (target $0.15/scene at 10K/month)
2. **Reduce Pro scenes** to 100 (gives $10 margin)
3. **Add overage pricing**: $0.50/scene beyond plan limits
4. **Cache/reuse**: Store rendered scenes; same prompt = no re-render

### Revised Pricing Recommendation
| Plan | Price | Scenes | Overage | Target Margin |
|------|-------|--------|---------|---------------|
| Free | $0 | 5 | N/A | Marketing cost |
| Creator | $20 | 40 | $0.60/scene | ~$4 (20%) |
| Pro | $50 | 100 | $0.50/scene | ~$10 (20%) |

### Break-Even Analysis
- **Fixed costs/month:** ~$200 (Vercel Pro $20 + Supabase Pro $25 + Runway minimum + misc)
- **Break-even:** 10 Creator users OR 4 Pro users
- **Target (Phase 3):** 50 paying users = $1,500 MRR → $500 gross profit after API costs

## Tech Stack
- Frontend: Next.js 14 (App Router), Tailwind, shadcn/ui.
- Backend: Next.js API routes, Supabase (Postgres/Auth/Storage).
- AI: Runway Gen-4 API primary; Pika as fallback.
- Media processing: ffmpeg in serverless (or edge if allowed size).
- Deploy: Vercel (frontend + API), Supabase managed.

---

## Technical Architecture

### System Architecture
```
┌─────────────────────────────────────────────────────────────────┐
│                         CLIENT (Next.js)                        │
│  ┌─────────┐ ┌─────────────┐ ┌──────────┐ ┌─────────────────┐  │
│  │  Auth   │ │  Character  │ │  Scene   │ │    Timeline     │  │
│  │  Pages  │ │   Upload    │ │Generator │ │   + Export      │  │
│  └────┬────┘ └──────┬──────┘ └────┬─────┘ └───────┬─────────┘  │
└───────┼─────────────┼─────────────┼───────────────┼────────────┘
        │             │             │               │
        ▼             ▼             ▼               ▼
┌─────────────────────────────────────────────────────────────────┐
│                    API ROUTES (Next.js)                         │
│  /api/auth  /api/characters  /api/scenes  /api/timeline         │
│                    /api/export  /api/admin                      │
└───────────────────────────────┬─────────────────────────────────┘
                                │
        ┌───────────────────────┼───────────────────────┐
        ▼                       ▼                       ▼
┌───────────────┐      ┌───────────────┐      ┌───────────────┐
│   Supabase    │      │  Runway API   │      │  Vercel Blob  │
│  (Auth/DB)    │      │  (Gen-4) +    │      │  + ffmpeg     │
│               │      │  Pika (backup)│      │  (export)     │
└───────────────┘      └───────────────┘      └───────────────┘
```

### Database Schema (Supabase Postgres)
```sql
-- Users (extends Supabase auth.users)
CREATE TABLE profiles (
  id UUID PRIMARY KEY REFERENCES auth.users(id),
  email TEXT NOT NULL,
  credits_remaining INT DEFAULT 20,
  plan TEXT DEFAULT 'beta', -- beta, free, creator, pro
  created_at TIMESTAMPTZ DEFAULT NOW(),
  updated_at TIMESTAMPTZ DEFAULT NOW()
);

-- Characters
CREATE TABLE characters (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id UUID REFERENCES profiles(id) ON DELETE CASCADE,
  name TEXT NOT NULL,
  description TEXT,
  reference_urls TEXT[], -- Array of storage URLs
  prompt_fragment TEXT, -- Auto-generated or edited
  created_at TIMESTAMPTZ DEFAULT NOW()
);

-- Projects (container for scenes)
CREATE TABLE projects (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id UUID REFERENCES profiles(id) ON DELETE CASCADE,
  title TEXT NOT NULL,
  status TEXT DEFAULT 'draft', -- draft, exporting, exported
  created_at TIMESTAMPTZ DEFAULT NOW(),
  updated_at TIMESTAMPTZ DEFAULT NOW()
);

-- Scenes
CREATE TABLE scenes (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  project_id UUID REFERENCES projects(id) ON DELETE CASCADE,
  character_id UUID REFERENCES characters(id),
  prompt TEXT NOT NULL,
  style_preset TEXT,
  video_url TEXT,
  thumbnail_url TEXT,
  order_index INT NOT NULL,
  render_count INT DEFAULT 0,
  status TEXT DEFAULT 'pending', -- pending, generating, completed, failed
  provider TEXT, -- runway, pika
  render_time_ms INT,
  created_at TIMESTAMPTZ DEFAULT NOW()
);

-- Exports
CREATE TABLE exports (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  project_id UUID REFERENCES projects(id) ON DELETE CASCADE,
  output_url TEXT,
  status TEXT DEFAULT 'pending', -- pending, processing, completed, failed
  created_at TIMESTAMPTZ DEFAULT NOW(),
  completed_at TIMESTAMPTZ
);

-- Credit Transactions (audit log)
CREATE TABLE credit_transactions (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id UUID REFERENCES profiles(id),
  amount INT NOT NULL, -- negative = deduct, positive = add
  reason TEXT NOT NULL, -- scene_generate, admin_add, purchase
  idempotency_key TEXT UNIQUE,
  created_at TIMESTAMPTZ DEFAULT NOW()
);

-- Indexes
CREATE INDEX idx_scenes_project ON scenes(project_id);
CREATE INDEX idx_characters_user ON characters(user_id);
CREATE INDEX idx_projects_user ON projects(user_id);
```

### API Endpoints
```
Authentication:
POST /api/auth/signup     - Email/password signup
POST /api/auth/login      - Login
POST /api/auth/logout     - Logout
GET  /api/auth/me         - Current user + credits

Characters:
POST /api/characters          - Create character (multipart upload)
GET  /api/characters          - List user's characters
GET  /api/characters/:id      - Get character details
DELETE /api/characters/:id    - Delete character

Projects:
POST /api/projects            - Create project
GET  /api/projects            - List user's projects
GET  /api/projects/:id        - Get project with scenes
DELETE /api/projects/:id      - Delete project

Scenes:
POST /api/scenes              - Generate scene (deducts credit)
  Body: { project_id, character_id, prompt, style_preset }
PUT  /api/scenes/:id/regenerate - Regenerate (max 3x, deducts credit)
PUT  /api/scenes/:id/reorder    - Update order_index
DELETE /api/scenes/:id          - Delete scene

Timeline:
PUT  /api/timeline/:project_id  - Bulk reorder scenes
  Body: { scene_ids: string[] }

Export:
POST /api/export/:project_id    - Start export (concat scenes)
GET  /api/export/:export_id     - Check export status + download URL

Admin:
GET  /api/admin/users           - List users with stats
PUT  /api/admin/credits/:user_id - Add credits manually
PUT  /api/admin/flags           - Toggle feature flags
```

### Security Model
- **Auth:** Supabase JWT tokens; verify on every API route
- **RLS:** Row Level Security on all tables (user can only access own data)
- **Rate Limiting:** 10 scene generations/minute/user (prevent abuse)
- **Input Validation:** Zod schemas on all API inputs
- **CORS:** Strict origin whitelist (production domain only)
- **Secrets:** All API keys in Vercel env vars, never client-side
- **Idempotency:** Credit deductions use idempotency tokens to prevent double-charge

## Success Criteria (for this MVP)
- 10 pre-paid users onboarded.
- Each generates ≥10 scenes; ≥6/10 say they would pay $20/month post-beta.
- Subjective consistency rated “good/great” by 8/10.
- Export flow used successfully by ≥8/10 users.

## Instrumentation
- Events: auth, character_upload, scene_generate_request, scene_generate_success/fail, regenerate, timeline_reorder, export_start/success/fail.
- Properties: user_id, character_id, style_preset, prompt_length, render_time_ms, credits_remaining.
- Dashboards: scenes/user, exports/user, failures by provider, credit burn.

## Risks & Mitigations (Build Phase)
- **Runway latency/cost spikes:** enforce regen limit, queue UI, provider fallback.
- **Credit leakage:** server-side credit decrement with idempotency tokens.
- **Export failures:** chunk renders; retry on fail; expose download even if concat fails.
- **Scope creep:** change control requires hitting MVP success criteria first.
