# StoryForge Sprint Plan (Initial 2 Sprints)
## Goal: Alpha readiness (Scene Builder, Character Lock/Continuity v1, Export MP4 16:9, initial brains/templates)

---

## Sprint 1 (Alpha Core Foundations)
**Focus:** Scene Builder core flow, Character creation/lock, Export MP4 16:9, initial brains/templates scaffolding, routing groundwork.

- Scene Builder & Timeline
  - Prompt enhancement integration (brain + beat + continuity) — M
  - Generate options + “generate more” — M
  - Lock/unlock with version history — M
  - Timeline reorder UI + persistence — S

- Continuity & Character Lock
  - Character create with embeddings (upload/generate) — M
  - Auto-inject characters into prompts — M
  - Consistency scoring per scene (baseline) — M

- Export Engine
  - MP4 16:9 export (Alpha) — M
  - Safe-zone preview overlay (16:9) — S

- Cinematic Brains & Formats
  - Brain gallery UI with previews — M
  - Ship 3 brains for Alpha (delivery setup) — L (start)

- Provider Routing & Fallbacks
  - Primary Runway routing with health checks — M

- Safety & Compliance
  - Prompt moderation + NSFW filter — M
  - Mature-aesthetic toggle (stored/logged) — S

- Analytics & Observability
  - Implement event taxonomy core (scene_generated with provider_route/cache_hit/safety_mode; safety_setting_changed) — M
  - Tracing with request IDs — M

- QA/Perf
  - QA test plan for editor flows — S
  - UI perf instrumentation (p95 latency) — S

**Exit for Sprint 1:** User can create/lock a scene with character continuity, generate options, reorder timeline; export MP4 16:9; see 3 brains selectable; safety enforced; core analytics emitting; routing stable on primary.

---

## Sprint 2 (Alpha Polish & Beta Seeds)
**Focus:** Continuity v1 polish, more export presets groundwork, routing/fallback, marketplace/billing prep (flagged off), dashboards/alerts, perf targets.

- Scene Builder & Timeline
  - Storyboard preview behind Beta flag — M

- Continuity & Character Lock
  - Continuity dashboard (issues surfaced) — M
  - Continuity v2 tracking start (location/time/props) — L (start)
  - Consistency >90% validation setup — S

- Export Engine
  - Render queue status + retries — M
  - Add vertical/cinematic presets groundwork (config, UI) — M (flag off)

- Provider Routing & Fallbacks
  - Sora/Kling fallback paths with circuit breaker — M
  - Storyboard fallback via Stability — M
  - Log provider_route + safety_mode; alert on fallback >20% — S

- Cinematic Brains & Formats
  - Format templates with beats (5) — M
  - Beat-to-scene linkage in timeline — M

- Safety & Compliance
  - Watermark/origin tracking — M
  - Audit log for safety overrides — S

- Billing, Credits, Promotions (flagged off)
  - Stripe plans scaffolding; entitlements — M
  - Credit wallet metering scaffolding — M

- Analytics & Observability
  - Dashboards (Activation/Reliability/Revenue/Engagement) — M
  - Alerts (p95 gen >90s; export <80%; provider fallback >20%; payments >3%) — S

- Infrastructure & Performance
  - Redis L1 + vector L2 caching deployment — M
  - Performance tuning toward p95 gen <90s — M

- QA/Perf
  - Export success SLO monitoring setup — S
  - Continuity/consistency QA scenarios — S

**Exit for Sprint 2:** Beta seeds in place (storyboard flaggable, format templates live, routing fallbacks working, queue visible), safety/watermarking in place, dashboards/alerts live, caches deployed, billing/credits scaffolded but gated.

---

## Dependencies & Prep
- Vendor keys/quotas: Runway primary; Sora/Kling fallback; Stability for storyboard.
- Feature flags: storyboard preview, style mixing, mature aesthetic, vertical exports, billing on/off.
- Seed data: 3 brains; 5 templates; sample characters for QA.
- Billing test accounts and promo codes prepared (flag off to users).
- Support/DMCA flow ready; watermark pipeline configured.

## DoD (per story)
- Code + tests (unit/e2e where applicable).
- Telemetry/events implemented per analytics spec.
- SLO checks where relevant (export, latency).
- Feature flags applied where staged delivery is required.
- QA signoff for user-facing flows.
