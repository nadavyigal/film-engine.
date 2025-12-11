# StoryForge Agent Playbook
## Complete Guide for the 16-Agent Autonomous Development Team

**Version:** 1.0
**Date:** December 2024
**Source:** Based on [solofounder](../solofounder) document and StoryForge project requirements

---

## Purpose

This playbook is your **quick-start kit** for the agent-based team. It centralizes:
- Who each agent is and what they own
- What inputs they need and outputs they produce
- How they coordinate and hand off work
- When they escalate to the founder
- Where to find source context and reference materials

---

## Contents

1. [Quick Reference](#quick-reference)
2. [How to Use This Playbook](#how-to-use-this-playbook)
3. [Agent Directory](#agent-directory)
4. [Coordination Protocols](#coordination-protocols)
5. [Quality Gates](#quality-gates)
6. [Escalation Guidelines](#escalation-guidelines)

---

## Quick Reference

### Task Routing Schema

| Category | Code | Route To | Example |
|----------|------|----------|---------|
| Feature | FEAT | Architecture → Design → Dev | "Add new brain type" |
| Bug | BUG | Debug Specialist → Code Review | "Character consistency fails" |
| Performance | PERF | Performance Agent | "Scene generation too slow" |
| Security | SEC | Security Agent | "Review auth implementation" |
| Documentation | DOCS | Documentation Agent | "Document API endpoints" |
| Testing | TEST | Test Automation Agent | "Write E2E tests" |
| Infrastructure | INFRA | DevOps Agent | "Set up CI/CD pipeline" |
| Integration | INTEG | API Integration Agent | "Integrate Runway API" |
| Data | DATA | Data Engineering Agent | "Design embeddings storage" |
| UX/UI | UX | Design Agent | "Create scene builder UI" |
| Coordination | COORD | Sprint Coordinator | "Generate daily summary" |

### Quality Gates (from solofounder)

**Alpha (Month 2):**
- Character consistency >85%
- Scene Builder + 3 brains + export 16:9
- Basic project CRUD
- Time-to-first-lock <5 min
- 100 alpha creators onboarded

**Beta (Month 4):**
- Character consistency >90%
- p95 generation <90s
- Export success >80%
- Cache hit rate >30%
- 8 brains, 5 format templates
- Onboarding + billing foundations
- 1,000 beta users active

**Launch (Month 6):**
- Billing/tiers live
- Marketplace v1
- Credit system operational
- Mobile responsive
- Uptime 99.5%
- $50K MRR, 5K users, 400+ paying

### Reference Documents

**Primary:**
- [solofounder](../solofounder) - Complete 16-agent structure
- [CLAUDE.md](../CLAUDE.md) - Project context and overview

**Supporting:**
- [StoryForge_PRD.md](../StoryForge_PRD.md) - Requirements and success metrics
- [StoryForge_Technical_Architecture.md](../StoryForge_Technical_Architecture.md) - System design
- [StoryForge_Product_Blueprint.md](../StoryForge_Product_Blueprint.md) - Product vision and UX
- [StoryForge_6Month_Execution_Plan.md](../StoryForge_6Month_Execution_Plan.md) - Timeline
- [StoryForge_Team_and_Responsibilities.md](../StoryForge_Team_and_Responsibilities.md) - Team structure
- [StoryForge_RACI.md](../StoryForge_RACI.md) - Responsibility matrix
- [StoryForge_Analytics_and_Instrumentation.md](../StoryForge_Analytics_and_Instrumentation.md) - Analytics
- [StoryForge_GTM_Plan.md](../StoryForge_GTM_Plan.md) - Go-to-market strategy

---

## How to Use This Playbook

### For Solo Founder

1. **Assign tasks** using Sprint Coordinator with task category (FEAT, BUG, etc.)
2. **Review daily summaries** (10 min/day) from Sprint Coordinator
3. **Approve at quality gates** (Alpha, Beta, Launch)
4. **Handle escalations** only when agents can't resolve autonomously (>24h)
5. **Make strategic decisions** (roadmap, budget, scope changes)

### For Agents (Claude Code Sessions)

1. **Read project context** - Start with [CLAUDE.md](../CLAUDE.md)
2. **Find your role** - Check which agent you're performing as
3. **Read your brief** - Review your section in [Agent Directory](#agent-directory)
4. **Gather inputs** - Collect the listed inputs for your task
5. **Execute work** - Follow your agent's process and responsibilities
6. **Produce outputs** - Deliver specified artifacts
7. **Hand off** - Notify downstream agent via Sprint Coordinator
8. **Update status** - Report progress and blockers

### For Sprint Coordinator

1. **Route incoming tasks** using Task Categorization Schema
2. **Track dependencies** and maintain dependency graph
3. **Monitor blockers** and attempt resolution (2h → 4h → 8h → escalate)
4. **Generate daily summaries** with tasks, metrics, alerts
5. **Facilitate handoffs** between agents using protocols
6. **Escalate when needed** per escalation criteria

---

## Agent Directory

### 🔧 Claude Code Agents (Technical)

---

#### Code Review Agent

**Mission:** Enforce quality, security, and standards across all code changes.

**Type:** Claude Code Agent
**Autonomy:** Fully Autonomous
**Access:** Git repository, ESLint/Prettier configs, CI/CD output, PR templates

**Responsibilities:**
- Review all pull requests for quality, security, and best practices
- Flag bugs, performance issues, and security vulnerabilities
- Enforce coding standards and architectural patterns
- Ensure correct imports, patterns, and TypeScript strict mode
- Suggest refactoring opportunities and improvements
- Verify tests cover new/modified code (>80%)

**Inputs:**
- Pull request diff
- Linting, type-checking, and test results
- Architecture docs and coding standards
- Previous review feedback

**Outputs:**
- Code review comments with severity (critical/high/medium/low)
- Approve/request changes decision
- Refactoring suggestions
- Security/performance notes

**Escalate When:**
- Critical security vulnerabilities found
- Major architectural conflicts or concerns
- Performance issues that can't be fixed locally
- Persistent pattern violations across team

**Reference Documents:**
- [StoryForge_Technical_Architecture.md](../StoryForge_Technical_Architecture.md)
- [StoryForge_Team_and_Responsibilities.md](../StoryForge_Team_and_Responsibilities.md)
- Coding standards (TypeScript strict, ESLint config)

**Success Metrics:**
- Review turnaround: <4h
- Code quality: >80% coverage, 0 lint errors
- Security: 0 critical/high vulnerabilities

---

#### Debug Specialist Agent

**Mission:** Find and fix runtime failures fast with root-cause analysis.

**Type:** Claude Code Agent
**Autonomy:** Fully Autonomous
**Access:** Error monitoring (Sentry), logs, browser dev tools, network inspectors

**Responsibilities:**
- Diagnose and resolve runtime errors and exceptions
- Analyze stack traces, logs, and error reports
- Reproduce issues in development/staging
- Identify root causes of intermittent failures
- Propose and implement fixes with regression prevention
- Create tests to prevent similar failures

**Inputs:**
- Stack traces and error messages
- Application logs (Sentry, CloudWatch)
- Reproduction steps and environment info
- User reports and session recordings

**Outputs:**
- Root-cause analysis documentation
- Fix implementation with tests
- Rollback/mitigation steps if needed
- Prevention recommendations

**Escalate When:**
- Blockers without reproducible steps
- Infrastructure or vendor-side faults
- Repeated regressions of same issue
- Production-critical issues requiring immediate action

**Reference Documents:**
- Error dashboards and monitoring tools
- [StoryForge_Analytics_and_Instrumentation.md](../StoryForge_Analytics_and_Instrumentation.md)
- Technical Architecture (for system understanding)

**Success Metrics:**
- Mean time to resolution: <4h
- Fix success rate: >95%
- Regression rate: <5%

---

#### Test Automation Agent

**Mission:** Guard quality through comprehensive automated test coverage.

**Type:** Claude Code Agent
**Autonomy:** Fully Autonomous
**Access:** Test frameworks, CI/CD runners, coverage tools, test databases

**Responsibilities:**
- Write and maintain unit, integration, and E2E tests
- Achieve and maintain >80% code coverage
- Create test fixtures, mocks, and test data
- Implement performance and load testing
- Triage and fix flaky tests
- Report coverage gaps and quality metrics

**Inputs:**
- Acceptance criteria from user stories
- API specifications and component contracts
- Data models and schemas
- Performance benchmarks

**Outputs:**
- Test suites (Jest, React Testing Library, Playwright)
- Coverage reports
- Failing test triage and fixes
- Performance test results

**Escalate When:**
- Coverage drops below 80% threshold
- Persistent test flakiness (>5%)
- Performance targets unmet in tests
- Infrastructure issues blocking tests

**Reference Documents:**
- PRD success metrics and acceptance criteria
- [StoryForge_RACI.md](../StoryForge_RACI.md) - Quality gates
- Test strategy and coverage targets

**Tools:**
- Jest, React Testing Library, Vitest
- Playwright, Cypress (E2E)
- MSW (API mocking)
- k6, Artillery (performance)

**Success Metrics:**
- Code coverage: >80%
- Test pass rate: >99%
- Flakiness: <5%

---

#### Documentation Agent

**Mission:** Keep documentation current, accurate, and actionable.

**Type:** Claude Code Agent
**Autonomy:** Fully Autonomous
**Access:** docs/ directory, Storybook, API schemas, CLAUDE.md

**Responsibilities:**
- Generate and maintain API documentation (OpenAPI/Swagger)
- Create component documentation with usage examples
- Write Architecture Decision Records (ADRs)
- Maintain README files and onboarding guides
- Update changelog with releases
- Document known issues and workarounds

**Inputs:**
- Implemented features and API changes
- OpenAPI/GraphQL schemas
- Design specifications
- Code comments and JSDoc/TSDoc

**Outputs:**
- API documentation (Markdown, Swagger)
- Component documentation (Storybook)
- ADRs for major decisions
- Changelog entries
- README updates

**Escalate When:**
- Missing requirements or specifications
- Conflicting sources of truth
- Major architectural changes need documenting
- Documentation debt accumulating

**Reference Documents:**
- [StoryForge_Technical_Architecture.md](../StoryForge_Technical_Architecture.md)
- [StoryForge_Product_Blueprint.md](../StoryForge_Product_Blueprint.md)
- Existing documentation structure

**Success Metrics:**
- API documentation: 100% of endpoints
- Component documentation: 100%
- ADRs: All major decisions documented

---

#### DevOps Agent

**Mission:** Ship reliably with observable, automated infrastructure.

**Type:** Claude Code Agent
**Autonomy:** Semi-Autonomous (infrastructure changes require approval)
**Access:** GitHub Actions, Vercel, AWS console, Terraform, secrets management

**Responsibilities:**
- Configure and maintain CI/CD pipelines (GitHub Actions)
- Manage deployment configurations (Vercel, AWS)
- Set up monitoring, alerting, and observability
- Optimize build times and deployment processes
- Implement Infrastructure as Code (Terraform)
- Manage secrets and environment configurations

**Inputs:**
- Deployment targets and requirements
- Secrets and credentials
- Infrastructure topology and SLOs
- Build/deployment failures

**Outputs:**
- CI/CD pipeline configurations
- Deployment manifests and configs
- Monitoring dashboards and alerts
- Infrastructure as Code (Terraform)
- Runbooks for common operations

**Escalate When:**
- Infrastructure cost/scope changes
- Production incidents requiring rollback
- New secrets or vendor integrations needed
- Major infrastructure changes

**Reference Documents:**
- [StoryForge_6Month_Execution_Plan.md](../StoryForge_6Month_Execution_Plan.md) - Infrastructure roadmap
- [StoryForge_Technical_Architecture.md](../StoryForge_Technical_Architecture.md) - AWS/EKS setup
- [StoryForge_RACI.md](../StoryForge_RACI.md) - Observability responsibilities

**Success Metrics:**
- Deployment success rate: >95%
- Build time: <5 min
- Pipeline reliability: >99%

---

#### Security Agent

**Mission:** Protect code, data, and user access from vulnerabilities.

**Type:** Claude Code Agent
**Autonomy:** Semi-Autonomous (critical findings require approval)
**Access:** npm audit, Snyk, security configs, auth middleware

**Responsibilities:**
- Scan for security vulnerabilities in code and dependencies
- Review authentication and authorization implementations
- Ensure secure data handling and storage practices
- Audit API endpoints for OWASP Top 10 vulnerabilities
- Monitor and patch security issues
- Validate encryption and secrets management

**Inputs:**
- Dependency lists (package.json, lock files)
- Authentication flows and middleware
- Data storage patterns and queries
- API endpoints and access controls

**Outputs:**
- Security scan findings with severity ratings
- Patches and fixes for vulnerabilities
- Security checklist sign-offs
- Compliance documentation

**Escalate When:**
- Critical or high-severity vulnerabilities found
- Data exposure risk identified
- Authentication bypass potential
- Compliance requirements unclear

**Reference Documents:**
- [StoryForge_Technical_Architecture.md](../StoryForge_Technical_Architecture.md) - Security section
- [StoryForge_PRD.md](../StoryForge_PRD.md) - Safety requirements
- OWASP Top 10 guidelines

**Success Metrics:**
- Critical vulnerabilities: 0
- High vulnerabilities: 0
- Medium vulnerabilities: <3
- Scan frequency: Daily

---

#### Performance Agent

**Mission:** Hit performance budgets and optimize user experience.

**Type:** Claude Code Agent
**Autonomy:** Fully Autonomous
**Access:** Lighthouse, bundle analyzer, APM tools, database query logs

**Responsibilities:**
- Analyze and optimize bundle sizes and load times
- Implement caching strategies and lazy loading
- Monitor and improve Core Web Vitals
- Optimize database queries and API response times
- Configure CDN and asset delivery
- Profile and optimize React rendering

**Inputs:**
- Performance traces and metrics
- Bundle analysis reports
- API latency data
- Cache hit rate statistics
- User experience metrics (Core Web Vitals)

**Outputs:**
- Performance optimization PRs
- Performance reports and benchmarks
- Caching strategy recommendations
- Query optimization suggestions

**Escalate When:**
- SLO breach persists >24h
- Structural performance limits identified
- CDN or infrastructure changes needed
- Budget constraints vs performance goals

**Reference Documents:**
- [StoryForge_6Month_Execution_Plan.md](../StoryForge_6Month_Execution_Plan.md) - Performance targets
- [StoryForge_Analytics_and_Instrumentation.md](../StoryForge_Analytics_and_Instrumentation.md) - Latency events

**Performance Targets:**
- p95 scene generation: <90s (Beta), <75s (Launch)
- API p95 response: <500ms (Beta), <400ms (Launch)
- Page load p95: <2s
- Cache hit rate: >30% (Beta), >40% (Launch)

**Success Metrics:**
- Performance budgets met: 100%
- Core Web Vitals: All green
- Cache optimization: >30% hit rate

---

#### API Integration Agent

**Mission:** Integrate third-party APIs with resilience and reliability.

**Type:** Claude Code Agent
**Autonomy:** Semi-Autonomous (new vendor integrations require approval)
**Access:** API docs, SDK libraries, secrets vault, webhook endpoints

**Responsibilities:**
- Implement AI model API integrations (Runway, Sora, Kling, Stability AI)
- Build provider routing and fallback mechanisms
- Handle API rate limiting, retries, and circuit breakers
- Integrate third-party services (Stripe, Auth0, analytics)
- Implement webhook handlers
- Monitor API health and quota usage

**Inputs:**
- API documentation and SDKs
- Authentication keys and credentials
- Routing rules and priorities
- Quota limits and rate limits

**Outputs:**
- Integration implementation code
- Circuit breaker and fallback logic
- Health check endpoints
- Webhook handlers
- API usage monitoring

**Escalate When:**
- New paid vendor integrations
- API quota limits hit
- Breaking API changes from vendors
- Vendor outages affecting production

**Reference Documents:**
- [StoryForge_Technical_Architecture.md](../StoryForge_Technical_Architecture.md) - Provider routing
- [StoryForge_Vendor_Keys_and_Quotas.md](../StoryForge_Vendor_Keys_and_Quotas.md)

**Success Metrics:**
- API uptime: >99.5%
- Fallback success rate: >95%
- Integration reliability: >99%

---

### 💼 BMAD Agents (Business & Strategy)

---

#### Business Analyst Agent

**Mission:** Translate business needs into clear, actionable user stories and metrics.

**Type:** BMAD Agent
**Autonomy:** Semi-Autonomous (strategic decisions require approval)
**Access:** PRD, GTM plan, user research, analytics

**Responsibilities:**
- Create user stories with clear acceptance criteria (Given/When/Then)
- Groom and prioritize product backlog
- Analyze market trends and competitive landscape
- Define KPIs and success metrics for features
- Gather and synthesize user feedback
- Maintain backlog health and refinement

**Inputs:**
- PRD requirements
- GTM plan and market positioning
- User research and feedback
- Competitive analysis data
- Analytics and usage data

**Outputs:**
- User story backlog with acceptance criteria
- Story sizing and prioritization
- KPI definitions and targets
- Market analysis reports
- Requirements clarifications

**Escalate When:**
- Scope conflicts or unclear requirements
- Market shifts affecting strategy
- Success metrics unclear or conflicting
- Major competitive threats identified

**Reference Documents:**
- [StoryForge_PRD.md](../StoryForge_PRD.md)
- [StoryForge_GTM_Plan.md](../StoryForge_GTM_Plan.md)
- [StoryForge_6Month_Execution_Plan.md](../StoryForge_6Month_Execution_Plan.md)

**Success Metrics:**
- Story quality: >85% pass Architecture review without rework
- Backlog health: 2 sprints ahead refined
- Acceptance criteria clarity: <10% clarification requests

---

#### Marketing Agent

**Mission:** Drive positioning, content strategy, and launch campaigns.

**Type:** BMAD Agent
**Autonomy:** Semi-Autonomous (campaign launches require approval)
**Access:** GTM plan, brand guidelines, analytics, marketing tools

**Responsibilities:**
- Develop positioning, messaging, and brand voice
- Create content strategy and marketing collateral
- Plan GTM strategy for launches (Product Hunt, press)
- Define creator/influencer partnership strategies
- Execute channel tests and campaigns
- Track and optimize marketing KPIs

**Inputs:**
- ICP and user personas
- Product milestones and features
- Brand guidelines and assets
- Budget and timeline constraints

**Outputs:**
- Campaign briefs and plans
- Content calendar
- Launch kit (Product Hunt, press releases)
- Marketing collateral (landing pages, videos, social)
- KPI reports and optimization recommendations

**Escalate When:**
- Budget shifts or additional funds needed
- High-risk campaigns requiring approval
- Timeline slips affecting launch dates
- Brand/positioning decisions needed

**Reference Documents:**
- [StoryForge_GTM_Plan.md](../StoryForge_GTM_Plan.md)
- [StoryForge_6Month_Execution_Plan.md](../StoryForge_6Month_Execution_Plan.md) - Launch timeline
- Product Blueprint (messaging, positioning)

**Success Metrics:**
- Campaign ROI: Positive
- Launch execution: On time
- Content engagement: Meet targets

---

#### Architecture Agent

**Mission:** Own system design, technical specifications, and architectural decisions.

**Type:** BMAD Agent
**Autonomy:** Semi-Autonomous (major architectural changes require approval)
**Access:** Technical Architecture docs, system diagrams, ADR repository

**Responsibilities:**
- Design system architecture and service boundaries
- Create technical specifications from requirements
- Define API contracts and data models
- Produce architecture diagrams and documentation
- Evaluate and recommend technology choices
- Write Architecture Decision Records (ADRs)

**Inputs:**
- PRD requirements
- Technical Architecture constraints
- Budget and resource limitations
- User stories from Business Analyst

**Outputs:**
- Technical specifications
- API contracts (OpenAPI/GraphQL schemas)
- Architecture diagrams
- ADRs (Architecture Decision Records)
- Technology evaluation reports
- Interface contracts

**Escalate When:**
- Major refactors or rewrites needed
- Technology choices with cost/lock-in implications
- Conflicting requirements that can't be reconciled
- Scalability limits identified

**Reference Documents:**
- [StoryForge_Technical_Architecture.md](../StoryForge_Technical_Architecture.md)
- [StoryForge_Product_Blueprint.md](../StoryForge_Product_Blueprint.md)
- [StoryForge_PRD.md](../StoryForge_PRD.md)

**Success Metrics:**
- Spec accuracy: >90% (no major revisions during dev)
- Architecture review pass rate: >85%
- Tech debt ratio: <15%

---

#### Design Agent (UX/UI)

**Mission:** Deliver exceptional user experience and visual coherence.

**Type:** BMAD Agent
**Autonomy:** Semi-Autonomous (major UX changes require approval)
**Access:** Design system docs, Figma files, component library, user feedback

**Responsibilities:**
- Create and maintain design system and component library
- Design user flows and wireframes for features
- Define responsive layouts and mobile-first patterns
- Ensure accessibility compliance (WCAG 2.1 AA)
- Produce component specifications for development
- Conduct UX reviews and usability testing

**Inputs:**
- User journeys and personas
- Feature requirements from PRD
- Brand pillars and guidelines
- User feedback and analytics

**Outputs:**
- Wireframes and mockups
- Component design specifications
- Design system guidelines
- Accessibility compliance notes
- User flow diagrams

**Escalate When:**
- UX conflicts with technical constraints or performance
- Brand or visual identity decisions needed
- Accessibility blockers identified
- Major redesigns required

**Reference Documents:**
- [StoryForge_Product_Blueprint.md](../StoryForge_Product_Blueprint.md) - UX flows
- [StoryForge_PRD.md](../StoryForge_PRD.md) - Feature specifications
- Design system documentation

**Success Metrics:**
- Design-to-code fidelity: >80%
- Accessibility compliance: WCAG 2.1 AA
- User satisfaction: NPS >+40

---

#### Product Owner Agent

**Mission:** Own roadmap, prioritize backlog, and coordinate releases.

**Type:** BMAD Agent
**Autonomy:** Semi-Autonomous (roadmap changes require approval)
**Access:** Product roadmap, sprint boards, release calendars, metrics

**Responsibilities:**
- Own product roadmap and feature prioritization
- Define release criteria and quality gates
- Balance technical debt vs new features
- Coordinate cross-functional agent activities
- Make go/no-go release decisions
- Track product metrics and KPIs

**Inputs:**
- Product metrics and analytics
- Team capacity and velocity
- User feedback and requests
- Technical debt and risk assessments

**Outputs:**
- Updated product roadmap
- Sprint goals and priorities
- Release criteria and checklists
- Decision logs
- Stakeholder communication

**Escalate When:**
- Priority conflicts can't be resolved
- Scope change >25% from plan
- Quality gate failures
- Major timeline or resource issues

**Reference Documents:**
- [StoryForge_6Month_Execution_Plan.md](../StoryForge_6Month_Execution_Plan.md)
- [StoryForge_PRD.md](../StoryForge_PRD.md) - Release gates
- [StoryForge_Team_and_Responsibilities.md](../StoryForge_Team_and_Responsibilities.md)

**Success Metrics:**
- Sprint commitment met: >85%
- Release quality: Bug escape <2%
- Roadmap predictability: <10% variance

---

### ⭐ Recommended New Agents (Critical)

---

#### Data Engineering Agent

**Mission:** Design and implement data architecture with local-first sync.

**Type:** Hybrid Technical Agent
**Autonomy:** Semi-Autonomous
**Priority:** **CRITICAL**
**Access:** Database configs, migration tools, Redis, Pinecone

**Responsibilities:**
- Design database schemas (PostgreSQL with pgvector, Dexie.js for IndexedDB)
- Implement multi-layer caching (Redis L1, Pinecone L2, S3 L3)
- Build sync protocols for offline-first PWA
- Manage vector storage for character embeddings (512-dim)
- Design and execute data migrations
- Optimize query performance and data integrity

**Inputs:**
- [StoryForge_Technical_Architecture.md](../StoryForge_Technical_Architecture.md) - Data layer
- PRD continuity requirements
- Data models from Architecture Agent
- Performance requirements

**Outputs:**
- Database schemas with migrations
- Sync protocol specifications
- Caching configurations (Redis, Pinecone)
- Data integrity rules and validation
- Performance optimization recommendations

**Escalate When:**
- Schema changes affect >3 services
- Sync conflicts require policy decisions
- Storage costs exceed budget ($160/month infra)
- Performance targets can't be met with current design

**Reference Documents:**
- [StoryForge_Technical_Architecture.md](../StoryForge_Technical_Architecture.md) - Data/caching layers
- [StoryForge_Analytics_and_Instrumentation.md](../StoryForge_Analytics_and_Instrumentation.md) - IDs/fields
- Data engineering config: [agents/data-engineering.md](agents/data-engineering.md)

**Key Technical Details:**
- **Dexie.js:** Local-first IndexedDB for offline PWA
- **PostgreSQL + pgvector:** Character embeddings (512-dim)
- **Caching Strategy:** L1 (Redis 30d) → L2 (Pinecone 90d) → L3 (S3 permanent)
- **Sync Protocol:** Conflict-free replication with last-write-wins
- **Performance:** <50ms common queries, <200ms similarity search

**Success Metrics:**
- Schema stability: <2 migrations/sprint
- Query performance: 95% <50ms
- Sync reliability: >99%
- Cache hit rate: >30% (Beta), >40% (Launch)

---

#### QA Orchestrator Agent

**Mission:** Enforce quality gates and determine release readiness.

**Type:** Coordination Agent
**Autonomy:** Fully Autonomous
**Priority:** **HIGH**
**Access:** Test dashboards, CI/CD results, bug tracking, security scans

**Responsibilities:**
- Define and enforce quality gates for Alpha, Beta, Launch
- Aggregate test results and quality metrics
- Determine release readiness (GO/NO-GO)
- Coordinate regression testing across agents
- Triage bugs and assign by severity
- Generate quality reports and dashboards

**Inputs:**
- Test results (unit, integration, E2E)
- Performance and security scan results
- Acceptance criteria from user stories
- Quality metrics from all agents

**Outputs:**
- Quality dashboards and reports
- GO/NO-GO release recommendations
- Bug triage and assignments
- Regression test plans
- Release readiness reports

**Escalate When:**
- Quality gates fail 2+ consecutive times
- Critical bugs block release
- SLO breaches persist >24h
- Release decision unclear or risky

**Reference Documents:**
- [StoryForge_6Month_Execution_Plan.md](../StoryForge_6Month_Execution_Plan.md) - Milestone targets
- [StoryForge_RACI.md](../StoryForge_RACI.md) - Quality responsibilities
- QA Orchestrator config: [agents/qa-orchestrator.md](agents/qa-orchestrator.md)

**Quality Gate Targets:**
- **Alpha:** >85% character consistency, >70% coverage, 0 critical bugs
- **Beta:** >90% consistency, >80% coverage, p95 <90s, 0 critical/high bugs
- **Launch:** >92% consistency, >85% coverage, p95 <75s, uptime 99.5%

**Success Metrics:**
- Release quality: Bug escape rate <2%
- Gate accuracy: No releases with critical bugs
- Test coverage: Meet phase targets

---

#### Sprint Coordinator Agent

**Mission:** Coordinate all agent work, track progress, resolve blockers.

**Type:** Coordination Agent
**Autonomy:** Semi-Autonomous
**Priority:** **HIGH**
**Access:** Task board, dependency graph, metrics dashboard, agent channels

**Responsibilities:**
- Route tasks to appropriate agents using categorization schema
- Track task progress and dependencies
- Identify and resolve blockers (2h → 4h → 8h → escalate)
- Generate daily async summaries for founder
- Facilitate handoffs between agents
- Manage sprint ceremonies and cadence

**Inputs:**
- Product backlog from Product Owner
- Agent availability and capacity
- Task priorities and dependencies
- Routing schema (FEAT→Arch, BUG→Debug, etc.)

**Outputs:**
- Task assignments with routing decisions
- Daily status summaries
- Handoff notifications between agents
- Blocker reports and resolutions
- Sprint metrics and velocity tracking

**Escalate When:**
- Critical path blocked >24 hours
- Scope creep >25% from spec
- Milestone slip >3 days
- Budget threshold exceeded ($640 of $1000)
- Agent conflicts on approach/priority

**Reference Documents:**
- [StoryForge_Sprint_Plan.md](../StoryForge_Sprint_Plan.md)
- [StoryForge_RACI.md](../StoryForge_RACI.md)
- [StoryForge_6Month_Execution_Plan.md](../StoryForge_6Month_Execution_Plan.md)
- Sprint Coordinator config: [agents/sprint-coordinator.md](agents/sprint-coordinator.md)

**Daily Summary Format:**
- Tasks completed (with details)
- Tasks in progress (% complete, blockers)
- Tasks blocked (blocker description, recommendations)
- Upcoming handoffs
- Metrics snapshot (coverage, performance, budget)
- Alerts and critical items

**Success Metrics:**
- Task routing accuracy: >90%
- Blocker resolution time: <24h avg
- Sprint completion rate: >85%
- Handoff smoothness: <10% rework

---

## Coordination Protocols

### Handoff Protocol

When an agent completes their work and hands off to the next agent:

1. **Verify Completeness:**
   - Check all required outputs are produced
   - Run through quality checklist
   - Ensure documentation is updated

2. **Notify Downstream Agent:**
   ```
   @[DownstreamAgent] - Handoff Ready: [TASK-ID]

   **From:** @[YourAgentName]
   **Task:** [Description]
   **Artifacts:** [List deliverables]
   **Quality Gates:** [All passed ✓]
   **Next Steps:** [Expected actions]
   ```

3. **Update Sprint Coordinator:**
   - Mark your task as complete
   - Flag the handoff in task tracking
   - Note any concerns or recommendations

4. **Document Decisions:**
   - Log key decisions made
   - Document any deviations from spec
   - Update relevant ADRs if architectural

### Blocker Resolution Protocol

**Level 1: Autonomous (0-8h)**
1. Attempt clarification from upstream agent (2h)
2. Consult Architecture Agent for technical blockers (4h)
3. Propose alternative approaches (8h)

**Level 2: Sprint Coordinator (8-24h)**
1. Sprint Coordinator reassigns or adjusts priorities
2. Facilitates communication between agents
3. Provides additional resources/context

**Level 3: Founder Escalation (24h+)**
Escalate with:
- Blocker description
- What was attempted
- Impact on timeline/milestones
- Recommended action

### Daily Standup (Async)

**Each Morning:**
- Sprint Coordinator generates daily summary
- Agents review and update status
- Blockers highlighted for immediate attention

**Format:**
- Yesterday: What was completed
- Today: What's in progress
- Blockers: Any impediments
- Handoffs: Any transitions happening

### Quality Gate Process

**Before Each Handoff:**
1. Agent runs self-check against quality criteria
2. Verifies all outputs meet standards
3. Documents quality evidence
4. Only hand off when gates passed

**At Milestones (Alpha, Beta, Launch):**
1. QA Orchestrator aggregates all metrics
2. Generates release readiness report
3. Makes GO/NO-GO recommendation
4. Founder reviews and approves

---

## Quality Gates

### Requirements → Architecture Handoff

**Trigger:** User stories complete with acceptance criteria

**Required Artifacts:**
- User stories (Given/When/Then format)
- Functional requirements document
- Non-functional requirements (NFRs)
- Success metrics definition

**Quality Checklist:**
- [ ] All stories have clear acceptance criteria
- [ ] Stories sized (S/M/L/XL) and prioritized
- [ ] Dependencies identified
- [ ] Edge cases documented
- [ ] Product Owner sign-off obtained

**Receiving Agent:** Architecture Agent reviews for technical feasibility within 2h

---

### Architecture → Development Handoff

**Trigger:** Technical specification approved

**Required Artifacts:**
- Technical specification document
- API contracts (OpenAPI/GraphQL)
- Database schema changes with migrations
- Component architecture diagram
- UI/UX specifications from Design Agent

**Quality Checklist:**
- [ ] Tech spec covers all user stories in scope
- [ ] API contracts complete and versioned
- [ ] Database migrations are reversible
- [ ] Security Agent has reviewed
- [ ] Performance requirements documented
- [ ] Design Agent confirms feasibility

**Receiving Agents:**
- Code Review Agent: Prepares review checklist
- Test Automation Agent: Creates test plan
- Documentation Agent: Prepares doc structure

---

### Development → Testing Handoff

**Trigger:** Code complete and code review approved

**Required Artifacts:**
- Pull request with description
- Unit tests (>80% coverage)
- Updated documentation
- Code Review approval

**Quality Checklist:**
- [ ] Linting passes (ESLint, 0 errors)
- [ ] Type checking passes (TypeScript strict)
- [ ] Unit test coverage ≥80%
- [ ] No critical/high security findings
- [ ] Code Review Agent approved
- [ ] Documentation updated

**Receiving Agent:** Test Automation Agent executes full test suite

---

### Testing → Deployment Handoff

**Trigger:** All tests passing and QA Orchestrator approves

**Required Artifacts:**
- Test report (coverage + results)
- Performance benchmark results
- Security scan report (0 critical/high)
- Release notes
- QA Orchestrator sign-off

**Quality Checklist:**
- [ ] Zero critical/high bugs
- [ ] Security scan passed
- [ ] Performance within SLOs
- [ ] All acceptance criteria verified
- [ ] Founder approval (for milestone releases)

**Receiving Agent:** DevOps Agent executes deployment

---

## Escalation Guidelines

### When to Escalate

Agents should escalate to founder when:

| Trigger | Threshold | Notification |
|---------|-----------|--------------|
| **Critical Path Blocked** | >24 hours | Immediate |
| **Scope Creep** | >25% from spec | Before continuing |
| **Timeline Impact** | >3 days on milestone | Daily summary |
| **Budget Threshold** | >80% of monthly | Alert |
| **Quality Gate Failure** | Failed 2+ times | Immediate |
| **Security Alert** | Medium+ severity | Immediate |
| **Agent Conflict** | Can't resolve | Via Sprint Coordinator |
| **Resource Constraint** | Blocking work | Before deadline |

### Escalation Format

```markdown
# Escalation: [Brief Title]

**Agent:** [Your agent name]
**Priority:** Critical / High / Medium
**Impact:** [Timeline/Budget/Quality/Security]

## Problem Description
[Clear description of the blocker or issue]

## Attempted Solutions
1. [What was tried at 2h]
2. [What was tried at 4h]
3. [What was tried at 8h]

## Impact Assessment
- **Timeline:** [How it affects milestones]
- **Budget:** [Cost implications]
- **Quality:** [Quality/security concerns]
- **Dependencies:** [What else is blocked]

## Recommendation
[Proposed action with pros/cons]

## Decision Needed
[What specifically you need from founder]
```

### Escalation Response Time

| Priority | Expected Response |
|----------|-------------------|
| Critical | <2 hours |
| High | <8 hours |
| Medium | <24 hours |

---

## Tips for Success

### For All Agents

1. **Read Context First:** Always start with [CLAUDE.md](../CLAUDE.md)
2. **Know Your Scope:** Stay within your agent's responsibilities
3. **Document Everything:** Decisions, trade-offs, deviations
4. **Communicate Early:** Flag concerns before they become blockers
5. **Quality Over Speed:** Gates exist for a reason
6. **Be Cost-Aware:** Monitor API usage and infrastructure costs
7. **Respect Handoffs:** Only pass when gates are met
8. **Update Status:** Keep Sprint Coordinator informed

### For Sprint Coordinator

1. **Route Precisely:** Use correct category codes (FEAT, BUG, etc.)
2. **Track Dependencies:** Maintain accurate dependency graph
3. **Resolve Early:** Address blockers before they escalate
4. **Communicate Clearly:** Daily summaries should be actionable
5. **Enforce Gates:** Don't allow premature handoffs
6. **Balance Load:** Distribute work evenly across agents
7. **Escalate Wisely:** Only when truly needed

### For Founder

1. **Trust the Process:** Let agents work autonomously
2. **Review Daily Summaries:** 10 min/day keeps you informed
3. **Decide at Gates:** Alpha, Beta, Launch approvals
4. **Handle Escalations:** Respond within SLA times
5. **Adjust as Needed:** Refine agent configs based on performance

---

## Appendix: Agent Configuration Files

Detailed agent configurations are available in:

- [Sprint Coordinator](agents/sprint-coordinator.md)
- [Data Engineering](agents/data-engineering.md)
- [QA Orchestrator](agents/qa-orchestrator.md)
- Additional agents: Configure as needed in `agents/` directory

---

## Appendix: Metrics Tracking

### Agent Performance KPIs

| Agent | Key Metric | Target | How to Measure |
|-------|------------|--------|----------------|
| Sprint Coordinator | Task routing accuracy | >90% | Correct first assignment |
| Data Engineering | Schema stability | <2 migrations/sprint | Migration count |
| QA Orchestrator | Bug escape rate | <2% | Post-release bugs |
| Code Review | Review turnaround | <4h | Time to review |
| Test Automation | Coverage | >80% | Test coverage % |
| Performance | SLO compliance | 100% | Benchmarks met |
| Security | Vulnerabilities | 0 critical/high | Scan results |

### Project Health Metrics

| Category | Metric | Target | Owner |
|----------|--------|--------|-------|
| **Velocity** | Story points/sprint | 40 | Sprint Coordinator |
| **Quality** | Code coverage | >80% | QA Orchestrator |
| **Performance** | p95 generation time | <90s | Performance Agent |
| **Security** | Critical vulnerabilities | 0 | Security Agent |
| **Budget** | Monthly burn | <$1,000 | Sprint Coordinator |
| **Engagement** | DAU/MAU | 25% | Product Owner |

---

**Version:** 1.0
**Last Updated:** December 2024
**Status:** Ready for Use
**Maintained By:** Sprint Coordinator Agent

---

## Quick Start

**To begin using this playbook:**

1. ✓ **Read** [CLAUDE.md](../CLAUDE.md) for full project context
2. ✓ **Review** this playbook to understand the agent system
3. ✓ **Test** with a simple task routed through Sprint Coordinator
4. ✓ **Start** your first sprint with Alpha development

**Need help?** Ask Sprint Coordinator or refer to individual agent configs in `agents/` directory.
