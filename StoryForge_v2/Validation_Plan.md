# Validation Plan
Objective: Secure 10 strong beta commitments from creators actively complaining about character/continuity drift. Two-phase approach: desk research first, live validation after MVP.

---

## PHASE A: Desk Research (Weeks 1-2) — BEFORE MVP BUILD
Goal: Confirm the problem exists at scale. If <10 meaningful complaints found, pivot before writing code.

### Daily Actions (Phase A)
- **Day 1-3:** Collect 30+ public complaints using search queries below. Log in `Customer_Research_Log.md`.
- **Day 4-7:** Categorize by severity, user type, recency. Identify top 15 high-severity complainers.
- **Day 8-10:** Cold DM top 15 using outreach script; target 8+ replies confirming pain.
- **Day 11-14:** Conduct 5-8 discovery calls (no product shown); validate pain depth and willingness to try a solution.

### Search Queries to Use
```
Reddit: r/aivideo, r/runwayml, r/StableDiffusion, r/midjourney
- "character consistency" OR "same character" + frustrated/issue/problem
- "drift" + video/generation
- "continuity" + AI video

Twitter/X:
- "runway gen-4" + consistency/drift/character
- "pika labs" + character/consistent
- "AI video" + "same character" + frustrating

Discord (Runway, Pika, AI Art):
- Search #help and #feedback channels for "consistency" "drift" "character"
```

### Phase A Gate
- **GO to MVP Build:** ≥10 recent (<90 days), meaningful complaints + ≥5 positive discovery call responses
- **PIVOT:** 5-9 complaints or lukewarm calls — narrow problem definition or shift user segment
- **KILL:** <5 complaints — problem doesn't exist at scale; abandon or radically pivot

---

## PHASE B: Live Validation (Weeks 7-10) — AFTER MVP IS DEMOABLE
Goal: Convert desk research contacts + new outreach into 10 explicit beta commitments using the working product.

### Daily Actions (Phase B)
- **Day 1-3:** Re-contact all Phase A respondents + 20 new complainers from ongoing monitoring.
- **Day 3-7:** Run 15 demo calls (20 min each) showing live MVP; use interview script below.
- **Day 7-10:** Secure commitments on calls; add to early access list with "I will use this week" confirmation.
- **Day 11-14:** Follow-ups with maybes; document objections and feature requests.

## Phase B Success / Failure Gates
- **GO to Launch:** ≥10 explicit "I will use this in the beta" commitments, repeated pain language, clear use-case pattern.
- **PIVOT:** 5-9 commitments — adjust offer (price/feature), user segment, or framing; rerun for 1 week.
- **KILL:** ≤4 commitments — problem/solution mismatch; stop further development.

## Interview Script (15 Minutes)
1) Context: “What do you make? How often?”
2) Pain: “Walk me through the last time consistency failed.”
3) Attempts: “What did you try? How long did it take?”
4) Impact: “How many hours per project does this cost?”
5) Value: “What would you pay monthly if solved?” (for willingness only; no ask to pay)
6) Show mock: character upload → prompt → timeline → export.
7) Ask: “I’m shipping this in ~4 weeks. Can I count on you to try it and give feedback in week 3? I’ll reserve you early access and a locked discount when pricing goes live.”

## Offer
- Early-access spot with 20 beta scenes included; no payment collected now.
- Promise to honor a discounted price at launch for committed beta users (e.g., first 50 get lifetime $20/mo); collect payment only after they’ve tried it.

## Outputs Required
**Phase A (Weeks 1-2):**
- 30+ complaint log with severity scores
- 5-8 discovery call notes (pain depth, current tools, time lost)
- Problem validation memo: GO/PIVOT/KILL decision

**Phase B (Weeks 7-10):**
- 15 demo call notes with reactions and objections
- Commitment confirmations (names/handles, intent to use, preferred price signal)
- Objection summary + top 3 feature requests
- Final GO/PIVOT/KILL decision memo (add to `Metrics_and_Decision_Gates.md`)

---

## Outreach Templates

### Cold DM Script (Phase A - Discovery)
```
Hey [Name]! Saw your post about [specific pain point they mentioned].

I'm building a tool to solve exactly this - keeping characters consistent across AI video scenes.

Would you have 10 mins this week to tell me more about your workflow? 
Not selling anything, just trying to understand the problem better.

— [Your name]
```

### Demo Call Invite (Phase B)
```
Hey [Name]! We talked a few weeks ago about character consistency issues.

I've built a working prototype that lets you lock character references and generate consistent multi-scene clips. 

Would you have 20 mins to try it live and give me feedback? 
If it helps, I'll give you early access + 20 free scenes.

— [Your name]
```

---

## Qualification Criteria
A "meaningful" complaint must have:
- [ ] Recency: Posted within last 90 days
- [ ] Specificity: Mentions specific tool (Runway/Pika/etc.) AND specific problem (drift/consistency)
- [ ] Severity signal: Words like "frustrating," "hours wasted," "can't," "impossible"
- [ ] Creator type: Makes serialized/episodic content (check their profile)
