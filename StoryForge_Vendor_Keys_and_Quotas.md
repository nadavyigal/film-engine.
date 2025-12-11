# StoryForge Vendor Keys & Quotas (Launch Readiness)
## Internal-only — do not commit secrets

---

## Primary/Secondary Video Providers
- Runway (Primary)
  - Keys: PROD, STAGING
  - Quotas: target launch-week capacity; confirm rate limits; enable alerts on throttle.
  - Notes: Used for main video synthesis; routed first.

- Sora (Fallback)
  - Keys: PROD, STAGING
  - Quotas: confirm available throughput; understand waitlist/usage caps.
  - Notes: Routed when Runway throttles/errors.

- Kling (Fallback)
  - Keys: PROD, STAGING
  - Quotas: confirm p95 latency and TPS; cost per minute.
  - Notes: Alternate fallback path; feature-flag controllable.

- Stability (Storyboard Fallback)
  - Keys: PROD, STAGING
  - Quotas: ensure sufficient for storyboard volume.
  - Notes: Used for storyboard/image-to-video fallback when video APIs throttle.

---

## Audio/Voice (Future)
- ElevenLabs or equivalent
  - Keys: TBD; keep in vault.
  - Quotas: none needed for Alpha/Beta unless voice shipped.

---

## Moderation/Safety
- Moderation provider (LLM-based + NSFW classifier)
  - Keys: PROD, STAGING
  - Quotas: sized for all prompts/outputs; add retry budget.
  - Notes: Required for prompt moderation + output filter.

---

## Data/Storage
- Vector DB (e.g., Pinecone/pgvector/Weaviate)
  - Keys/creds: PROD, STAGING
  - Quotas: dimension 512; expected QPS from continuity queries.
  - Notes: Used for character embeddings; ensure multi-AZ or replica.

- S3 + CDN
  - Keys: PROD, STAGING
  - Quotas: media storage; ensure bucket policies; CDN configured.

- Redis (L1 cache)
  - Access: connection strings
  - Quotas: memory reservations; max clients.

---

## Auth/Billing
- Stripe
  - Keys: Test/Live
  - Notes: Keep test mode for Alpha/Beta; promos flagged; webhooks configured.

---

## Actions to Complete
- Store all keys in vault/SSM; never in code.
- Document per-env endpoints and rate limits.
- Set alerts on throttle/429/error rates for Runway/Sora/Kling/Stability and Moderation.
- Pre-flight token/credential validity before Sprint 1 kickoff.
