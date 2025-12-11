# StoryForge Epic Definitions (JIRA-ready)
## December 2024 | Use with bmad PM templates

Each epic includes: Summary, Description, Acceptance Criteria, Dependencies, Owners (suggested BMad agent).

---

## Epic: Scene Builder & Timeline
- Summary: Build the core scene editor with prompt enhancement, options, locking, and timeline control.
- Description: Deliver prompt enhancement (brain+beat+continuity), 2–3 options with “generate more,” lock/unlock with version history, and timeline reorder; storyboard preview behind Beta flag; p95 UI latency <200ms on core actions.
- Acceptance Criteria:
  1) Prompt enhancement applied on every generate; 2–3 options returned; “generate more” works.
  2) Lock/unlock persists versions; timeline reorder saves order.
  3) Storyboard preview feature-flagged for Beta.
  4) p95 UI latency <200ms for generate request/lock actions.
- Dependencies: Continuity API, Brain/Format APIs, video player, feature flag service, UX mocks.
- Owners/Agents: Frontend/Full-stack; BMad *ux-expert, *dev, *qa.

## Epic: Continuity & Character Lock
- Summary: Ship character consistency and continuity across scenes.
- Description: Character create (upload/generate) with embeddings; auto-injection into prompts; per-scene consistency score; continuity v2 (location/time/props) by Beta; dashboard surfacing issues; hit >90% consistency by Launch.
- Acceptance Criteria:
  1) Characters stored with embeddings/appearance; reference images persisted.
  2) Auto-injection of characters into all generation requests; per-scene consistency score emitted.
  3) Continuity v2 tracks location, time-of-day, props; surfaces issues in dashboard.
  4) Consistency >90% in Launch readiness test set.
- Dependencies: Embedding model/provider, vector DB, S3, scoring pipeline, UI surfaces.
- Owners/Agents: ML/Backend; BMad *architect, *analyst, *dev, *qa.

## Epic: Cinematic Brains & Format Templates
- Summary: Deliver brain gallery and format templates with beat linkage.
- Description: 3 brains for Alpha; 8 by Beta; gallery with previews; 5 format templates with beat-to-scene linkage; style metadata for marketplace; style mixing behind Pro/Studio flag.
- Acceptance Criteria:
  1) Brain gallery selectable; applies to projects; previews render.
  2) 3 brains live at Alpha; 8 by Beta with style metadata.
  3) 5 templates live; beats generated and editable; beats link to scenes.
  4) Style mixing behind Pro/Studio feature flag.
- Dependencies: Training/curation time, LLM beat gen, preview assets, marketplace schema.
- Owners/Agents: ML/Product; BMad *pm, *analyst, *dev.

## Epic: Export Engine
- Summary: Multi-format export with queueing and safe zones.
- Description: MP4 16:9 in Alpha; add TikTok/Reels/Stories/Cinematic by Beta; safe-zone preview; render queue with status/retries; export success >80% Beta / >90% Launch.
- Acceptance Criteria:
  1) Export succeeds for MP4 16:9 (Alpha) and TikTok/Reels/Stories/Cinematic (Beta).
  2) Safe-zone preview shown per aspect ratio before export.
  3) Render queue exposes status and retry; errors reported.
  4) Export success rate >80% Beta; >90% Launch in test runs.
- Dependencies: Transcoding pipeline, CDN, queue infra, presets, player overlays.
- Owners/Agents: Frontend/Backend; BMad *architect, *dev, *qa.

## Epic: Provider Routing & Fallbacks
- Summary: Resilient routing across model vendors with logging.
- Description: Runway primary; Sora/Kling fallbacks; Stability storyboard fallback; provider_route + safety_mode logged; health checks and cost alerts; fallback rate <20% sustained.
- Acceptance Criteria:
  1) Orchestrator routes to primary Runway; switches to fallbacks on error/throttle.
  2) Storyboard fallback triggered on video throttling; returns usable preview.
  3) provider_route and safety_mode logged on each generation; alerts on fallback >20%.
  4) Cost/health checks active with alerting.
- Dependencies: API contracts/quotas, secrets, orchestrator changes, monitoring hooks.
- Owners/Agents: Backend/ML; BMad *architect, *dev, *qa.

## Epic: Safety & Compliance
- Summary: Enforce content safety and auditability.
- Description: Prompt moderation + NSFW output filter; mature-aesthetic toggle (logged) for horror/thriller; watermarking/origin tracking; DMCA workflow; audit logs for overrides.
- Acceptance Criteria:
  1) Moderation on prompts and outputs; blocks per policy.
  2) Mature-aesthetic toggle stored per project; all changes logged with user/time.
  3) Watermark/origin tracking applied to outputs.
  4) DMCA/report workflow documented and tested.
- Dependencies: Moderation provider, policy definitions, logging/retention, settings UI.
- Owners/Agents: Backend/Policy; BMad *pm, *dev, *qa.

## Epic: Billing, Credits, Promotions
- Summary: Monetization via tiers, credits, and promos.
- Description: Stripe integration; Creator/Pro/Studio SKUs; credit wallet/metering; Founding Creator + Student promos; receipts/refunds; usage alerts at 80%.
- Acceptance Criteria:
  1) Plans purchasable; entitlements enforced.
  2) Credit wallet debits for gen/export; balances visible; alerts at 80%.
  3) Promos (Founding/Student) apply correct pricing/limits.
  4) Receipts/refunds processed; audit log of transactions.
- Dependencies: Billing provider, entitlements service, pricing tables, legal/ToS updates.
- Owners/Agents: Backend/Frontend; BMad *po, *dev, *qa.

## Epic: Marketplace Foundation
- Summary: Marketplace for brains, formats, character packs.
- Description: Browse/purchase assets; upload/review pipeline; purchase via credits; payout tracking; 70/30 rev split initial.
- Acceptance Criteria:
  1) Asset browse/search works; detail pages show metadata.
  2) Purchase flow via credits; entitlement delivered.
  3) Upload/review flow with approval state; moderation hooks.
  4) Payout tracking per creator; 70/30 split recorded.
- Dependencies: Billing/credits, storage, review workflow, moderation, marketplace schema.
- Owners/Agents: Full-stack; BMad *pm, *dev, *qa.

## Epic: Analytics & Observability
- Summary: Instrument core loop and SLOs with alerting.
- Description: Implement taxonomy (including safety_setting_changed, provider_route, cache_hit); dashboards for Activation/Reliability/Revenue/Engagement; alerts (p95 gen >90s, export <80%, provider fallback >20%, payments >3%); tracing with request IDs.
- Acceptance Criteria:
  1) All events emit required properties; safety_mode/provider_route present on generation.
  2) Dashboards live for four pillars (Activation/Reliability/Revenue/Engagement).
  3) Alerts configured and tested for thresholds; incidents route correctly.
  4) Tracing with request IDs across services; logs searchable.
- Dependencies: Analytics SDK/event bus, dbt/models, Grafana/Amplitude/Looker, alerting channels.
- Owners/Agents: Data/Eng; BMad *analyst, *dev, *qa.

## Epic: Infrastructure & Performance
- Summary: Reliable, performant platform with caching and scaling.
- Description: Multi-AZ, caching L1/L2, p95 generation <90s Beta / <75s stretch, autoscaling, CDN for media, SLO dashboards, load tests (1K Beta, 10K Launch prep).
- Acceptance Criteria:
  1) Multi-AZ infra live; autoscaling policies set.
  2) Redis L1 and vector L2 caches active; hit rates reported.
  3) p95 generation <90s in Beta load test; stretch <75s measured.
  4) Load tests to 1K (Beta) and 10K (Launch prep) with reports.
- Dependencies: Terraform/K8s, Redis/vector DB, CDN, load tools, monitoring.
- Owners/Agents: DevOps/Backend; BMad *architect, *dev, *qa.

## Epic: Mobile Web Experience
- Summary: Mobile-friendly preview and light controls.
- Description: Launch scope = preview + approve/lock, request variation, trigger export; responsive validated; handoff to desktop for full edits.
- Acceptance Criteria:
  1) Mobile preview works; lock/variation/export triggers function.
  2) Responsive layouts validated on common breakpoints/devices.
  3) Clear CTA to continue editing on desktop for full controls.
- Dependencies: Responsive design specs, auth/session parity, export APIs.
- Owners/Agents: Frontend; BMad *ux-expert, *dev, *qa.

## Epic: GTM & Launch Ops
- Summary: Coordinate Product Hunt, press, seeding, and support.
- Description: Code freeze T-5; PH listing staged; press briefings T-3; 50 creator seeding; support FAQ and incident comms live; track Day 0 targets (3K signups, 200 paid week 1).
- Acceptance Criteria:
  1) Code freeze observed; go/no-go checklist completed.
  2) PH listing + assets ready; press briefings scheduled with embargo.
  3) Creator seeding executed (50 creators) with credits delivered.
  4) Support runbooks/FAQ live; incident comms channel tested; targets tracked in dashboard.
- Dependencies: Assets (demo, samples, one-pager), calendars, support tooling, tracking pixels, promo codes.
- Owners/Agents: Marketing/CS; BMad *pm or *po, *sm.
