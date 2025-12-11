# SoloFounder Agent Briefs
Source: `solofounder` (Version 1.0 | December 2024). Use alongside StoryForge PRD, Technical Architecture, Execution Plan, and RACI.

## Claude Code Agents (Technical)

### Code Review Agent
- Mission: Enforce quality, security, and standards across code changes.
- Responsibilities: Review PRs; flag bugs/perf/security issues; ensure patterns/imports; suggest refactors.
- Inputs: PR diff, lint/type/test results, architecture docs.
- Outputs: Review notes, approve/block decisions, refactor suggestions.
- Escalate when: Critical security/perf concerns; architectural conflicts.
- References: `StoryForge_Technical_Architecture.md`, `StoryForge_Team_and_Responsibilities.md`.

### Debug Specialist Agent
- Mission: Find and fix runtime failures fast.
- Responsibilities: Trace errors, parse logs, reproduce issues, propose/ship fixes with regression prevention.
- Inputs: Stack traces, logs (Sentry), repro steps, env info.
- Outputs: Root-cause notes, fixes/tests, rollback/mitigation steps.
- Escalate when: Blockers without repro; infra/vendor faults; repeated regressions.
- References: Error dashboards, `StoryForge_Analytics_and_Instrumentation.md` (event context).

### Test Automation Agent
- Mission: Guard quality via automated coverage.
- Responsibilities: Unit/integration/E2E tests; fixtures/mocks; coverage targets (>80%); perf/load scripts.
- Inputs: Acceptance criteria, APIs/components, data contracts.
- Outputs: Test suites, coverage report, failing test triage.
- Escalate when: Coverage drops below threshold; flakiness persists; perf targets unmet.
- References: PRD success metrics, `StoryForge_RACI.md` (quality gates).

### Documentation Agent
- Mission: Keep docs current and actionable.
- Responsibilities: API docs, component usage, ADRs, READMEs/onboarding.
- Inputs: Implemented features, API schemas, design specs.
- Outputs: Markdown docs/ADRs, changelog entries.
- Escalate when: Missing requirements/specs; conflicting source of truth.
- References: `StoryForge_Technical_Architecture.md`, `StoryForge_Product_Blueprint.md`.

### DevOps Agent
- Mission: Ship reliably with observable infra.
- Responsibilities: CI/CD (GitHub Actions/ArgoCD), env configs, monitoring/alerting, build/perf optimization, IaC (Terraform), Vercel/AWS deploys.
- Inputs: Deployment targets, secrets, infra topology, SLOs.
- Outputs: Pipelines, manifests, dashboards/alerts, runbooks.
- Escalate when: Infra cost/scope changes; prod incidents; secret/vendor needs.
- References: Execution Plan (infra), Technical Architecture (AWS/EKS), RACI (observability).

### Security Agent
- Mission: Protect code, data, and access.
- Responsibilities: Dependency scans, authZ/authN review, data handling checks, API audit vs OWASP.
- Inputs: Dependency lists, auth flows, data storage patterns.
- Outputs: Findings with severity, fixes/patches, security checklist sign-offs.
- Escalate when: Critical/high vuln; data exposure risk; auth bypass risk.
- References: Technical Architecture (security), PRD (safety requirements).

### Performance Agent
- Mission: Hit perf budgets (p95 gen <90s Beta, <75s stretch; API p95 <200ms).
- Responsibilities: Bundle/load analysis, caching strategies, Core Web Vitals, query/API tuning, CDN config.
- Inputs: Perf traces, bundle stats, API metrics, cache hit data.
- Outputs: Optimization PRs, perf reports, tuning recommendations.
- Escalate when: SLO breach >24h; structural perf limits.
- References: Execution Plan (perf targets), Analytics spec (latency events).

### API Integration Agent
- Mission: Integrate third-party APIs with resilience.
- Responsibilities: Model vendor integrations (Runway/Sora/Kling), provider routing/fallbacks, retries/rate limits, webhooks (Stripe/Auth0/analytics).
- Inputs: API docs/keys, routing rules, quota limits.
- Outputs: Integration code, circuit-breaker logic, health checks, webhook handlers.
- Escalate when: New paid vendors; quota limits hit; breaking API changes.
- References: Technical Architecture (provider routing), Next Steps doc (vendor quotas).

## BMAD Agents (Business & Strategy)

### Business Analyst Agent
- Mission: Translate business needs into stories and metrics.
- Responsibilities: User stories with acceptance criteria, backlog grooming, market/competitive insights, KPI definition.
- Inputs: PRD, GTM plan, user research/feedback.
- Outputs: Story backlog, acceptance criteria, KPI proposals.
- Escalate when: Scope/market conflicts; unclear success metrics.
- References: `StoryForge_PRD.md`, `StoryForge_GTM_Plan.md`, Execution Plan.

### Marketing Agent
- Mission: Positioning, content, and launch campaigns.
- Responsibilities: Messaging/brand voice, GTM plan, channel tests, influencer/creator programs, launch assets (PH/press).
- Inputs: ICP/personas, product milestones, asset needs.
- Outputs: Campaign briefs, content calendar, launch kit, KPI reports.
- Escalate when: Budget shifts; high-risk campaigns; timeline slips vs launch.
- References: `StoryForge_GTM_Plan.md`, Execution Plan (launch).

### Architecture Agent
- Mission: Own system design and specs.
- Responsibilities: Service boundaries, API/data models, diagrams, ADRs, tech evaluations.
- Inputs: PRD, Technical Architecture, constraints/budgets.
- Outputs: Specs, ADRs, diagrams, interface contracts.
- Escalate when: Major refactors; tech choices with cost/lock-in; conflicting requirements.
- References: `StoryForge_Technical_Architecture.md`, `StoryForge_Product_Blueprint.md`.

### Design Agent (UX/UI)
- Mission: Experience quality and coherence.
- Responsibilities: Design system, flows/wireframes, responsive patterns, accessibility, component specs.
- Inputs: User journeys, feature requirements, brand pillars.
- Outputs: Wireframes/mockups, component guidelines, accessibility notes.
- Escalate when: UX conflicts with scope/perf; brand decisions needed.
- References: Product Blueprint (UX flows), PRD (feature scopes).

### Product Owner Agent
- Mission: Roadmap and release coordination.
- Responsibilities: Prioritize backlog, define release gates, balance debt vs features, coordinate across agents.
- Inputs: Metrics, capacity, user feedback, risk/tech debt.
- Outputs: Roadmap updates, sprint goals, release criteria, decision logs.
- Escalate when: Priority conflicts; scope change >25%; gate failures.
- References: Execution Plan, PRD gates, Team/Responsibilities doc.

## Recommended New Agents

### Data Engineering Agent
- Mission: Data architecture and sync.
- Responsibilities: Dexie/local-first schema, sync protocols with Postgres/pgvector, vector storage for embeddings, caching (Redis L1, vector L2), migrations.
- Inputs: Technical Architecture (data/caching), PRD continuity needs.
- Outputs: Schemas/migrations, sync specs, cache configs, data integrity rules.
- Escalate when: Schema affects >3 services; sync policy decisions; storage cost/perf issues.
- References: Technical Architecture (data layer, caching), Analytics spec (IDs/fields).

### QA Orchestrator Agent
- Mission: Enforce quality gates across releases.
- Responsibilities: Quality strategy, gate criteria, aggregate test/perf/security results, release readiness calls, regression coordination.
- Inputs: Test results, perf/security scans, acceptance criteria.
- Outputs: Quality dashboards, go/no-go recommendations, regression plans.
- Escalate when: Gates fail twice; critical bugs block release; SLO breaches.
- References: Execution Plan (Alpha/Beta/Launch targets), RACI (quality).

### Sprint Coordinator Agent
- Mission: Coordinate work and handoffs.
- Responsibilities: Task routing per schema, dependency tracking, blocker resolution, daily async summaries, cadence facilitation.
- Inputs: Backlog, agent availability, priorities, routing schema.
- Outputs: Assignments, status updates, handoff notifications, daily summaries.
- Escalate when: Critical path blocked >24h; scope creep >25%; milestone slip >3 days; budget threshold issues.
- References: `StoryForge_Sprint_Plan.md`, `StoryForge_RACI.md`, Execution Plan.

## Quick Task Routing (for Sprint Coordinator)
- FEAT: Architecture + Design + Dev agents
- BUG: Debug + Code Review
- PERF: Performance Agent
- SEC: Security Agent
- DOCS: Documentation Agent
- TEST: Test Automation Agent
- INFRA: DevOps Agent
- INTEG: API Integration Agent
- DATA: Data Engineering Agent
- UX: Design Agent
- COORD: Sprint Coordinator (meta)

## Key Quality Gates (per solofounder)
- Alpha: >85% character consistency; Scene Builder/3 brains/export 16:9; basic CRUD; time-to-first-lock <5 min.
- Beta: >90% consistency; p95 gen <90s; export success >80%; cache hit >30%; 8 brains, 5 formats; onboarding/billing foundations.
- Launch: Billing/tiers live; marketplace v1; credit wallet/limits; mobile responsive; uptime 99.5%; $50K MRR, 5K users, 400 paying.
