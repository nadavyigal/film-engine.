# StoryForge: Lean Path to PMF
## Executive Action Plan
### 16 Weeks to Validation | $75K Budget

---

## TL;DR

**Current Plan:** 6 months, $960K, 12 people, launch with everything
**Lean Plan:** 16 weeks, $75K, 2 people, validate then scale
**Key Insight:** Character consistency is solved by Runway Gen-4. Our value is the WORKFLOW layer.

---

## The Pivot

### FROM:
Building a platform with 8 brains, 5 formats, microservices, marketplace

### TO:
Validating that creators will pay for AI video workflow tools, THEN building the platform

---

## 16-Week Roadmap

### Weeks 1-2: VALIDATE OR KILL
**Goal:** Get 10 people to pre-pay $20

**Actions:**
1. Scrape Reddit/Twitter for 30 creators complaining about character consistency
2. DM them: "I'm building X. 15-min call?"
3. Interview script:
   - "Walk me through the last time this happened"
   - "What did you try?"
   - "How much time did it waste?"
   - Show Figma mockup
   - "Would you pre-pay $20 for first access in 3 weeks?"

**Success:** 10 pre-payments = $200 revenue
**Failure:** <10 pre-payments = KILL or PIVOT

**Cost:** $0 (pure hustle)

---

### Weeks 3-6: BUILD MVP
**Product:** "StoryClip" - Character reference + scene generation + timeline

**Features:**
- Upload 3-5 character reference images
- Generate scenes with character consistency (via Runway Gen-4 API)
- Simple timeline view
- Export as MP4

**NOT Included:**
- No "Brains" (just prompts)
- No "Formats" (no story templates)
- No fine-tuning sliders
- No collaboration
- No marketplace

**Tech Stack:**
- Next.js 14 + Vercel
- Supabase (DB + Auth + Storage)
- Runway Gen-4 API

**Team:** 1 founder + 1 contract engineer
**Cost:** $15K

**Success:** Deliver to 10 pre-paid users in 4 weeks

---

### Weeks 7-10: ITERATE & EXPAND
**Goal:** 50 users, $150 MRR

**Actions:**
1. Weekly interviews with all 10 beta users
2. Identify #1 feature request → Build it
3. Invite 40 more users from waitlist
4. Charge $10/month (early pricing)

**Key Metrics:**
- Scenes per user (engagement)
- Project completion rate
- Would pay monthly (survey)

**Success:** 30% conversion (15 paying) = $150 MRR
**Failure:** <10% conversion = PIVOT (different features or users)

**Team:** 1 founder + 1 engineer
**Cost:** $20K

---

### Weeks 11-14: ADD VALUE
**Goal:** 200 users, $1,500 MRR

**Product Additions:**
- Format Templates v1: "TikTok Series" + "Short Film"
- Style Presets: Thriller, K-Drama, TikTok Native (prompt engineering, not ML)
- Billing: Stripe integration, 3 tiers (Free/Creator/Pro)

**Growth:**
- Product Hunt launch
- Founder content: "How I made a TikTok series with AI in 2 hours"
- Seed 20 TikTok creators with free Pro accounts

**Success:** 200 users, 50 paying (25%), $1,500 MRR
**Failure:** Stagnant growth = PIVOT (positioning, user segment, or pricing)

**Team:** 1 founder + 1 engineer + 1 contract designer
**Cost:** $25K

---

### Weeks 15-16: DECIDE
**PMF Signals (YES → SCALE):**
- MRR growth >15% month-over-month
- 25%+ free-to-paid conversion
- Users generating 25+ scenes/month
- Organic word-of-mouth
- Clear pattern: "Users who do X become paying customers"

**No PMF (PIVOT):**
- <10% conversion
- Users ghost after first session
- Find different use case users love

**Kill Signals:**
- No engagement
- Unit economics don't work
- No path to profitability

**Team:** 1 founder + 1 engineer
**Cost:** $15K

---

## IF SCALE (Week 17+)

### Raise Seed Round
**Traction to Show:**
- $1,500+ MRR
- 200 users, 50 paying
- 25% conversion rate
- 15% MoM growth
- Clear roadmap

**Raise:** $2M-4M seed

### Execute Full StoryForge Vision
**Now build:**
- 8 Cinematic Brains (ML-based, trained on validated user preferences)
- 5 Format Templates (validated by usage data)
- Advanced Continuity Dashboard
- Collaboration Features
- Marketplace (if users are requesting it)
- Mobile App

**Team:** Hire 8-12 people
**Timeline:** 6-12 months to full platform
**Goal:** $50K MRR

---

## Cost Breakdown

| Phase | Duration | Team | Cost |
|-------|----------|------|------|
| Validation | 2 weeks | Founder | $0 |
| MVP Build | 4 weeks | Founder + 1 eng | $15K |
| Iterate | 4 weeks | Founder + 1 eng | $20K |
| Scale Validation | 4 weeks | Founder + 1 eng + 1 design | $25K |
| Decision | 2 weeks | Founder + 1 eng | $15K |
| **TOTAL** | **16 weeks** | **2 people** | **$75K** |

**Compare to Original:**
- Original M1-M4 cost: $540K
- Lean approach: $75K
- **Savings: $465K**

---

## Key Metrics Dashboard

### Weeks 1-2 (Validation):
- [ ] 30 pain point posts collected
- [ ] 15 user interviews completed
- [ ] 10 pre-payments secured ($200)

### Weeks 3-10 (MVP):
- [ ] 10 beta users onboarded
- [ ] Average 10+ scenes per user
- [ ] 6/10 would pay monthly
- [ ] Expand to 50 users
- [ ] 30% conversion rate (15 paying)
- [ ] $150 MRR

### Weeks 11-16 (Scale Validation):
- [ ] 200 total users
- [ ] 50 paying users (25% conversion)
- [ ] $1,500 MRR
- [ ] 15% MoM growth
- [ ] 40% project completion rate

---

## Decision Trees

### Week 2 Decision:
```
10+ pre-payments?
├─ YES → Build MVP (Weeks 3-6)
└─ NO → Kill or Pivot
    ├─ Pivot Option 1: Different feature (storyboarding tool)
    ├─ Pivot Option 2: Different user (filmmakers not TikTok)
    └─ Kill: Problem not painful enough
```

### Week 10 Decision:
```
$150 MRR + 30% conversion?
├─ YES → Add templates + styles (Weeks 11-14)
└─ NO → Pivot
    ├─ Pivot Option 1: Different feature set
    ├─ Pivot Option 2: Different pricing
    └─ Kill: Users won't pay for this solution
```

### Week 16 Decision:
```
$1,500 MRR + 25% conversion + 15% growth?
├─ YES → SCALE
│   └─ Raise seed → Hire team → Build full vision
└─ NO → Pivot or Kill
    ├─ Pivot: Found different use case users love
    └─ Kill: No product-market fit
```

---

## What Changes from Original Plan

### KEEP (Core Value):
- Target user: TikTok/YouTube creators making serialized content
- Format Templates (narrative scaffolding)
- Scene Builder (iteration workflow)
- Multi-scene project management
- Vision of workflow layer above AI models

### DELAY (Post-PMF):
- 8 Cinematic Brains → Start with 3 style presets
- Microservices → Start with monolith
- Marketplace → Only if users request
- Voice synthesis → Post-PMF
- Mobile app → Post-PMF
- Collaboration → Post-PMF

### REPLACE:
- "Character consistency engine" → Use Runway Gen-4 API
- Custom ML models → Third-party APIs
- 16-agent team → 2-person team
- 6-month plan → 16-week validation

---

## Risk Mitigation

### Risk: "We can't get 10 pre-payments"
**Mitigation:** GOOD. You just saved $960K by not building something nobody wants.

### Risk: "We build MVP but users don't use it"
**Mitigation:** Only $15K sunk cost. Pivot to what users DO want.

### Risk: "We find PMF but it's smaller than we thought"
**Mitigation:** Better a real $10K MRR business than a fake $50K MRR plan.

### Risk: "Competitors move faster"
**Mitigation:** Lean approach = 10x faster learning. You'll out-iterate them.

### Risk: "We miss the big platform vision"
**Mitigation:** You still build it, just AFTER validating users want it.

---

## What to Do Tomorrow

### Founder Actions (Day 1):

**Morning:**
1. Decision: Commit to lean path or original path
2. If lean: Cancel Month 1 hiring plans
3. Create validation spreadsheet (30 users to contact)

**Afternoon:**
1. Write DM template for outreach
2. Create interview guide (10 questions)
3. Design pre-payment offer page

### Founder Actions (Day 2-5):

1. Scrape Reddit: r/StableDiffusion, r/Midjourney, r/Filmmakers, r/TikTokCreators
2. Search Twitter: "Runway consistency," "Pika character," "AI video frustrating"
3. Collect 30 posts with URLs
4. Begin DM outreach

### Week 2:
1. Conduct 15 user interviews
2. Collect 10 pre-payments
3. Make decision: Build or Kill

---

## Success Looks Like

### Week 16:
- $1,500 MRR with 200 users
- 50 paying customers who love the product
- Clear understanding of what features drive value
- Validated pricing and user segment
- Product-market fit signal strong enough to raise seed

### Month 12 (after raising seed):
- $50K MRR
- 5,000 users, 400 paying
- Full StoryForge platform live
- 8 Brains, 5 Formats, Marketplace
- Team of 10-12
- Path to Series A clear

---

## The Bottom Line

You have two paths:

**Path A (Original):** 6 months, $960K, 12 people, launch everything, hope it works

**Path B (Lean):** 16 weeks, $75K, 2 people, validate with users, THEN build everything

**Both paths can reach the same destination.**

**Path B just proves people want to get there before you buy the bus.**

---

**Prepared By:** Mary, Business Analyst
**Date:** December 2024
**Status:** AWAITING FOUNDER DECISION
**Next Action:** Commit to Path A or Path B by EOW
