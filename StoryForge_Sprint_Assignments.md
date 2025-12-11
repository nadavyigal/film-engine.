# StoryForge Sprint Assignments (Internal Tracker Staging)
## Use to bulk-assign after importing CSVs

---

## Sprint 1 (Alpha Core Foundations)
- Scene Builder: Prompt enhancement; generate options; lock/unlock; timeline reorder — **Owner:** Frontend Lead; **Flags:** none.
- Continuity: Character create + embeddings; auto-inject; consistency score (baseline) — **Owner:** ML/Backend Lead; **Flags:** none.
- Export: MP4 16:9; safe-zone overlay 16:9 — **Owner:** Backend/Frontend Lead; **Flags:** none.
- Brains: Gallery UI; 3 brains (delivery setup) — **Owner:** ML/Product Lead; **Flags:** none.
- Routing: Runway primary with health checks — **Owner:** Backend/ML Lead; **Flags:** none.
- Safety: Prompt moderation + NSFW; mature-aesthetic toggle — **Owner:** Backend/Policy Lead; **Flags:** mature_aesthetic toggle (OFF by default).
- Analytics: Core events (scene_generated incl. provider_route/cache_hit/safety_mode; safety_setting_changed); tracing with request IDs — **Owner:** Data/Eng Lead; **Flags:** none.
- QA/Perf: Editor QA plan; UI perf instrumentation — **Owner:** QA Lead; **Flags:** none.

## Sprint 2 (Alpha Polish & Beta Seeds)
- Scene Builder: Storyboard preview behind Beta flag — **Owner:** Frontend Lead; **Flags:** storyboard_preview (OFF by default).
- Continuity: Dashboard surfacing issues; continuity v2 start; consistency validation setup — **Owner:** ML/Backend Lead; **Flags:** none.
- Export: Queue status/retries; vertical/cinematic presets groundwork — **Owner:** Backend/Frontend Lead; **Flags:** vertical_exports (OFF).
- Routing: Sora/Kling fallback; Stability storyboard fallback; fallback alerts — **Owner:** Backend/ML Lead; **Flags:** storyboard_fallback (ON), provider_fallbacks (ON).
- Brains/Formats: 5 templates with beats; beat→scene linkage; continue brains to 8 — **Owner:** ML/Product Lead; **Flags:** style_mixing (OFF; Pro/Studio only).
- Safety: Watermark/origin; audit log overrides — **Owner:** Backend/Policy Lead; **Flags:** mature_aesthetic toggle remains OFF by default.
- Billing/Promos (scaffold only, OFF): Stripe plans, credit wallet scaffolding — **Owner:** Backend/Frontend Lead; **Flags:** billing_enabled (OFF), promos_enabled (OFF).
- Analytics/Observability: Dashboards; alerts (gen p95>90s, export<80%, fallback>20%, payments>3%) — **Owner:** Data/Eng Lead; **Flags:** none.
- Infra/Perf: Redis L1 + vector L2; perf tuning toward p95<90s — **Owner:** DevOps/Backend Lead; **Flags:** none.
- QA: Export SLO monitoring setup; continuity QA scenarios — **Owner:** QA Lead; **Flags:** none.

## Notes for Tracker Setup
- After importing `StoryForge_JIRA_Epics.csv` and `StoryForge_Epic_Stories.csv`, bulk-assign owners per above.
- Apply feature flags: `storyboard_preview`, `style_mixing`, `mature_aesthetic`, `vertical_exports`, `billing_enabled`, `promos_enabled`.
- Keep billing/promos OFF in Alpha/Beta; style_mixing gated to Pro/Studio only; mature_aesthetic OFF by default.
- Verify environments have vendor keys before starting Sprint 1 (see vendor key doc).
