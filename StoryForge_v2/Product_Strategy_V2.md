# Product Strategy (V2)
## Core Thesis
The moat is the workflow and narrative layer above commoditizing video models, not model R&D. StoryForge wins by giving creators a fast, structured way to produce serialized AI video with consistent characters, coherent beats, and repeatable styles.

## Problem & Target User
- User: Short-form serial storytellers (TikTok/YouTube Shorts creators) who publish episodic content weekly.
- Pain: Character and continuity drift across scenes/episodes, lack of narrative scaffolding, and fragmented tooling that slows output.
- Evidence: Runway Gen-4 already charges for consistency (paid-only), creators complain publicly about drift, and 10+ explicit beta commitments is the validation bar.

## Value Proposition
“Ship a consistent, multi-scene AI video series in hours, not days — with guardrails for story beats, style, and continuity.”

## Differentiation
- **Workflow layer first:** Lean on Runway/Pika for generation; StoryForge owns prompts, references, timeline, and iteration loops.
- **Format templates:** Lightweight beat scaffolds for episodic TikTok/Shorts; unlocks speed and reduces blank-page risk.
- **Continuity dashboard:** Single place to manage references, locked shots, and scene order.
- **Data flywheel:** Usage data on prompts/styles/templates informs future ML-based Brains once PMF is proven.

## Positioning
- Near-term brand: **StoryClip** — a focused tool that locks characters and scenes for serial creators.
- Post-PMF brand: **StoryForge** — the fuller workflow platform (templates, style brains, collaboration) built after validation.

## Key Choices (Based on Red-Team & Validation Docs)
- Start with one template (TikTok Series) and a few style presets (prompt-engineered), not 8 Brains/5 Formats.
- Monolith + managed services (Vercel + Supabase); avoid microservices until >1K WAU.
- Success is measured in committed beta users, scenes generated, and conversion — not internal process completeness.
