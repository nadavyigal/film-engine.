# StoryForge Product Requirements (PRD)
## Version 1.0 | December 2024 | Confidential

---

# 1. Purpose
- Align stakeholders on the next 6 months to reach PMF ($50K MRR, 5K users).
- Define user value, scope, acceptance criteria, and release gates for Alpha (M2), Beta (M4), and Public Launch (M6).
- Serve as the single reference for engineering, design, marketing, and GTM teams.

---

# 2. Goals & Success Metrics
- **North Star:** Completed projects/user/month target 2.5 by Month 6.
- **Activation:** 40% of new users complete their first project within 48 hours.
- **Engagement:** DAU/MAU 25%; avg scenes per project ≥ 6.
- **Quality:** Character consistency >90%; avg iterations per scene <3; p95 generation time <90s.
- **Monetization:** Free-to-paid conversion ≥ 8%; Month 6 MRR ≥ $50K.
- **Satisfaction:** NPS ≥ +40.

---

# 3. Target Users
- **Storyteller (Primary):** TikTok/YouTube creators making serialized content; needs fast, coherent story production with consistent characters.
- **Marketer (Secondary):** Brand/D2C marketer producing high-volume campaign content; needs speed, brand-safe outputs, and multi-format export.
- **Filmmaker (Tertiary):** Scripted storyteller with limited budget; needs proof-of-concept visuals with continuity.

---

# 4. Releases & Gates
## Alpha (end M2)
- **Scope:** Scene Builder v1, 3 brains (Thriller, K-Drama, TikTok Native), character locking v1, single-format export (MP4 16:9), basic project CRUD.
- **Exit Criteria:** >85% character consistency; time-to-first-lock <5 min; 100 creators onboarded with weekly feedback.

## Beta (end M4)
- **Scope:** 8 brains, 5 format templates, continuity v2 (location/time-of-day/props), export presets (TikTok 9:16, YouTube 16:9, Reels 9:16), onboarding v1, billing foundations (no charges).
- **Exit Criteria:** >90% character consistency; p95 generation <90s; export success >80%; cache hit rate >30%; 1K beta users active.

## Public Launch (end M6)
- **Scope:** Billing live (Creator/Pro/Studio tiers), marketplace v1 (brains/templates/character packs), credit system, usage limits, abuse prevention, mobile-responsive polish.
- **Exit Criteria:** $50K MRR; 5K users; 400+ paying; uptime 99.5%; launch checklist green.

---

# 5. Functional Requirements
Each requirement lists **(Stage)** where it must be delivered.

## 5.1 Project Foundations
- Create/list/update/delete projects with types (series, short film, quick clip). **(Alpha)**
- Store project-wide brain, format, settings, and scene order; reorder via timeline. **(Beta)**
- Project duplication and template-based creation. **(Beta)**
- Permissions: owner-only in Alpha/Beta; invite collaborators in future. **(Post-launch)**

## 5.2 Cinematic Brains
- Brain gallery with visual previews and description; selection applies globally. **(Alpha)**
- Brain parameters injected into prompt (shot language, color grading, pacing). **(Alpha)**
- Minimum 8 brains live by Beta; support style metadata for marketplace items. **(Beta)**
- Style mixing (two-brain blend) experimentation behind flag. **(Post-launch)**

## 5.3 Format Templates
- Gallery of 5 templates (6-episode mini-series, 3-act, TikTok series, explainer, brand story). **(Beta)**
- Generate beats and scene starters from user story seed; editable beats. **(Beta)**
- Beat-to-scene linkage tracked in project timeline; gaps surfaced. **(Beta)**
- Custom templates from marketplace items. **(Post-launch)**

## 5.4 Character Locking & Continuity
- Create characters via upload or AI generation; store embeddings and appearance descriptors. **(Alpha)**
- Auto-inject character refs into every generation; report consistency score per scene. **(Alpha)**
- Continuity v2: location persistence, time-of-day, basic prop tracking. **(Beta)**
- Continuity dashboard surfacing issues and suggesting fixes. **(Beta)**
- Voice references and lip-sync alignment. **(Post-launch)**
- Project settings include a “mature aesthetic” toggle that relaxes style filters (not legality/ToS) for horror/thriller, with all overrides logged. **(Launch)**

## 5.5 Scene Builder (Core Editor)
- Prompt entry with system enhancement (brain + beat + continuity context). **(Alpha)**
- Generate 2-3 options per request; allow “generate more” and side-by-side compare. **(Alpha)**
- Fine-tuning controls (lighting, camera, mood, pacing) with safe ranges. **(Alpha)**
- Lock/unlock scenes; preserve version history. **(Alpha)**
- Storyboard/keyframe preview prior to final synthesis. **(Beta)**
- In-canvas comments and simple annotations. **(Post-launch)**

## 5.6 Export Engine
- Export locked scenes to MP4 16:9 (Alpha); add TikTok 9:16, Reels 9:16, Stories 9:16, Cinematic 2.39:1 by Beta. **(Alpha+Beta)**
- Safe-zone preview and crop guidance before render. **(Beta)**
- Render queue with status + retries; delivery via CDN links. **(Beta)**
- Direct publish to TikTok/YouTube APIs with OAuth. **(Post-launch)**

## 5.7 Performance & Reliability
- p95 generation <90s (Beta); <75s stretch for launch.
- Export success >80% (Beta) and >90% (Launch).
- Autosave project state; recover from tab close. **(Beta)**
- Rate limits and abuse controls tuned for launch. **(Launch)**

## 5.8 Billing & Marketplace
- Stripe integration with Creator ($19/50 scenes), Pro ($49/200 scenes), Studio ($199/unlimited + API). **(Launch)**
- Credit wallet and usage metering across generation and export. **(Launch)**
- Marketplace browse/purchase for brains, formats, character packs; payout tracking. **(Launch+)**

---

# 6. Non-Functional Requirements
- **Security & Privacy:** JWT auth; RBAC; data encrypted at rest (AES-256) and in transit (TLS 1.3); secrets in vault/SSM.
- **Content Safety:** Prompt moderation; NSFW detection on outputs; watermarking and origin tracking; DMCA workflow; “mature aesthetic” toggle logged and auditable.
- **Scalability:** Multi-AZ infra; auto-scaling services; CDN for media; caching (Redis L1, vector L2).
- **Observability:** Tracing for generation pipeline; logs with request IDs; dashboards for latency, failures, and cache hit rates.
- **Availability:** 99.0% (Alpha/Beta), 99.5% (Launch).
- **Compliance (aspirational):** SOC 2 readiness checklist started by Beta; PII handling documented.

---

# 7. Instrumentation & Data
- Track funnel: sign-up + first prompt + first locked scene + first export + paid conversion.
- Core events (see analytics spec): project_created, brain_selected, format_selected, character_locked, scene_generated, scene_locked, export_started/export_succeeded, payment_succeeded, safety_setting_changed.
- Standard identifiers: user_id, project_id, scene_id, brain_id, format_id; client_ts and server_ts; app_version.

---

# 8. Dependencies & Assumptions
- Third-party model APIs remain stable; multi-provider router available for failover.
- GPU budget supports target generation times; caching reduces costs by ≥50%.
- Legal: NDAs for Alpha users; content policy approved before launch.
- Hiring completed per execution plan (ML, Frontend, DevOps, Marketing).

---

# 9. Risks & Mitigations
- Character consistency below target → increase reference frames, fallback regeneration, tighter scoring thresholds.
- Generation latency too high → expand caching, pre-gen predicted scenes, optimize queueing.
- Model provider outages → failover routing + graceful degradation to storyboard-only mode.
- Abuse or unsafe content → stronger moderation, rate limits, identity verification for heavy users.

---

# 10. Decisions (locked)
- Provider mix: Runway primary; Sora/Kling as fallbacks; Stability image-to-video for storyboard fallback during throttling.
- Style mixing access: gated behind Pro/Studio; small Alpha flag for ~20 power users.
- Safety defaults: strict by default; “mature aesthetic” toggle relaxes only style filters and is fully logged.
- Mobile scope at launch: preview + light controls (approve/lock, request variation, trigger export); full editing remains desktop.
