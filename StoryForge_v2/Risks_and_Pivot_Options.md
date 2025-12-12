# Risks & Pivot Options

## Risk Matrix (Near-Term)

| Risk | Probability | Impact | Score | Priority |
|------|-------------|--------|-------|----------|
| Demand overestimated | Medium (40%) | Critical | 🔴 HIGH | P1 |
| Model dependency (API changes) | Medium (35%) | High | 🟠 MED-HIGH | P2 |
| Unit economics negative | High (60%) | High | 🔴 HIGH | P1 |
| Scope creep | Medium (50%) | Medium | 🟡 MEDIUM | P3 |
| Activation friction | High (60%) | Medium | 🟠 MED-HIGH | P2 |
| Technical debt / outages | Low (20%) | Medium | 🟢 LOW | P4 |
| Competition launches similar | Medium (40%) | Low | 🟢 LOW | P4 |

*Score = Probability × Impact. Priority based on score + time-sensitivity.*

---

## Key Risks (Detailed)

### 🔴 P1: Demand Overestimated
- **Signal:** Cannot secure 10 committed beta users in Phase 0/2.
- **Mitigation:** 
  - Phase 0 desk research validates demand BEFORE building
  - Pivot offer/user segment quickly if interviews are lukewarm
  - Kill threshold: <5 commitments after 2 attempts
- **Owner:** Founder
- **Decision Point:** Week 2 (Phase 0 gate), Week 10 (Phase 2 gate)

### 🔴 P1: Unit Economics Negative
- **Signal:** Cost per scene exceeds revenue per scene at scale.
- **Mitigation:**
  - ✅ Revised pricing tiers (see GoToMarket doc) with 20% margin target
  - Negotiate volume pricing with Runway at 10K scenes/month
  - Implement scene caching (same prompt = no re-render)
  - Overage pricing as profit center
- **Owner:** Founder + Eng
- **Decision Point:** Week 6 (baseline cost known), Week 14 (scale economics)

### 🟠 P2: Model Dependency
- **Signal:** Runway/Pika costs spike >50%, latency >60s, or API deprecated.
- **Mitigation:**
  - Provider abstraction layer (swap Runway↔Pika without code changes)
  - Regen limits (max 3 per scene)
  - Queue UI with status (perceived latency < actual)
  - Keep prompts portable (no provider-specific syntax)
  - Monitor for new providers (Luma, Kling, etc.)
- **Owner:** Eng
- **Decision Point:** Ongoing; escalate if costs exceed 2x baseline

### 🟠 P2: Activation Friction
- **Signal:** <50% of signups generate first scene.
- **Mitigation:**
  - Guided onboarding (preset character + first prompt suggested)
  - Example project users can clone/remix
  - Clear credit countdown with "use it or lose it" messaging
  - Simplify character upload (accept fewer images initially)
- **Owner:** Founder + Designer
- **Decision Point:** Week 8 (first beta cohort data)

### 🟡 P3: Scope Creep
- **Signal:** Team discusses features beyond current phase scope.
- **Mitigation:**
  - Decision gates in Execution_Roadmap enforce discipline
  - Any scope add requires hitting prior success metrics
  - Feature requests logged but not acted on until validated
- **Owner:** Founder
- **Decision Point:** Every phase gate

---

## Technical Risks (Added)

| Risk | Probability | Impact | Mitigation |
|------|-------------|--------|------------|
| Runway API rate limits | Medium | High | Queue system, retry logic, backoff |
| Supabase storage limits | Low | Medium | Monitor usage; upgrade tier if >5GB |
| ffmpeg serverless timeout | Medium | Medium | Chunk exports; use background job |
| CORS/auth issues | Low | Low | Strict whitelist; test early |
| Credit double-deduction | Medium | High | Idempotency tokens on all mutations |

## Pivot Options (If Gates Missed)
- **Feature pivot:** Narrow to character lock-as-a-service (reference → prompt fragment) without generation/export.
- **User pivot:** Shift to filmmakers/marketers if TikTok creators stall; adjust templates accordingly.
- **Business model pivot:** Done-for-you service or credits-only pricing if SaaS subs lag.
- **Product pivot:** If templates outperform generation, emphasize storyboarding/timeline and integrate external renders.

## Post-PMF Risk (When Scaling)
- **Competition copies workflow:** Defend with data-driven templates/styles and continuity tools; build collaboration and marketplace only after usage demand.
- **Infra scale:** Move from monolith when >1K WAU; introduce service boundaries for rendering/export and auth/credits first.
