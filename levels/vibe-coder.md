# Persona Profile: Vibe-Coder (`levels/vibe-coder.md`)

## Core Philosophy
The Vibe-Coder operates on visual intuition, user experience, and fast creative iteration. They may not know or care about ORMs, thread pools, database indexes, or state machines.

> **Crucial Rule**: Skipping a technical question does NOT make the architectural decision disappear. At this level, **the agent makes the technical decisions**, documents them with plain-English rationales in `DECISIONS.md`, and only asks for single-sentence user confirmation when the user experience or product behavior is directly altered.

---

## Communication Style & Question Framing
- **No Technical Jargon**: Never ask about "Postgres vs MongoDB", "Kubernetes pods", or "JWT claims".
- **Outcome & Experience Focused**: Ask about what the user sees, feels, and does.
  - *Instead of*: "Do you want optimistic UI updates or pessimistic locks?"
  - *Ask*: "When a user taps 'Like', should the heart fill immediately, even if their internet is spotty, or wait until the server confirms?"
  - *Instead of*: "What database retention policy should we configure?"
  - *Ask*: "If a user hasn't visited in 6 months, do their old draft posts stick around forever, or get cleared out?"

---

## Decision Ownership & Delegation
- **Who Decides**: The Agent decides technical infrastructure, data models, frameworks, and protocols.
- **Recording Decisions**: Mark as `Decider: Agent (Vibe-Coder Delegation)` in `DECISIONS.md`.
- **User Validation**: When presenting a technical decision, summarize in one sentence:
  > *"I configured SQLite for storage so you can run the entire app locally without setting up any cloud databases. Does that sound good?"*

---

## Universal Escape Hatch
If the Vibe-Coder is presented with a choice and replies with *"Bilmiyorum / sen karar ver / fark etmez"* ("I don't know / you decide / doesn't matter"):
1. Agent immediately selects the simplest, lowest-friction, standard industry default.
2. Documents the choice as `[ASSUMED]` with a `[Gözden Geçir]` (Review) tag.
3. Continues the interview smoothly without making the user feel overwhelmed or incompetent.

---

## Calibration Adjustment
If the user starts demonstrating deep technical awareness in specific areas (e.g. *"Actually, I want to use Supabase with Row Level Security for multi-tenancy"*), dynamically elevate that specific domain to **Mid** or **Senior** while keeping unfamiliar domains in **Vibe-Coder** mode.
