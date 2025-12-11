# CLAUDE.md - StoryForge Project Context

This file provides guidance to Claude Code and all AI agents working on the StoryForge project.

## Project Overview

**StoryForge** is a generative film-creation platform that enables anyone to create complete cinematic series and movies using AI. We're building a cloud-native, microservices-based platform that orchestrates multiple AI models, manages complex state across multi-scene projects, and provides real-time collaborative editing capabilities.

**Mission:** "Everyone has a story. Now everyone can show it."

**Product Thesis:** Suno democratized music creation through structured workflows, format constraints, and iterative refinement. We apply the same methodology to filmmaking.

---

## Architecture & Tech Stack

### Frontend
- **Next.js 14** with TypeScript
- **React** for UI components
- **Tailwind CSS** for styling
- **Radix UI** for accessible components
- **PWA-ready** with offline-first capabilities

### Backend Services (Microservices)
- **Project Service** - Project lifecycle and scene management
- **Scene Service** - Scene generation and iteration
- **Continuity Engine** - Character and environment consistency
- **Brain Service** - Cinematic style management
- **Format Service** - Narrative structure templates
- **Generation Orchestrator** - Multi-model AI coordination
- **Export Service** - Multi-format rendering
- **User Service** - Authentication and profiles
- **Billing Service** - Subscriptions and credits
- **Marketplace Service** - Community content

### Data Layer
- **PostgreSQL** (Primary database with pgvector extension)
- **Redis** (L1 cache)
- **Pinecone** (Vector database for character embeddings)
- **S3 + CloudFront** (Media storage and CDN)
- **Kafka** (Event streaming)
- **ClickHouse** (Analytics)

### AI/ML Layer
- **Runway API** (Primary video generation)
- **Sora API** (Video generation fallback)
- **Kling API** (Video generation fallback)
- **Stability AI** (Image generation)
- **Claude API** (Prompt enhancement and story generation)
- **ElevenLabs** (Voice synthesis)

### Infrastructure
- **AWS** (Cloud provider)
- **EKS** (Kubernetes for services)
- **API Gateway** (Kong/AWS API Gateway)
- **GraphQL** (Apollo Federation)

---

## Core Concepts

### Cinematic Brains
Pre-trained style models that encode visual language, pacing, and narrative conventions of specific genres/directors. Examples: Thriller, K-Drama, Pixar, TikTok Native.

### Format Templates
Narrative structure blueprints providing story scaffolding (6-Episode Mini-Series, 3-Act Short Film, TikTok Series, etc.).

### Character Locking
System maintaining character visual consistency across scenes using face embeddings (512-dim vectors) and appearance descriptors.

### Continuity Engine
Maintains consistency across:
- **Character Identity** - Face embeddings, clothing, voice
- **Environment** - Locations, lighting, props
- **Temporal Coherence** - Time-of-day, weather, season

---

## Development Workflow

### Agent-Based Team Structure
StoryForge uses a **16-agent team structure** for autonomous development.

**Complete guide:** [solofounder-team/AGENT_PLAYBOOK.md](solofounder-team/AGENT_PLAYBOOK.md)

#### Claude Code Agents (8)
1. **Code Review Agent** - Code quality, security, best practices
2. **Debug Specialist** - Error diagnosis and resolution
3. **Test Automation** - Unit, integration, E2E testing
4. **Documentation** - API docs, ADRs, guides
5. **DevOps** - CI/CD, deployment, monitoring
6. **Security** - Vulnerability scanning, auth review
7. **Performance** - Optimization, bundle analysis
8. **API Integration** - Third-party integrations

#### BMAD Agents (5)
1. **Business Analyst** - Requirements, user stories
2. **Marketing** - GTM strategy, content
3. **Architecture** - System design, tech specs
4. **Design (UX/UI)** - Design system, wireframes
5. **Product Owner** - Roadmap, prioritization

#### New Critical Agents (3)
1. **Sprint Coordinator** - Task routing, progress tracking
2. **Data Engineering** - Database schema, sync protocols
3. **QA Orchestrator** - Quality gates, release readiness

### Task Categorization Schema
- **FEAT** - New features → Architecture → Design → Dev
- **BUG** - Bug fixes → Debug Specialist → Code Review
- **PERF** - Performance → Performance Agent
- **SEC** - Security → Security Agent
- **DOCS** - Documentation → Documentation Agent
- **TEST** - Testing → Test Automation
- **INFRA** - Infrastructure → DevOps
- **INTEG** - Integrations → API Integration
- **DATA** - Database → Data Engineering
- **UX** - UI/UX → Design Agent

---

## Project Structure

```
StoryForge/
├── docs/                          # Documentation
│   ├── StoryForge_Technical_Architecture.md
│   ├── StoryForge_Product_Blueprint.md
│   ├── StoryForge_PRD.md
│   ├── StoryForge_6Month_Execution_Plan.md
│   └── StoryForge_Epic_Stories.md
├── solofounder                    # Agent team structure doc
├── solofounder-team/             # Agent configurations
│   ├── README.md
│   ├── agents/                   # Individual agent configs
│   └── workflows/                # Handoff protocols
├── services/                     # Microservices (future)
│   ├── project-service/
│   ├── scene-service/
│   ├── continuity-engine/
│   └── ...
├── web/                          # Next.js frontend (future)
├── infra/                        # Infrastructure as code
└── BMAD-METHOD/                  # BMAD framework reference
```

---

## Key Requirements & Constraints

### Performance Targets
- **p95 Generation Time:** <90s (Beta), <75s (Launch)
- **Export Success:** >80% (Beta), >90% (Launch)
- **Character Consistency:** >90%
- **Cache Hit Rate:** >30%

### Quality Standards
- **Code Coverage:** >80%
- **TypeScript Strict Mode:** 100%
- **Security Vulnerabilities:** 0 critical/high
- **Availability:** 99.0% (Alpha/Beta), 99.5% (Launch)

### Cost Management
- **Monthly Budget:** $1,000 total
  - Claude API: $500
  - Infrastructure: $200
  - Third-party tools: $100
  - Buffer: $200
- **Cache target:** 50% inference cost reduction

---

## Development Phases

### Alpha (Month 1-2)
**Scope:** Scene Builder v1, 3 brains, character locking v1, basic export
**Exit Criteria:** >85% character consistency, 100 alpha creators, <5min time-to-first-lock

### Beta (Month 3-4)
**Scope:** 8 brains, 5 format templates, continuity v2, multi-format export
**Exit Criteria:** >90% consistency, p95 gen <90s, 1K active users

### Launch (Month 5-6)
**Scope:** Billing live, marketplace v1, credit system, mobile-responsive
**Exit Criteria:** $50K MRR, 5K users, 400+ paying, 99.5% uptime

---

## Key Principles for Agents

### 1. Specialization
Each agent owns a specific domain with clear boundaries. Don't overstep into another agent's territory.

### 2. Explicit Handoffs
Follow defined handoff protocols. Required artifacts must be complete before handoff.

### 3. Quality Gates
Never skip quality checks. All gates must pass before proceeding.

### 4. Escalation Protocol
Attempt autonomous resolution first (2h → 4h → 8h). Escalate to founder only after 24h or for critical issues.

### 5. Documentation
All decisions and artifacts must be documented for audit trail.

### 6. Cost Awareness
Always consider API costs, infrastructure costs, and optimization opportunities.

---

## Reference Documents

All agents should familiarize themselves with:
- **[solofounder-team/AGENT_PLAYBOOK.md](solofounder-team/AGENT_PLAYBOOK.md)** - Complete 16-agent guide
- **[solofounder](solofounder)** - Original agent team specification
- **[StoryForge_Technical_Architecture.md](StoryForge_Technical_Architecture.md)** - System design, data models, infrastructure
- **[StoryForge_Product_Blueprint.md](StoryForge_Product_Blueprint.md)** - Product vision, features, UX flows
- **[StoryForge_PRD.md](StoryForge_PRD.md)** - Requirements, success metrics, release gates
- **[StoryForge_6Month_Execution_Plan.md](StoryForge_6Month_Execution_Plan.md)** - Timeline and milestones
- **[StoryForge_Epic_Stories.md](StoryForge_Epic_Stories.md)** - Epic breakdown and user stories

---

## Success Metrics

### North Star Metric
**Completed Projects per User per Month:** Target 2.5 by Month 6

### Supporting Metrics
- **Activation:** 40% complete first project within 48h
- **Engagement:** DAU/MAU 25%
- **Retention:** Month 1 retention 35%
- **Monetization:** Free → Paid conversion 8%
- **Quality:** <3 iterations per scene
- **Satisfaction:** NPS +40

---

## Communication & Coordination

### Daily
- Sprint Coordinator generates progress summary
- Agents update task status in real-time

### Weekly
- Sprint review with completed work demo
- Metrics review and priority adjustment

### Bi-weekly
- Architecture review (ADRs, tech debt)
- Performance metrics assessment

### Monthly
- Strategic review (roadmap, budget)
- Agent performance optimization

### Milestone Gates
- Full review before Alpha, Beta, Launch phases
- Founder approval required for phase transitions

---

## Important Notes

### Content Safety
- **Prompt Moderation:** All prompts go through content policy enforcement
- **NSFW Detection:** All outputs scanned before delivery
- **Mature Aesthetic Toggle:** Relaxes style filters (not legality/ToS) for horror/thriller, fully logged
- **Watermarking:** All outputs tracked for origin verification

### Security
- **No secrets in code:** Use AWS Secrets Manager
- **JWT + OAuth 2.0:** Auth0 or Cognito
- **Data encryption:** AES-256 at rest, TLS 1.3 in transit
- **RBAC:** Role-based access control for all services

### Provider Routing
- **Primary:** Runway API for video generation
- **Fallback:** Sora → Kling → Stability AI (image-to-video)
- **Failover:** Automatic with circuit breaker pattern
- **Graceful Degradation:** Storyboard-only mode during outages

---

## Getting Started for New Agents

1. **Read this file completely**
2. **Review your agent-specific configuration** in `solofounder-team/agents/`
3. **Understand the RACI matrix** for your responsibilities
4. **Check current sprint status** with Sprint Coordinator
5. **Review handoff protocols** for your upstream/downstream agents
6. **Set up access** to necessary tools and services
7. **Introduce yourself** to related agents you'll work with

---

**Document Version:** 1.0
**Last Updated:** December 2024
**Maintained By:** Sprint Coordinator + Founder
**Questions?** Check the solofounder document or escalate to Sprint Coordinator
