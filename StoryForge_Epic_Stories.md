# StoryForge Epic → Stories/Tasks
## Estimates are t-shirt sizes (S/M/L) and note key dependencies.

---

## Epic: Scene Builder & Timeline
- Story: Prompt enhancement pipeline integration (brain + beat + continuity). **Size:** M. **Deps:** Continuity/Brain/Format APIs, prompt service.
- Story: Generate 2–3 options + “generate more” action. **Size:** M. **Deps:** Generation orchestrator.
- Story: Lock/unlock scenes with version history. **Size:** M. **Deps:** Scenes backend API, storage for versions.
- Story: Timeline reorder UI + persistence. **Size:** S. **Deps:** Project service ordering endpoint.
- Story: Storyboard/keyframe preview behind Beta flag. **Size:** M. **Deps:** Storyboard generator, feature flag service.
- Task: UI perf budget instrumentation (p95 latency <200ms). **Size:** S. **Deps:** Frontend telemetry.
- Task: QA test plan for editor core flows. **Size:** S. **Deps:** QA.

## Epic: Continuity & Character Lock
- Story: Character create (upload/generate) with embeddings stored. **Size:** M. **Deps:** Embedding model, vector DB, S3.
- Story: Auto-inject characters into generation prompts. **Size:** M. **Deps:** Orchestrator hook.
- Story: Consistency scoring per scene + reporting to UI. **Size:** M. **Deps:** Scoring pipeline, UI surface.
- Story: Continuity v2 (location/time/props) tracking. **Size:** L. **Deps:** Detection models, state store.
- Story: Continuity dashboard surfacing issues. **Size:** M. **Deps:** UI, continuity API.
- Task: Target test set >90% consistency validation. **Size:** S. **Deps:** QA/ML eval.

## Epic: Cinematic Brains & Format Templates
- Story: Brain gallery UI with previews and selection. **Size:** M. **Deps:** Brain metadata service, assets.
- Story: Ship 3 brains for Alpha; extend to 8 by Beta (model delivery). **Size:** L. **Deps:** Training/curation.
- Story: Format templates (5) with beat generation/editing. **Size:** M. **Deps:** LLM beat generator, format service.
- Story: Beat-to-scene linkage in project timeline. **Size:** M. **Deps:** Project/timeline API.
- Story: Style mixing behind Pro/Studio flag. **Size:** M. **Deps:** Feature flag, mixing pipeline.

## Epic: Export Engine
- Story: MP4 16:9 export (Alpha). **Size:** M. **Deps:** Transcoding pipeline, storage/CDN.
- Story: Add TikTok/Reels/Stories/Cinematic presets (Beta). **Size:** M. **Deps:** Preset configs, transcoder.
- Story: Safe-zone preview overlay per aspect. **Size:** S. **Deps:** Frontend player overlay.
- Story: Render queue status + retries. **Size:** M. **Deps:** Queue infra, jobs API.
- Task: Export success SLO monitoring (>80% Beta, >90% Launch). **Size:** S. **Deps:** Observability.

## Epic: Provider Routing & Fallbacks
- Story: Primary Runway routing with health checks. **Size:** M. **Deps:** Runway API, orchestrator.
- Story: Sora/Kling fallback paths with circuit breaker. **Size:** M. **Deps:** Vendor APIs, feature flags.
- Story: Storyboard fallback via Stability image-to-video. **Size:** M. **Deps:** Stability API.
- Task: Log provider_route + safety_mode; alert on fallback >20%. **Size:** S. **Deps:** Telemetry/alerts.
- Task: Cost/health dashboards. **Size:** S. **Deps:** Monitoring stack.

## Epic: Safety & Compliance
- Story: Prompt moderation + NSFW output filter. **Size:** M. **Deps:** Moderation provider, policy.
- Story: Mature-aesthetic toggle stored/logged per project. **Size:** S. **Deps:** Settings UI/API, logging.
- Story: Watermark/origin tracking on outputs. **Size:** M. **Deps:** Transcoder/post-process.
- Story: DMCA/report workflow implementation. **Size:** M. **Deps:** Support tooling/process.
- Task: Audit log for safety overrides. **Size:** S. **Deps:** Logging store.

## Epic: Billing, Credits, Promotions
- Story: Stripe integration for Creator/Pro/Studio plans. **Size:** M. **Deps:** Stripe, entitlements.
- Story: Credit wallet + metering gen/export + 80% usage alerts. **Size:** M. **Deps:** Billing service, notifier.
- Story: Promotions (Founding Creator, Student) application. **Size:** S. **Deps:** Promo rules in billing.
- Story: Receipts/refunds + audit log. **Size:** S. **Deps:** Billing provider.

## Epic: Marketplace Foundation
- Story: Browse/search + asset detail pages. **Size:** M. **Deps:** Marketplace API, assets.
- Story: Purchase via credits; entitlement delivery. **Size:** M. **Deps:** Billing/credits, entitlements.
- Story: Upload/review flow with moderation. **Size:** M. **Deps:** Storage, review workflow, moderation hooks.
- Story: Payout tracking with 70/30 split. **Size:** M. **Deps:** Payout subsystem/ledger.

## Epic: Analytics & Observability
- Story: Implement event taxonomy (incl. safety_setting_changed, provider_route, cache_hit). **Size:** M. **Deps:** Analytics SDK/event bus.
- Story: Dashboards for Activation/Reliability/Revenue/Engagement. **Size:** M. **Deps:** Amplitude/Grafana/Looker.
- Story: Alerts (p95 gen >90s; export <80%; provider fallback >20%; payments >3%). **Size:** S. **Deps:** Alerting stack.
- Story: Tracing with request IDs across services. **Size:** M. **Deps:** Tracing middleware.

## Epic: Infrastructure & Performance
- Story: Multi-AZ + autoscaling setup. **Size:** M. **Deps:** Terraform/K8s.
- Story: Redis L1 + vector L2 caching with reported hit rates. **Size:** M. **Deps:** Redis/vector DB.
- Story: Performance tuning to p95 gen <90s Beta / <75s stretch. **Size:** L. **Deps:** Profiling, caching, model routing.
- Story: Load tests to 1K (Beta) and 10K (Launch prep) with reports. **Size:** M. **Deps:** Load tools, staging env.

## Epic: Mobile Web Experience
- Story: Mobile preview + lock/variation/export triggers. **Size:** M. **Deps:** Frontend, API parity.
- Story: Responsive validation on target devices. **Size:** S. **Deps:** Device matrix, QA.
- Story: Desktop CTA for full editing. **Size:** S. **Deps:** UI update.

## Epic: GTM & Launch Ops
- Story: Code freeze + go/no-go checklist at T-5. **Size:** S. **Deps:** Release calendar.
- Story: PH listing staged + press briefings T-3 with assets. **Size:** M. **Deps:** Assets, PR schedule.
- Story: Creator seeding (50) with credits delivered. **Size:** M. **Deps:** Billing credits, roster.
- Story: Support FAQ + incident comms live; Day 0 targets dashboard. **Size:** M. **Deps:** Support tooling, analytics.
