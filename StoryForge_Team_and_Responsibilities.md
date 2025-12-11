# StoryForge Team, Responsibilities, and Timeline
Version: December 2024 | Owners: CPO, CTO

## Team Snapshot (Month 6 steady state)
- Leadership: CEO, CTO, CPO
- Product/Growth: Product Lead, Head of Marketing, Community Manager, Customer Success/Support
- Engineering: ML Lead, ML Engineer #2, Backend Eng x2, Frontend Eng x2, Full Stack Eng, DevOps/SRE, QA
- Design/UX: Product Designer (contract or shared)
- Data: Data/Analytics Lead

## Role Responsibilities & Primary Ownership
- Product Lead (CPO track): Own PRD/roadmap, stage gates, backlog/priority, acceptance criteria, release notes, feedback synthesis.
- CTO/Eng Manager: Architecture/service boundaries, security/SLOs, vendor choices, dependency unblocking, performance budgets, incident process.
- ML Lead: Prompt enhancement + provider routing, caching hooks, embedding/consistency scoring, brain training, continuity v2, latency tuning, safety/mature aesthetic logging.
- ML Engineer #2: Additional brains, storyboard/keyframe flow, semantic cache, quality eval loop, style mixing experiments, provider_route telemetry.
- Backend Engineer #1: Project/scene/character services, export service and queue, auth/JWT, Stripe/credits/usage metering, rate limits/abuse prevention, payout tracking.
- Backend Engineer #2: Format/beat service, onboarding service, analytics event bus, provider health checks, API perf (<200ms p95), mobile token support.
- Frontend Engineer #1: Scene Builder UI (prompt/variations/sliders/lock/version history), character cards, brain gallery, project timeline, export presets/status, error states.
- Frontend Engineer #2: Format gallery + beat editor, continuity dashboard, onboarding wizard, billing/upgrade flows, marketplace browse/purchase, responsive polish, in-app feedback widget, safe-zone preview.
- Full Stack Engineer: Glue format→beat→scene flows, auth flows (Auth0), analytics client SDK, autosave/retry paths, export/generation error recovery.
- DevOps/SRE: AWS/Terraform, EKS, CI/CD (GitHub Actions/ArgoCD), observability (Datadog/Grafana/Sentry), CDN/media, WAF/TLS, quota/cost monitors, load/perf tests, incident runbooks.
- Data/Analytics Lead: Event taxonomy implementation, schema validation, Amplitude/ClickHouse models, dashboards (activation/reliability/revenue/engagement), guardrail alerts, experimentation governance.
- QA Engineer: Test plans and automation (unit/e2e/load), regression gates, beta/launch exit criteria verification, bug triage ownership during launches.
- Head of Marketing: Positioning/messaging, launch assets (PH/press/demo), channel mix and paid tests, lifecycle comms, KPI tracking (CAC, activation, conversion).
- Community Manager: Creator council/Discord, office hours, challenges/showcases, marketplace creator recruiting, feedback routing, credit rewards.
- Customer Success/Support: Concierge onboarding for top creators, FAQ/help center, incident comms, NPS/CSAT, churn reason tagging and save offers.
- Design/UX: Onboarding flows, galleries (brain/format), editor ergonomics, continuity surfacing, safe-zone previews, marketing site visuals, asset kits.

## Tasks, Ownership, and Timeline (M1-M6)
- M1 Foundation
  - Infra: AWS/EKS/CI/CD/monitoring (DevOps, CTO).
  - Core services: Project/scene CRUD, generation orchestrator v1 (Backend #1, ML Lead).
  - Scene Builder MVP UI (FE #1).
  - Architecture/vendor decisions (CTO, ML Lead, Product).
  - Hiring: Senior ML, FE, DevOps (CEO/CTO).
- M2 Alpha (100 creators, end of month)
  - Character locking v1 (>85%): embeddings, injection, scoring (ML Lead).
  - 3 brains live (ML Lead).
  - Export MP4 16:9 + render queue v1 (Backend #1, FE #1).
  - Project CRUD + timeline basics (Backend #1, FE #1).
  - Analytics baseline events (Data Lead, Full Stack).
  - Alpha onboarding + weekly feedback loop (Product, CS).
- M3 Formats & Continuity
  - Format service + beat-to-scene linkage, UI (Backend #2, FE #2, Full Stack).
  - Continuity v2 (location/time/props) + dashboard (ML Lead, FE #2).
  - +5 brains, semantic cache (ML #2).
  - Mobile preview polish (FE #2).
  - Metrics targets: consistency >90%, avg scenes/project ≥6 (Product, Data).
- M4 Performance & Beta (1K users)
  - Performance: p95 generation <90s, cache hit >30% (ML Lead, Backend #1, DevOps).
  - Onboarding v1, auth hardening (FE #2, Full Stack, Backend #2).
  - Billing foundations (no charge), usage tracking (Backend #1/#2).
  - Analytics dashboards + alerting live (Data Lead).
  - Load tests (DevOps, QA).
- M5 Monetization & Marketplace
  - Stripe + credits + usage metering + billing UI (Backend #1, FE #2, Full Stack).
  - Marketplace MVP (brains/templates/character packs, payouts) (Backend #1, FE #2).
  - Marketing/Community hires, channel experiments, launch assets (Marketing, Community, Design).
  - Abuse controls/rate limits (Backend #2, DevOps).
- M6 Public Launch (5K users, $50K MRR)
  - Mobile-responsive polish, safe-zone/export presets final (FE #2, FE #1).
  - Rate limiting/abuse prevention tuned (Backend #2, DevOps).
  - SLA dashboards green; incident runbook staffed (DevOps, CTO).
  - GTM execution: PH/press/influencers, launch video (Marketing, Design).
  - Support readiness: FAQ, scripts, incident comms, NPS loop (CS, Product).

## Near-Term TODOs (next 2 weeks)
- Finalize provider routing and cache strategy sign-off (CTO, ML Lead).
- Lock vector DB choice and provision (CTO, DevOps).
- Complete Scene Builder MVP parity with acceptance criteria (FE #1, Backend #1, ML Lead).
- Stand up baseline analytics events and schema validation (Data Lead, Full Stack).
- Schedule alpha user list + NDA distribution + feedback cadence (Product, CS, Marketing).
- Terraform/EKS production cluster with monitoring + alert thresholds (DevOps).

## Ownership Map by Workstream
- Generation/Continuity: ML Lead (R), ML #2 (S), Backend #1 (C), DevOps (C for perf), Product (A for scope).
- Brains/Styles: ML Lead (A/R), ML #2 (R), Design (C for visuals), Product (C for selection).
- Formats/Beats: Backend #2 (R), FE #2 (R), Full Stack (C), Product (A).
- Scene Builder UI: FE #1 (R), FE #2 (S), ML Lead (C for prompt context), Product (A).
- Export/Render: Backend #1 (R), FE #1 (R for UI), DevOps (C for CDN), Product (A).
- Billing/Credits: Backend #1 (R), FE #2 (R for UI), Full Stack (C), Product (A), Finance/CEO (I).
- Marketplace: Backend #1 (R), FE #2 (R), Product (A), Marketing (C), CS (I).
- Infra/Observability: DevOps (A/R), CTO (C), QA (I for perf).
- Analytics/Experiments: Data Lead (A/R), Full Stack (C), Product (C), Marketing (I).
- GTM/Launch: Head of Marketing (A/R), Product (C), Community (C), CS (C), CEO (I).
- Support/Success: CS (A/R), Product (C), DevOps (I for incidents), Marketing (I).

Legend: A = Accountable, R = Responsible, C = Consulted, I = Informed, S = Support.

