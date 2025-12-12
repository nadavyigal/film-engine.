# StoryForge V2 - Development Plan

## Document Enhancement Log
| Date | Change | File | Status |
|------|--------|------|--------|
| 2024-12-11 | Fixed timeline inconsistency (Phase A/B validation) | Validation_Plan.md | ✅ |
| 2024-12-11 | Added detailed budget breakdown ($75K allocated) | Execution_Roadmap_16w.md | ✅ |
| 2024-12-11 | Added week-by-week execution tables | Execution_Roadmap_16w.md | ✅ |
| 2024-12-11 | Added system architecture diagram | MVP_Spec_StoryClip.md | ✅ |
| 2024-12-11 | Added complete database schema (6 tables) | MVP_Spec_StoryClip.md | ✅ |
| 2024-12-11 | Added API endpoint definitions | MVP_Spec_StoryClip.md | ✅ |
| 2024-12-11 | Added security model | MVP_Spec_StoryClip.md | ✅ |
| 2024-12-11 | Added unit economics model | MVP_Spec_StoryClip.md | ✅ |
| 2024-12-11 | Revised pricing tiers (fixed Pro tier loss) | GoToMarket_and_Pricing.md | ✅ |
| 2024-12-11 | Added founder content schedule | GoToMarket_and_Pricing.md | ✅ |
| 2024-12-11 | Added specific community targets | GoToMarket_and_Pricing.md | ✅ |
| 2024-12-11 | Added creator seeding criteria | GoToMarket_and_Pricing.md | ✅ |
| 2024-12-11 | Added conversion funnel targets | GoToMarket_and_Pricing.md | ✅ |
| 2024-12-11 | Added probability/impact risk matrix | Risks_and_Pivot_Options.md | ✅ |
| 2024-12-11 | Added technical risks section | Risks_and_Pivot_Options.md | ✅ |
| 2024-12-11 | Added search queries reference | Customer_Research_Log.md | ✅ |
| 2024-12-11 | Added outreach templates | Validation_Plan.md | ✅ |
| 2024-12-11 | Added qualification checklist | Validation_Plan.md | ✅ |
| 2024-12-11 | Restructured for Phase A/B workflow | Customer_Research_Log.md | ✅ |
| 2024-12-12 | Added build prep guide (repo/env/Supabase schema) | Phase1_Build_Prep.md | ✅ |

---

## Critical Issues Identified & Resolved

### 🔴 Issue 1: Timeline Conflict
**Problem:** Validation_Plan.md said "Weeks 1-2, run after MVP is demoable" but MVP build was Weeks 3-6.
**Resolution:** Split validation into Phase A (desk research, Weeks 1-2, before MVP) and Phase B (live demos, Weeks 7-10, after MVP).

### 🔴 Issue 2: Budget Gap
**Problem:** Only $55K of $75K was allocated across phases.
**Resolution:** Added explicit budget breakdown table showing $75K fully allocated with $5K buffer.

### 🔴 Issue 3: Pro Tier Unprofitable
**Problem:** At $0.40/scene, Pro tier (200 scenes for $50) lost $30/user.
**Resolution:** Revised to 100 scenes for $50 with $0.50/scene overage; targets 20% gross margin.

### 🟡 Issue 4: Missing Technical Specs
**Problem:** No database schema, API endpoints, or architecture defined.
**Resolution:** Added complete system architecture, 6-table schema, and 15+ API endpoints.

### 🟡 Issue 5: Vague GTM Plan
**Problem:** No specific communities, schedules, or selection criteria.
**Resolution:** Added specific Reddit/Discord targets, weekly content schedule, and creator qualification checklist.

---

## Execution Checklist (Week 1 Start)

### Before Writing Any Code
- [ ] Follow `Phase1_Build_Prep.md` for repo/env/Supabase setup
- [ ] Set up project repo with Next.js 14 + TypeScript
- [ ] Configure Supabase project (auth, database, storage)
- [ ] Create Runway/Pika API accounts and test endpoints
- [ ] Set up Vercel project with env vars
- [ ] Initialize database schema from MVP_Spec
- [ ] Create Figma mockups for demo calls

### Phase 0 (Weeks 1-2)
- [ ] Collect 30+ complaints using search queries
- [ ] Qualify complaints (3+ criteria each)
- [ ] DM top 15 complainers
- [ ] Conduct 5-8 discovery calls *(deferred; validation risk noted)*
- [ ] Fill in Phase A decision memo *(desk research completed; calls pending)*
- [ ] **GATE:** GO/PIVOT/KILL decision

### Phase 1 (Weeks 3-6)
- [ ] Week 3: Auth + UI shell
- [ ] Week 4: Character upload + storage
- [ ] Week 5: Scene generation + Runway integration
- [ ] Week 6: Timeline + export
- [ ] **GATE:** MVP demoable to beta users

## Phase 0 Runbook (Weeks 1-2)
Goal: 30+ qualified complaints, 5-8 discovery calls, and a GO/PIVOT/KILL memo before writing code.

### Daily Cadence
- [ ] Collect 10+ complaints/day using the queries in `Customer_Research_Log.md`; log URLs and quotes.
- [ ] Score each entry (severity 1-10, recency <90 days, tool, user type); mark "Qualified?" once 3+ criteria are met.
- [ ] After every 10 entries, add a 3-5 bullet pattern summary under the complaint table (themes, tools, failure mode, time cost).
- [ ] DM 3-5 highest-severity complainers with the Phase A script from `Validation_Plan.md`; note DM date/status in the table.
- [ ] Offer 3 call slots/day; book 1+/day until 5-8 calls are done; log booked calls in the discovery table.

### Evidence to Capture
- Complaint log: URL, exact quote, severity score, tool, segment, date, qualification note.
- Discovery calls: pain severity, time lost per project, current tools, willingness to try, key quote, date.
- Outreach trace: in the complaint table "Qualified?" cell, jot DM date + reply status (or add a temporary "DM status" column if clearer).

### Milestones & Gates
- Week 1 checkpoint (Day 7): >=10 qualified complaints, >=2 booked calls, pattern summary added.
- Week 2 gate (Day 14): 30+ complaints logged, Phase A decision memo drafted in `Customer_Research_Log.md` -> GO/PIVOT/KILL; discovery calls deferred to Phase B (risk noted).

---

## Key Metrics to Track

| Phase | Primary Metric | Target | Current |
|-------|----------------|--------|---------|
| 0 | Qualified complaints | 10+ | — |
| 0 | Positive discovery calls | 5+ | — |
| 1 | MVP completion | 100% | — |
| 2 | Beta commitments | 10+ | — |
| 3 | Paying users | 50 | — |
| 3 | MRR | $1,500 | — |
| 3 | Conversion rate | 25% | — |

---

## Next Actions
1. **Immediate:** Begin Phase 0 desk research (search Reddit/Twitter/Discord)
2. **This week:** Set up Supabase project and Runway API test account
3. **Before Week 3:** Complete 30+ complaint collection and 5+ discovery calls
4. **Week 2 end:** Make GO/PIVOT/KILL decision on problem validation

---

## Notes & Learnings
*(Add ongoing notes here as you execute)*
