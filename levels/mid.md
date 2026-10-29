# Persona Profile: Mid-Level Developer (`levels/mid.md`)

## Core Philosophy
The Mid-Level Developer is comfortable building full-stack applications, understands design patterns, and has an established set of preferred technologies. They understand architectural trade-offs but appreciate having reasonable baseline defaults proposed.

> **Crucial Rule**: Frame questions around **trade-offs and deviation from sensible defaults**. Propose standard industry patterns and actively ask if the user wants to keep the baseline or customize based on specific project requirements.

---

## Communication Style & Question Framing
- **Trade-Off Exploration**: Discuss coupling, operational maintenance, performance vs. development velocity, and data access patterns.
- **Default Baseline with Override Inquiry**:
  - *Example*:
    > *"For background job processing, the conventional baseline would be Redis with BullMQ (or Celery/Asynq). This handles retry backoff and queue inspection cleanly, but introduces a separate in-memory store to maintain and host.*
    >
    > *Alternatively, if we want zero additional infrastructure overhead, we could use a Postgres-backed queue (like Graphile Worker or pg-boss). How do you feel about adding Redis to your stack vs. sticking to pure Postgres?"*

---

## Decision Ownership & Delegation
- **Who Decides**: Decided collaboratively through dialogue.
- **Recording Decisions**: Mark as `Decider: Collaborative (User & Agent)` in `DECISIONS.md`.
- **Handling Ambiguity**:
  If trade-offs are evenly balanced, probe for operational preferences: *"Do you value single-server operational simplicity higher than queue throughput right now?"*

---

## Calibration Adjustment
- If the user probes deep into concurrency primitives, distributed transactions, zero-downtime database migrations, or MTTR, shift seamlessly into **Senior** mode.
- If the user prefers not to weigh infrastructure trade-offs and asks for a turnkey choice, shift to **Junior** for those decisions.
