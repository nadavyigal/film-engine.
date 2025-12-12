# 16-Week Execution Roadmap
Budget target: $75K. Team: founder + 1 eng (designer part-time in Weeks 11-14).

## Budget Breakdown
| Phase | Weeks | Allocation | Notes |
|-------|-------|------------|-------|
| Phase 0 | 1-2 | $2K | Tools, domain, Figma, minor outreach |
| Phase 1 | 3-6 | $18K | MVP dev, Supabase, Vercel, Runway API testing |
| Phase 2 | 7-10 | $10K | Validation, increased API usage, support tools |
| Phase 3 | 11-14 | $30K | Designer, marketing, PH, creator seeding, infra scale |
| Phase 4 | 15-16 | $10K | Optimization, decision buffer |
| **Buffer** | — | $5K | Contingency for overruns |
| **Total** | — | **$75K** | |

---

## Phase 0 (Weeks 1-2): Desk Research Sanity Check
**Budget: $2K**

- Actions: Collect 30+ public complaints (Reddit/Twitter/Discord); categorize pain, severity, and user type. Run 5-8 discovery calls. No product demo yet.
- Deliverables: Complaint log, pattern summary, discovery call notes, build/kill decision based on evidence of repeated pain.
- Gate: If <10 meaningful, recent complaints from target users + <5 positive discovery calls → reconsider or pivot problem before building.

## Phase 1 (Weeks 3-6): Build StoryClip MVP
**Budget: $18K** (Dev time $12K, Infra $3K, API testing $3K)

- Scope: Auth/credits, character upload, single-option scene gen, timeline, concatenated export, lean admin.
- Deliverables: Deployed MVP (internally demoable + to 2-3 friendly testers); credits provisioned; support channel live.
- Success: MVP stable enough to demo; export works end-to-end; baseline latency/cost understood.

**Week-by-Week Breakdown:**
| Week | Focus | Deliverable |
|------|-------|-------------|
| 3 | Setup + Auth | Repo, CI/CD, Supabase auth, basic UI shell |
| 4 | Character System | Upload, storage, character cards, metadata |
| 5 | Scene Generation | Runway/Pika integration, prompt builder, regen logic |
| 6 | Timeline + Export | Drag-drop, ffmpeg concat, download, admin panel |

## Phase 2 (Weeks 7-10): Validate with Live MVP
**Budget: $10K** (Increased API usage $5K, Support tools $2K, Outreach $3K)

- Actions: Run Phase B of validation plan; demo to 20+ creators; secure 10 explicit beta commitments.
- Deliverables: 15 demo call notes, objection/feature summary, early access list, GO/PIVOT/KILL decision.
- Success: 10 commitments, repeated pain language, clear use-case pattern. If not, pivot before scaling.

**Key Activities:**
| Week | Focus |
|------|-------|
| 7 | Re-engage Phase A contacts, new outreach |
| 8-9 | Demo calls (3-4 per day target) |
| 10 | Follow-ups, decision memo, prep for launch |

## Phase 3 (Weeks 11-14): Add Value & Launch
**Budget: $30K** (Designer $8K, Marketing $7K, Infra scale $10K, Creator seeding $5K)

- Product: Add top-requested feature from validation + 2 format templates (TikTok Series, Short Film), 3 style presets, Stripe billing.
- GTM: Product Hunt launch, founder content push, seed 20 creators with free Pro.
- Success: 200 users, 50 paying (25%), $1.5K MRR, 15% MoM growth.

**Week-by-Week:**
| Week | Focus |
|------|-------|
| 11 | Stripe integration, billing UI, top feature build |
| 12 | Templates + presets, designer polish, PH prep |
| 13 | Product Hunt launch, creator seeding starts |
| 14 | Conversion optimization, founder content blitz |

## Phase 4 (Weeks 15-16): Decide
**Budget: $10K** (Optimization, buffer for pivots)

- Evaluate metrics vs. PMF signals; tighten conversion and onboarding.
- A/B test pricing, onboarding flows, and messaging.
- Decision: SCALE (raise seed), PIVOT (feature/user/pricing), or KILL.

**Decision Matrix:**
| Scenario | MRR | Conversion | Growth | Decision |
|----------|-----|------------|--------|----------|
| Strong PMF | >$1.5K | >25% | >15% MoM | SCALE |
| Weak PMF | $500-1.5K | 10-25% | 5-15% MoM | PIVOT |
| No PMF | <$500 | <10% | <5% MoM | KILL |

## If Scale (Week 17+)
- Fundraise with proof points ($1.5K MRR, 200 users, 25% conversion, 15% MoM).
- Hire ML/FE/design/marketing; expand to 8 Brains, 5 Formats, continuity dashboard, collaboration, marketplace.
