# StoryForge Agent Team

**Your complete autonomous development team** - 16 specialized agents working together to build StoryForge with minimal founder intervention.

---

## 📖 Start Here: [AGENT_PLAYBOOK.md](AGENT_PLAYBOOK.md)

**The complete guide** to your 16-agent team - everything in one place:
- ✓ All 16 agent briefs (mission, responsibilities, inputs/outputs)
- ✓ Task routing and coordination protocols
- ✓ Quality gates for Alpha, Beta, Launch phases
- ✓ Handoff procedures and escalation guidelines
- ✓ Quick reference tables and success metrics

---

## Quick Navigation

### For Solo Founder

| What You Need | Where to Go |
|---------------|-------------|
| **Complete agent guide** | [AGENT_PLAYBOOK.md](AGENT_PLAYBOOK.md) |
| **Project overview** | [CLAUDE.md](../CLAUDE.md) |
| **Setup summary** | [AGENT_SETUP_COMPLETE.md](../AGENT_SETUP_COMPLETE.md) |
| **Deep dive on critical agents** | [agents/](agents/) directory |

### For Claude Code (Acting as Agent)

1. **Read project context:** [CLAUDE.md](../CLAUDE.md)
2. **Read the playbook:** [AGENT_PLAYBOOK.md](AGENT_PLAYBOOK.md)
3. **Find your agent:** Look up in Agent Directory section
4. **Check detailed config:** If you're one of the 3 critical agents, see [agents/](agents/)
5. **Execute:** Follow your agent's process

---

## What's in This Directory

```
solofounder-team/
├── README.md                      # This file - your starting point
├── AGENT_PLAYBOOK.md              # 📖 Complete 16-agent guide (main resource)
└── agents/                        # Detailed configs for 3 critical agents
    ├── sprint-coordinator.md      # Task routing & progress tracking
    ├── data-engineering.md        # Database schema & caching
    └── qa-orchestrator.md         # Quality gates & release readiness
```

---

## The 16-Agent Team

### 🔧 Claude Code Agents (8 - Technical)
1. **Code Review** - Quality, security, standards enforcement
2. **Debug Specialist** - Error diagnosis and resolution
3. **Test Automation** - Unit, integration, E2E testing
4. **Documentation** - API docs, ADRs, guides
5. **DevOps** - CI/CD, deployment, monitoring
6. **Security** - Vulnerability scanning, auth review
7. **Performance** - Optimization, caching, Core Web Vitals
8. **API Integration** - Third-party integrations (Runway, Sora, etc.)

### 💼 BMAD Agents (5 - Business & Strategy)
9. **Business Analyst** - Requirements and user stories
10. **Marketing** - GTM strategy and content
11. **Architecture** - System design and tech specs
12. **Design (UX/UI)** - Design system and user experience
13. **Product Owner** - Roadmap and prioritization

### ⭐ Critical New Agents (3 - Coordination)
14. **Sprint Coordinator** - ✓ Central task routing and progress tracking
15. **Data Engineering** - ✓ Database schema, caching, sync protocols
16. **QA Orchestrator** - ✓ Quality gates and release readiness

---

## Quick Start

### Test the System

Try this sample task to see how agents work:

```
"Sprint Coordinator, route this task:

Category: DATA
Description: Design the initial database schema for Projects, Scenes,
and Characters tables including face embeddings for character locking.
Priority: High

Show me what the Data Engineering Agent proposes."
```

Expected: Data Engineering Agent will provide complete schema design with PostgreSQL + Dexie.js, caching strategy, and migration plan.

### Start Your First Sprint

```
"Sprint Coordinator, let's create the first sprint backlog for Alpha phase.
Break down the requirements from StoryForge_PRD.md into tasks and assign
them to appropriate agents."
```

### Get Daily Summary

```
"Sprint Coordinator, generate today's daily summary showing:
- Tasks completed
- Tasks in progress
- Blockers and recommendations
- Metrics snapshot"
```

---

## How It Works

### Task Flow Example

```
You → Sprint Coordinator → Appropriate Agent → Work Done → Handoff → Next Agent

Example:
"Add new brain type" (FEAT)
  ↓
Sprint Coordinator routes to Architecture
  ↓
Architecture creates technical spec
  ↓
Hands off to Design for UI
  ↓
Design creates wireframes
  ↓
Hands off to Development
  ↓
Development implements with tests
  ↓
Code Review approves
  ↓
QA Orchestrator validates
  ↓
DevOps deploys
  ↓
Done! ✓
```

### Task Categories (Quick Reference)

| Code | Agent | Example |
|------|-------|---------|
| **FEAT** | Architecture → Design → Dev | "Add scene builder timeline" |
| **BUG** | Debug → Code Review | "Character consistency fails" |
| **DATA** | Data Engineering | "Design caching strategy" |
| **PERF** | Performance | "Optimize generation time" |
| **SEC** | Security | "Review auth flow" |
| **TEST** | Test Automation | "Add E2E tests" |
| **DOCS** | Documentation | "Update API docs" |
| **INFRA** | DevOps | "Setup CI/CD" |

---

## Quality Gates

### Alpha (Month 2)
- Character consistency >85%
- Scene Builder + 3 brains functional
- Basic CRUD operations
- Time-to-first-lock <5 min
- 100 alpha creators onboarded

### Beta (Month 4)
- Character consistency >90%
- p95 generation <90s
- Export success >80%
- Cache hit rate >30%
- 8 brains, 5 format templates
- 1,000 beta users active

### Launch (Month 6)
- Character consistency >92%
- p95 generation <75s
- Billing/tiers live
- Marketplace v1
- $50K MRR, 5K users, 400+ paying
- Uptime 99.5%

---

## Daily Workflow

**Your 10-Minute Daily Routine:**

1. **Morning:** Ask Sprint Coordinator for yesterday's summary
2. **Review:** Tasks completed, in progress, blocked
3. **Check:** Metrics, alerts, budget burn
4. **Decide:** Approve escalations or adjust priorities
5. **Done:** Agents continue autonomous work

**Agents handle:**
- Task execution
- Quality checks
- Handoffs
- Progress tracking
- Blocker resolution (up to 24h)

**You handle:**
- Strategic decisions
- Quality gate approvals (Alpha, Beta, Launch)
- Escalations (after agents try for 24h)
- Roadmap adjustments

---

## Reference Documents

All agents use these as source context:

**Primary:**
- [solofounder](../solofounder) - Original 16-agent specification
- [CLAUDE.md](../CLAUDE.md) - Project overview and context
- [AGENT_PLAYBOOK.md](AGENT_PLAYBOOK.md) - This team's complete guide

**Supporting:**
- [StoryForge_PRD.md](../StoryForge_PRD.md) - Requirements and success metrics
- [StoryForge_Technical_Architecture.md](../StoryForge_Technical_Architecture.md) - System design
- [StoryForge_Product_Blueprint.md](../StoryForge_Product_Blueprint.md) - Product vision
- [StoryForge_6Month_Execution_Plan.md](../StoryForge_6Month_Execution_Plan.md) - Timeline
- [StoryForge_RACI.md](../StoryForge_RACI.md) - Responsibility matrix
- [StoryForge_GTM_Plan.md](../StoryForge_GTM_Plan.md) - Go-to-market

---

## Success Metrics

### Agent Performance
- Task routing accuracy: >90%
- Sprint completion rate: >85%
- Blocker resolution: <24h avg
- Handoff smoothness: <10% rework

### Project Health
- Code coverage: >80%
- Character consistency: >90%
- p95 generation time: <90s
- System availability: >99%
- Budget burn: <$1,000/month

---

## Support

**Questions about agents?**
→ Check [AGENT_PLAYBOOK.md](AGENT_PLAYBOOK.md)

**Need detailed agent config?**
→ See [agents/](agents/) directory for Sprint Coordinator, Data Engineering, QA Orchestrator

**Questions about the project?**
→ Check [CLAUDE.md](../CLAUDE.md)

**System not working as expected?**
→ Review [AGENT_SETUP_COMPLETE.md](../AGENT_SETUP_COMPLETE.md)

---

## Status

✅ **Setup Complete** - Ready for first sprint!

**What's Working:**
- 16-agent team fully configured
- Task routing system defined
- Quality gates established
- Handoff protocols documented
- 3 critical agents have detailed configs

**Next Steps:**
1. Test with a sample task
2. Create first sprint backlog
3. Begin Alpha development

---

**Version:** 1.0
**Last Updated:** December 2024
**Maintained By:** Sprint Coordinator Agent

---

## Get Started Now

**Recommended first action:**

```
"Sprint Coordinator, I'm ready to start. Please:
1. Confirm all agents are aware of their responsibilities
2. Show me the task routing schema
3. Generate a template daily summary
4. Recommend how to structure our first sprint for Alpha phase"
```

This will verify the system is working and set you up for success!
