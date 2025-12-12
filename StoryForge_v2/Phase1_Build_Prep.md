# Phase 1 Build Prep (Founder-Friendly, Low-Talk Mode)

Goal: Start build setup while live calls are paused. Outcome: repo scaffolded, Supabase schema applied, storage ready, env vars defined.

## 1) Repo Scaffold (Next.js 14 + TS + Tailwind)
- Run locally (Node 18+): `npx create-next-app@latest storyclip --ts --app --tailwind --use-pnpm`
- Install UI kit: `npx shadcn-ui@latest init` (select default Tailwind config)
- Install Supabase client: `pnpm add @supabase/supabase-js`

## 2) Env Vars (dev: `.env.local`; prod: Vercel Project Settings)
- SUPABASE_URL=
- SUPABASE_ANON_KEY=
- SUPABASE_SERVICE_ROLE_KEY= (server-only; never to client)
- RUNWAY_API_KEY=
- PIKA_API_KEY=
- NEXT_PUBLIC_SITE_URL= (for auth redirects)
- NEXTAUTH_SECRET= (or equivalent secret if using NextAuth; otherwise generate a random 32+ char string for session encryption)

## 3) Supabase Database Setup
- In Supabase SQL editor, paste and run `supabase_schema.sql` from this folder (creates profiles, characters, projects, scenes, exports, credit_transactions + indexes).
- Enable RLS on all tables; add simple policies for row ownership:
  - profiles: user can select/update own row (`auth.uid() = id`)
  - characters/projects/scenes/exports/credit_transactions: user can select/insert/update/delete where `auth.uid() = user_id` (or the project’s user_id via join where applicable)
- Create storage bucket `characters` (private) for reference images; use signed URLs.

## 4) Minimal Vercel Setup
- Create a Vercel project; connect the repo.
- Add env vars from section 2.
- Set build command `pnpm run build`; output `.next`.

## 5) Next.js App Router Stubs (to build in Week 3)
- `/upload` (character upload + metadata)
- `/scenes` (prompt input, style preset select, single render + up to 3 regens)
- `/timeline` (drag/drop order; show thumbnails)
- `/export` (trigger serverless export + download link)
- `/admin` (list users, credits, manual top-up)

## 6) Serverless Endpoints (outline now, wire in Week 3-4)
- `POST /api/characters` (upload refs -> storage; save character record)
- `POST /api/scenes` (validate prompt/style; deduct credit via idempotency key; call Runway; store scene)
- `POST /api/scenes/:id/regenerate` (same as above, max 3)
- `POST /api/export` (ffmpeg concat from scene URLs; store export record; return download URL)
- `POST /api/credits/admin-add` (protected; add credits)

## 7) Passive Monitoring (keep desk research alive without calls)
- Check the saved Reddit/Twitter queries daily; log new high-severity complaints in `Customer_Research_Log.md`.
- If patterns change, update the relevant pattern summary block.

## 8) When Ready to Resume Calls
- Use the follow-up snippets in `Customer_Research_Log.md` with your Calendly/link; aim for 5-8 calls before Phase 2.
