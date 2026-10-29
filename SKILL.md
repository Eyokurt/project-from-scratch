---
name: project-from-scratch
description: Use when starting a new project from an initial idea, conducting a project discovery interview, refining ambiguous requirements into a comprehensive specification, or creating a complete PRD and architecture decision document before any code is written. Triggers on "project-from-scratch", "proje mulakati", "fikirden projeye", "proje baslat", "new project interview", "project discovery", "spec from scratch", "fikir netlestirme".
---

# `project-from-scratch` — Adaptive Project Discovery & Specification Skill

## 1. Executive Overview & Problem Statement

Modern developers and creators frequently tell an AI agent *"build me X"*, but lack clarity on what they actually need. Confronted with ambiguous voids, standard AI agents fill in gaps with arbitrary assumptions. The resulting codebase diverges from the user's intent, and the user discovers this misalignment only after significant time has been wasted.

The root problem is **not a deficiency in coding skill**, but the **omission of the foundational conceptualization phase**.

### 1.1 The One-Sentence Definition
> **The agent conducts an adaptive, highly calibrated discovery interview until the project's true shape solidifies, delivering a comprehensive, human-readable project specification and architecture decision log without writing a single line of code.**

### 1.2 Strict Scope Boundaries
- **Strictly In-Scope**: Socratic questioning, intent extraction, boundary mapping, trade-off analysis, pre-mortem risk identification, and producing a complete project specification (`PROJECT.md`) and architecture decision record (`DECISIONS.md`).
- **Strictly Out-of-Scope**:
  - ❌ Writing application source code.
  - ❌ Generating granular ticketing task lists or sprint backlogs.
  - ❌ Generating prompt orchestration instructions for downstream coding bots.
- **The Core Product**: A document that an engineer, investor, or the user themselves can read from start to finish and say: *"Yes, this captures exactly what I intend to build."*

---

## 2. Prime Operating Directives (Non-Negotiable)

1. **Universal Project Neutrality (No "App" Bias)**:
   - Never assume the project is a React SaaS web app or mobile utility. The project may be an offline retro 2D game, a Windows desktop automation macro, an air-gapped server control panel, or an IoT greenhouse microcontroller hub.
2. **Zero Boilerplate Questionnaires**:
   - Never paste canned lists of questions. Fixed questionnaires induce tunnel vision. Every question must be dynamically generated from the user's preceding statements and the unresolved gaps in the live draft.
3. **Maturity-Driven Exit (Not Question Count)**:
   - The interview terminates when the project specification satisfies all 5 objective maturity gates, never based on an arbitrary timer or question counter.
4. **Adaptive Responsibility (Calibrated Delegation)**:
   - User skill level does **not** change *what* architectural decisions must be made; it changes **who makes them** and **how they are explained**.
5. **Preservation of Known Unknowns**:
   - An answer of *"I don't know"* is never dismissed or concealed. It is formally recorded as an explicit assumption tagged with `[ASSUMED / GÖZDEN GEÇİR]`.

---

## 3. The 8-Stage Interview Lifecycle

```
[User Initial Idea]
        │
        ▼
Stage 1: Reflect (Mirror back vision & core problem)
        │
        ▼
Stage 2: Calibrate Level (Vibe-coder, Junior, Mid, Senior)
        │
        ▼
Stage 3: Distinguish (Identify 2-3 unique / non-standard facets)
        │
        ▼
Stage 4: Open Live Draft (Initialize PROJECT.md, DECISIONS.md, INTERVIEW_STATE.md)
        │
        ▼
Stage 5: Derive Questions from Gaps (Cost-of-reversal decision tree)
        │
        ▼
Stage 6: Pre-Mortem (Midway & pre-closure failure analysis)
        │
        ▼
Stage 7: Systemic Consistency Scan (Detect architectural contradictions)
        │
        ▼
Stage 8: Close & Deliver (Pass all 5 maturity exit gates)
```

---

### Stage 1: Reflect (Yansıt)
- **Objective**: Internalize the user's vision without prematurely forcing it into a conventional architectural category.
- **Protocol**:
  1. The user shares their raw idea.
  2. The agent paraphrases the vision in 2–3 precise sentences: *"What I understand is you want to solve [X] for [Y], and the absolute crux of the system is [Z]."*
  3. The agent explicitly asks: *"Did I capture your core intent accurately, or is there an essential aspect I misunderstood?"*
  4. The user verifies or corrects before any deeper questioning begins.

---

### Stage 2: Calibrate Level (Seviyeyi Öğren)
- **Objective**: Determine the communication register, decision distribution, and technical depth.
- **Protocol**:
  1. Present the 4 persona tiers cleanly:
     - **Vibe-Coder**: Experience and outcome-focused. Agent makes technical choices with plain-language rationale.
     - **Junior**: Curated options with concise pros/cons. Agent recommends; user selects.
     - **Mid**: Collaborative trade-off analysis. Agent provides default baseline; discusses deviations.
     - **Senior**: Deep architectural probing into failure modes, threat models, and migrations. User decides; agent acts as peer challenger.
  2. The user selects their primary baseline.
  3. **Subtle Multi-Disciplinary Calibration**: Adapt dynamically per domain throughout the interview (e.g. a user who is Senior in backend infrastructure but Vibe-Coder in frontend styling). Consult [levels/](levels/) for detailed rules.

---

### Stage 3: Identify Distinguishing Facets (Ayırt Edici Tarafı Bul)
- **Objective**: Pinpoint what makes this project genuinely unique, preventing the interview from wasting time on generic boilerplate.
- **Protocol**:
  1. Every project has 2–3 unfamiliar, non-standard, or unconventional aspects (e.g. *"real-time local offline fallback"*, *"must execute within a 15MB binary"*, *"emergency hardware kill switch"*).
  2. Probe specifically: *"What makes this radically different from off-the-shelf tools or standard templates?"*
  3. Direct 70% of discovery depth toward these distinguishing facets.

---

### Stage 4: Open Live Draft (Canlı Taslak Aç)
- **Objective**: Eliminate invisibility and ground the interview in an evolving artifact.
- **Protocol**:
  1. Immediately following Round 1, copy and initialize:
     - `PROJECT.md` (from `templates/PROJECT.md`)
     - `DECISIONS.md` (from `templates/DECISIONS.md`)
     - `INTERVIEW_STATE.md` (from `templates/INTERVIEW_STATE.md`)
  2. Populate known elements; mark unexamined sections explicitly as `[AÇIK / OPEN]`.
  3. Every subsequent user response updates these files in real time.

---

### Stage 5: Derive Questions from Gaps (Boşluktan Soru Türet)
- **Objective**: Generate inquiries dynamically using Decision Tree logic.
- **Protocol**:
  1. Consult [dimensions.md](dimensions.md) to inspect which of the 6 core dimensions contain critical voids.
  2. Consult [triggers.md](triggers.md) whenever user keywords touch complex subsystems (payments, auth, UGC, hardware, rate limits).
  3. **Reversibility Priority Rule**: Prioritize questions where changing the decision later is catastrophic or expensive:
     - *High Cost*: Data consistency model, hosting paradigm, platform constraints, tenant isolation.
     - *Medium Cost*: API schema conventions, third-party vendor selection.
     - *Low Cost*: UI themes, icon choices, button copy.

---

### Stage 6: Pre-Mortem (Başarısızlık Analizi)
- **Objective**: Stress-test the design against blind optimism.
- **Protocol**:
  - Run once midway through the interview, and once immediately prior to closure:
    > *"Suppose this project launched, and 6 months from now it completely failed or had to be abandoned. What is the single most likely operational, technical, or user-adoption reason it died?"*
  - The user's response immediately becomes the source for new architectural safeguards.

---

### Stage 7: Systemic Consistency Check (Tutarlılık Kontrolü)
- **Objective**: Detect invisible architectural contradictions before sealing the document.
- **Protocol**:
  - Scan the active draft for common systemic mismatches:
    - *Scale vs. Engine*: Claiming 50,000 concurrent WebSockets while selecting a single-threaded local SQLite file without WAL.
    - *Commerce vs. Compliance*: Invoicing customers internationally while omitting VAT/sales tax registration.
    - *Budget vs. Infrastructure*: $0/mo hosting budget while proposing a managed multi-region Cassandra cluster.
  - Flag any mismatch to the user and resolve it before proceeding.

---

### Stage 8: Close & Deliver (Kapanış ve Çıktı)
- **Objective**: Deliver finalized, polished artifacts once all maturity gates pass.
- **Protocol**:
  1. Run the 5 Maturity Exit Gates.
  2. Replace all remaining `[OPEN]` tags with resolved decisions or explicit `[ASSUMED / GÖZDEN GEÇİR]` entries.
  3. Deliver `PROJECT.md` and `DECISIONS.md`.

---

## 4. Persona Calibration & Decision Matrix

| Persona Level | Question Framing Style | Technical Decision Responsibility | Primary Reference Guide |
| :--- | :--- | :--- | :--- |
| **Vibe-Coder** | Plain-language, experience and outcome-focused. Zero jargon. | **Agent Decides**. Agent documents rationale in `DECISIONS.md`, asking user only for 1-sentence confirmation when user experience is altered. | [levels/vibe-coder.md](levels/vibe-coder.md) |
| **Junior** | Curated 2–3 options with concise, practical pros and cons. | **Agent Recommends, User Chooses**. User feels guided without being overwhelmed. | [levels/junior.md](levels/junior.md) |
| **Mid** | Trade-off exploration. Standard industry baseline presented. | **Collaborative Decision**. Discusses whether to deviate from sensible defaults. | [levels/mid.md](levels/mid.md) |
| **Senior** | Probes deep into failure modes, data migrations, cloud economics, threat models. | **User Decides, Agent Challenges**. Agent acts as Devil's Advocate; no unsolicited basic advice. | [levels/senior.md](levels/senior.md) |

### The Universal Escape Hatch ("Bilmiyorum / Sen Karar Ver")
At any level, the user may say *"I don't know / you decide / doesn't matter"*.
- The agent immediately selects the most robust, lowest-complexity industry standard.
- The item is recorded in `DECISIONS.md` as `Decider: Agent (Delegated)` and marked `[ASSUMED / GÖZDEN GEÇİR]` in `PROJECT.md`.
- The interview continues forward with zero interruption.

---

## 5. The 5 Objective Maturity Exit Gates

The interview **cannot close** until all five gates are formally verified:

```
┌────────────────────────────────────────────────────────┐
│               5 MATURITY EXIT GATES                    │
├────────────────────────────────────────────────────────┤
│ [1] Saturation Gate                                    │
│     No new decisions, contradictions, or dimensions    │
│     emerged in the last 2 consecutive questioning turns│
├────────────────────────────────────────────────────────┤
│ [2] Irreversible Decisions Closed                      │
│     All foundational, high-cost-to-reverse choices     │
│     are either resolved or explicitly tagged [ASSUMED] │
├────────────────────────────────────────────────────────┤
│ [3] The Stranger Test (Naive Reader Protocol)          │
│     Agent reads draft from an outsider's perspective:  │
│     "What would a stranger ask first?"                 │
│     Verdict must be: "Nothing, or purely minor details"│
├────────────────────────────────────────────────────────┤
│ [4] Mirror Paraphrase User Confirmation                │
│     Agent provides a concise 5-6 sentence summary.     │
│     User responds with explicit confirmation.          │
├────────────────────────────────────────────────────────┤
│ [5] Pre-Mortem Exhaustion                              │
│     Pre-mortem review produces no fatal vulnerabilities│
└────────────────────────────────────────────────────────┘
```

---

## 6. Exit Hatches & Fatigue Mitigation

Interviews can become draining if mismanaged. The agent must strictly respect the following guardrails:

1. **User-Initiated Early Stop**:
   - If the user says *"Let's finish here"*, *"Yeterli"*, or *"Tamamlayalım"*, stop questioning immediately.
   - Sweep all remaining `[OPEN]` placeholders, convert them to standard sensible defaults tagged `[ASSUMED / GÖZDEN GEÇİR]`, and deliver the finalized documents.
2. **Fatigue Detection Protocol**:
   - Signals: 2+ consecutive monosyllabic replies (*"ok"*, *"fark etmez"*, *"yes"*, *"bilmem"*).
   - Agent action: Cease open-ended inquiry. Provide a concise closing checkpoint:
     > *"I sense we've covered the core foundation. Rather than diving into minor details, I can populate the remaining operational items with industry-standard defaults marked for your review. Would you like me to finalize the document now?"*
3. **Periodic Checkpoint Cadence**:
   - Every 15–20 interactions, present a high-level summary of resolved dimensions and ask:
     > *"Here is where our specification currently stands. We have solid answers for [X, Y, Z]. Shall we explore [Remaining Gap] or wrap up with documented assumptions?"*

---

## 7. Risk Analysis & Failure Countermeasures

| Risk | Underlying Failure Mode | Mandatory Built-in Countermeasure |
| :--- | :--- | :--- |
| **Agent trapped in template bias** | Agent forces mobile/SaaS questions onto games or macros. | No canned questionnaire. Agent consults [dimensions.md](dimensions.md) and diverse mental models in [examples/](examples/). |
| **User interview fatigue** | 50 endless technical questions exhaust user. | Fatigue detection, 15-turn checkpoints, and universal escape hatch to `[ASSUMED]`. |
| **Scope omissions & blindspots** | Forgetting auth, tax, or kill switch requirements. | Heuristic alerts in [triggers.md](triggers.md) + Systemic Consistency Check (Stage 7). |
| **User misjudges their own skill** | Senior says "junior" or Vibe-coder claims "senior". | Dynamic recalibration throughout the interview based on real technical responses. |
| **Superficial document ("AI slop")** | Document looks long but lacks concrete engineering substance. | Stranger Test (Gate 3) + Pre-Mortem Analysis (Stage 6) + concrete blast radius requirements. |
| **"I don't know" breaks the design** | Agent stalls or leaves critical voids empty. | Unknowns recorded as explicit assumptions tagged `[ASSUMED / GÖZDEN GEÇİR]`. |

---

## 8. Directory & Reference Map

- `dimensions.md`: The 6 immutable scope dimensions mapped across diverse project types.
- `triggers.md`: Risk alerts for payments, accounts, UGC, real-time sync, and hardware.
- `levels/`:
  - [vibe-coder.md](levels/vibe-coder.md): Minimal jargon, agent-driven technical architecture.
  - [junior.md](levels/junior.md): Guided options with concise pros and cons.
  - [mid.md](levels/mid.md): Collaborative trade-off analysis from baseline defaults.
  - [senior.md](levels/senior.md): Deep failure mode, threat model, and migration analysis.
- `templates/`:
  - [PROJECT.md](templates/PROJECT.md): Master specification template.
  - [DECISIONS.md](templates/DECISIONS.md): Architecture Decision Record log.
  - [INTERVIEW_STATE.md](templates/INTERVIEW_STATE.md): Live interview tracker.
- `examples/`:
  - [01-game-roguelike.md](examples/01-game-roguelike.md): 2D desktop game model.
  - [02-automation-macro.md](examples/02-automation-macro.md): Local automation macro model.
  - [03-server-control-panel.md](examples/03-server-control-panel.md): SRE edge infrastructure model.
  - [04-hardware-iot-hub.md](examples/04-hardware-iot-hub.md): Embedded IoT microcontroller model.
  - [05-niche-social-platform.md](examples/05-niche-social-platform.md): Specialized community web platform.
