# Metrics & Decision Gates

## Core Metrics by Phase

### Phase 0: Desk Research (Weeks 1-2)
| Metric | Target | How to Measure |
|--------|--------|----------------|
| Complaints collected | 30+ | Customer_Research_Log.md |
| Qualified complaints | 10+ | Meet 3+ criteria on checklist |
| Discovery calls completed | 5-8 | Interview notes logged |
| Pain severity (avg) | ≥7/10 | Self-reported in calls |
| Willingness to try solution | ≥60% | Call notes |

### Phase 1: MVP Build (Weeks 3-6)
| Metric | Target | How to Measure |
|--------|--------|----------------|
| MVP completion | 100% | All 5 features deployed |
| Internal demo success | 3/3 testers | Can complete full flow |
| Cost per scene (baseline) | <$0.50 | Runway API billing |
| Export success rate | >90% | ffmpeg job logs |

### Phase 2: Live Validation (Weeks 7-10)
| Metric | Target | How to Measure |
|--------|--------|----------------|
| Demo calls completed | 15 | Interview notes |
| Beta commitments | 10+ | Early access list |
| Demo reaction (avg) | ≥7/10 | Self-reported |
| Activation rate | >60% | % generating first scene |
| Scenes per user | ≥10 | Database query |

### Phase 3: Launch & Scale (Weeks 11-14)
| Metric | Target | How to Measure |
|--------|--------|----------------|
| Total users | 200 | Supabase auth count |
| Paying users | 50 | Stripe dashboard |
| Conversion rate | 25% | Paying / total users |
| MRR | $1,500 | Stripe MRR |
| MoM growth | >15% | Week 14 vs Week 12 |
| Gross margin | >20% | (Revenue - API costs) / Revenue |

---

## Decision Gates

### Week 2: Research Gate (Phase 0 → Phase 1)
| Outcome | Criteria | Action |
|---------|----------|--------|
| **GO** | ≥10 qualified complaints + ≥5 positive discovery calls | Proceed to MVP build |
| **PIVOT** | 5-9 complaints OR lukewarm calls | Narrow problem definition OR shift user segment; rerun 1 week |
| **KILL** | <5 complaints OR <3 positive calls | Problem doesn't exist at scale; abandon or radically pivot |

### Week 10: Validation Gate (Phase 2 → Phase 3)
| Outcome | Criteria | Action |
|---------|----------|--------|
| **GO** | ≥10 beta commitments + avg demo reaction ≥7 | Launch with templates + billing |
| **PIVOT** | 5-9 commitments | Adjust offer/pricing/segment; rerun outreach 1 week |
| **KILL** | ≤4 commitments | Product-market mismatch; major pivot or kill |

### Week 14: Launch Gate (Phase 3 → Phase 4)
| Outcome | Criteria | Action |
|---------|----------|--------|
| **GO** | ≥30 paying users + $500 MRR + >20% conversion | Add more templates/styles; continue scaling |
| **PIVOT** | 15-29 paying OR 10-20% conversion | A/B test pricing/features; adjust messaging |
| **KILL** | <15 paying OR <10% conversion | Major pivot needed |

### Week 16: Scale Gate (Phase 4 → Scale/Kill)
| Outcome | Criteria | Action |
|---------|----------|--------|
| **SCALE** | ≥50 paying + $1.5K MRR + >25% conversion + >15% MoM | Raise seed; hire team |
| **PIVOT** | $500-1.5K MRR + 10-25% conversion | Tighten conversion; test new segments |
| **KILL** | <$500 MRR OR <10% conversion OR negative MoM | Shut down or radical pivot |

## Instrumentation Requirements
- Event schema in `MVP_Spec_StoryClip.md` implemented before beta.
- Dashboards for: scenes/user, exports/user, failure rates by provider, conversion funnels, credit burn, template/style adoption.
- Weekly reporting cadence; publish to Discord and keep snapshots in this folder.

## Decision Memos
- For each gate, add a short memo here: date, metrics, decision (GO/PIVOT/KILL), next actions.
