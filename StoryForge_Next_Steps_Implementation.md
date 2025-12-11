# StoryForge Next Steps (Execution Checklist)
## December 2024 | Internal

---

# 1) Engineering Implementation
- Mature aesthetic toggle (Launch): add project-level setting; backend enforces and logs overrides; UI flag on settings panel; default OFF.
- Provider routing: wire primary Runway with Sora/Kling fallbacks; storyboard fallback via Stability image-to-video when throttled; include provider_route + safety_mode in logs.
- Scene Builder: ensure version history + “generate more” options ship in Alpha; storyboard/keyframe preview behind Beta flag.
- Continuity: expose consistency score per scene; continuity dashboard by Beta (surfacing location/time/props issues).
- Export: presets live (Alpha MP4 16:9; Beta adds TikTok 9:16, Reels 9:16, Stories 9:16, Cinematic 2.39:1); safe-zone preview and render queue status.
- Billing/tiers (Launch): Creator/Pro/Studio SKUs, credit wallet, usage metering; Founding Creator + Student promo flags.

# 2) Analytics Integration
- Implement events per `StoryForge_Analytics_and_Instrumentation.md` including:
  - `safety_setting_changed` (mature_aesthetic toggles).
  - `scene_generated` with `safety_mode`, `provider_route`, `cache_hit`, `model_vendor`.
  - Export events with render_time_ms, format, aspect_ratio.
- Standard props on every event: user_id, project_id, client_ts, server_ts, app_version, platform, experiment_assignments, session_id.
- Dashboards to stand up: Activation funnel (signup→first lock→export), Reliability (p50/p95 latency, cache hit, provider route mix), Revenue (MRR by tier, credit burn), Engagement (iterations per scene, continuity score distribution).
- Alerting: p95 generation >90s (Launch), export success <80%, payment failures >3%, provider fallback rate >20%.

# 3) GTM & Launch Ops
- Code freeze T-5 days before PH/press; dry run of export/generation SLAs at freeze.
- Product Hunt: target Week 1 signups 3,000; paying conversions 200; listing staged with assets (demo video, sample projects, press one-pager).
- Press: briefings scheduled T-3 with embargo; press kit in shared folder.
- Influencer seeding: 50 creators with sponsored credits; Day 0 content lined up.
- Support: FAQ + incident comms template live; Zendesk/Intercom routing validated.

# 4) Vendor & Quotas
- Confirm Runway quotas for launch week; obtain Sora/Kling fallback limits; Stability storyboard capacity.
- Add health checks + failover policies in orchestrator; cost monitoring alerts for GPU/API spikes.

# 5) Owners (suggested)
- Eng: Provider routing + safety toggle (Backend/ML lead), Scene Builder/Export (Frontend/Full-stack).
- Data: Analytics implementation + dashboards (Data/Analytics lead).
- Ops: Vendor contracts/quotas, alerting SLOs (Ops/DevOps).
- GTM: PH/press, influencer program, support readiness (Marketing/CS).
