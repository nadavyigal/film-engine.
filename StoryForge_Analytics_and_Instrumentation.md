# StoryForge Analytics & Instrumentation
## Version 1.0 | December 2024 | Confidential

---

# 1. Objectives
- Measure the core loop from sign-up → first lock → export → paid conversion.
- Quantify narrative quality proxies (consistency, iterations) and performance (latency, cache).
- Provide dashboards for Product, Growth, and Engineering with alerting on regression.

---

# 2. Key Metrics
- **North Star:** Completed projects/user/month (target 2.5 @ M6).
- **Activation:** first_locked_scene_within_24h %, first_export_within_48h %, onboarding completion.
- **Engagement:** avg_scenes_per_project, iterations_per_scene, DAU/MAU.
- **Quality:** character_consistency_score, export_success_rate, p95_generation_time.
- **Monetization:** free_to_paid_conversion, ARPPU by tier, credit burn rate, marketplace GMV/take rate.
- **Retention:** week4_retention, churn_reason tags, reactivation rate.

---

# 3. Event Taxonomy (core)
| Event | Required Properties | Notes |
|-------|---------------------|-------|
| user_signed_up | user_id, source, goal (creator/marketer/filmmaker), country | Trigger onboarding flow ID |
| onboarding_completed | user_id, selected_brain?, selected_format? | Capture drop-off if not fired |
| project_created | user_id, project_id, project_type, brain_id?, format_id? | |
| brain_selected | user_id, project_id, brain_id, surface (gallery/recommendation) | |
| format_selected | user_id, project_id, format_id | Include beats_count |
| character_created | user_id, project_id, character_id, creation_mode (upload/generate) | |
| character_locked | user_id, project_id, character_id, consistency_score | |
| safety_setting_changed | user_id, project_id, setting (mature_aesthetic), from_state, to_state, reason? | Log overrides |
| scene_prompt_submitted | user_id, project_id, scene_id, beat_id?, parameters | parameters hash for cache |
| scene_generated | user_id, project_id, scene_id, option_count, duration_s, latency_ms, cache_hit (l1/l2/miss), model_vendor, safety_mode (default/mature), provider_route (primary/fallback/storyboard) | |
| scene_variation_requested | user_id, project_id, scene_id, reason (style/continuity/quality) | |
| scene_locked | user_id, project_id, scene_id, iterations_count, consistency_score | |
| export_started | user_id, project_id, scenes_count, format (tiktok/youtube/reel/stories/cinematic), aspect_ratio | |
| export_succeeded | user_id, project_id, scenes_count, format, duration_s, render_time_ms | paired with export_id |
| export_failed | user_id, project_id, error_code, stage (storyboard/synthesis/export) | |
| payment_succeeded | user_id, plan, amount, currency, credits_purchased | |
| credit_balance_changed | user_id, delta, reason (generation/export/purchase/refund) | |
| marketplace_purchase | user_id, asset_id, asset_type (brain/format/character_pack), price | |
| feedback_submitted | user_id, surface, rating, comment, sentiment | |

Standard properties on all events: `user_id`, `project_id` (when applicable), `client_ts`, `server_ts`, `app_version`, `platform` (web/mobile), `experiment_assignments` (map), `session_id`.

---

# 4. Data Stack & Pipeline
- **Collection:** Frontend via Segment/SDK; backend via event bus (Kafka) with schema validation.
- **Storage:** Snowflake/ClickHouse for analytics; Redis for real-time counters; S3 for raw events.
- **Processing:** dbt for modeling; aggregation jobs for dashboards; anomaly detection on latency/export failure.
- **Visualization:** Amplitude for funnels/retention; Grafana/Datadog for SLOs; Looker/Hex for finance views.
- **Privacy:** PII minimized; IP redaction; data retention policy (12 months raw, 24 months aggregates).

---

# 5. Dashboards (owners)
- **Activation (Growth):** signup→first lock funnel, time-to-first-export, onboarding drop-offs.
- **Engagement (Product):** scenes per project, iterations per scene, brain/format adoption, continuity score distribution.
- **Reliability (Eng):** generation latency p50/p95, cache hit rates, export failure codes, vendor error rates, provider_route mix.
- **Revenue (Ops):** MRR by tier, ARPPU, credit burn, marketplace GMV/take rate, refunds.
- **Cohorts (Product/Growth):** retention by segment (creator/marketer/filmmaker), by brain, by acquisition source.

---

# 6. Experimentation
- **Framework:** A/B with server-side assignment stored with `experiment_assignments`; client respects variant.
- **Guardrails:** Do not run experiments that risk export success <80% or generation p95 >120s.
- **Common Tests:** onboarding copy variants, default brain/format recommendations, pricing page layout, upsell timing at scene 6 vs 8.
- **Evaluation Windows:** activation (48h), engagement (7 days), monetization (14-28 days).

---

# 7. Alerting & Ops
- Generation p95 > 110s (Beta) / >90s (Launch) for 15 minutes → page Eng.
- Export success < 80% over 30 minutes → incident response.
- Payment failures >3% over 1 hour → alert Ops/Support.
- Continuity score rolling average <88% (Beta) → flag ML team.
- Provider route fallback rate >20% over 1 hour → investigate vendor availability/cost.

---

# 8. Implementation Notes
- Use consistent IDs across services (UUIDv4); map external vendor IDs to internal IDs.
- Send both client_ts and server_ts; compute skew for trust.
- Hash prompts when needed to avoid storing user PII; store hash for caching and analytics.
- Respect user opt-out for analytics; route to “anonymous” workspace with no PII.
- Include safety_mode and provider_route in generation/export logs to align with alerting.
