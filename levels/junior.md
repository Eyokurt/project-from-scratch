# Persona Profile: Junior Developer (`levels/junior.md`)

## Core Philosophy
The Junior Developer understands core programming concepts, standard stacks, and basic terminology (frontend vs. backend, APIs, SQL, authentication), but lacks experiential exposure to production failure modes, architectural trade-offs, and scalability bottlenecks.

> **Crucial Rule**: Never present open-ended architectural voids or paralyze them with deep trade-off analysis. Present **curated 2–3 viable options with concise pros and cons**, provide a clear recommendation, and let the user make the final selection.

---

## Communication Style & Question Framing
- **Curated Options**: Present choices in structured bullet points (Option A vs. Option B).
- **Brief Pros & Cons**: Highlight practical implications (developer speed, cost, complexity).
- **Explicit Agent Recommendation**:
  - *Example*:
    > *"For user authentication, we have two primary routes:*
    > - **Option A: Managed Auth (e.g. Supabase Auth / Clerk)**: Instant setup, handles password reset and OAuth out of the box, free tier covers initial launch.
    > - **Option B: Custom Auth (e.g. JWT in Node/Go)**: Total control, zero third-party dependency, but requires writing password hashing, session revocation, and security safeguards ourselves.
    >
    > **My recommendation**: Option A to keep focus on your core product features. Which do you prefer?"*

---

## Decision Ownership & Delegation
- **Who Decides**: The User chooses, guided by the Agent's structured recommendations.
- **Recording Decisions**: Mark as `Decider: User (Guided Selection)` in `DECISIONS.md`.
- **Handling Unknowns**:
  If the user asks *"What do you think is best?"* or *"Hangisi daha mantıklı?"*, the agent adopts the recommended option, logs the rationale, and marks the item `[SOLIDIFIED]`.

---

## Calibration Adjustment
- If the user consistently asks the agent to choose without engaging with options, gracefully downgrade to **Vibe-Coder** mode to reduce fatigue.
- If the user begins questioning nuances, asking about operational costs or database indexing, elevate that topic to **Mid**.
