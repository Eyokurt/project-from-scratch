# The 6 Fixed Architectural Dimensions (`dimensions.md`)

> **Core Principle**: These 6 dimensions are **not a canned questionnaire**. They represent an immutable **scope checklist**. The agent must never recite these verbatim to the user; instead, the agent tracks which dimensions have been thoroughly populated and derives natural, context-specific questions based on the gaps.

Every project—whether a retro video game, a high-frequency automation macro, a Kubernetes control plane, a niche social platform, or a microcontroller firmware project—must have clear answers to these six dimensions before the discovery phase can be closed.

---

## Dimension Breakdown & Cross-Domain Mapping

| Dimension | Fundamental Question | Invariant Goal | Domain Adaptation Example |
| :--- | :--- | :--- | :--- |
| **1. Target Audience & Core Problem** *(Kimin için, hangi problem?)* | Who is the primary beneficiary, and what specific friction, deficit, or desire triggers their usage? | Eliminate vague "for everybody" delusions. Define the exact persona and operational trigger. | **Game**: "Speedrunners wanting deterministic physics and instant restarts."<br>**Macro**: "Accountants spending 4 hours daily copying PDF tables into SAP."<br>**Server Panel**: "Solo founders managing 5–20 Docker containers without learning full K8s." |
| **2. Non-Goals & Strict Boundaries** *(Ne olmayacak?)* | What will this project explicitly **NOT** attempt to do, support, or solve in Phase 1? | Prevent feature creep and premature abstraction. Draw a hard fence around MVP scope. | **Game**: "No multiplayer, no procedural level generation, no character customization."<br>**Macro**: "No web-based dashboard, no cross-platform Linux support, no OCR on distorted scans."<br>**Server Panel**: "No multi-cloud auto-failover, no custom billing or tenant invoicing." |
| **3. Operational Constraints** *(Kısıtlar)* | What non-negotiable boundaries exist around time, budget, platform, compute, and skill? | Anchor the architecture in hard reality rather than theoretical ideals. | **Game**: "Must run smoothly on low-end laptops (Intel UHD 620), solo dev, release in 3 months."<br>**Macro**: "Windows 11 only, must run without admin privileges, zero recurring cloud costs."<br>**Server Panel**: "Self-hostable on a \$5/mo VPS, single binary deployment, minimal RAM footprint (<100MB)." |
| **4. Blast Radius & Failure Impact** *(Ne bozulursa kime ne zarar verir?)* | If this system crashes, corrupts data, hangs, or executes incorrectly, what is the worst consequence? | Uncover implicit reliability, security, and backup requirements. | **Game**: "Lost 45-minute save file, rage quit, negative Steam review."<br>**Macro**: "Target portal bans user account for botting, or wrong invoice values sent to tax office."<br>**Server Panel**: "Accidental deletion of production database volume; user service downtime." |
| **5. Definition of Done** *(“Bitti” neye benziyor?)* | What concrete, observable milestones prove that Phase 1 / MVP is fully accomplished? | Replace subjective "when it feels good" with measurable completion criteria. | **Game**: "Playable 3-level vertical slice with save/load, settings menu, and 60fps locked."<br>**Macro**: "Successfully processes a 500-row batch with 0 exceptions and writes audit log in under 3 minutes."<br>**Server Panel**: "User can spin up, stop, restart, inspect logs, and rollback a containerized app via web UI." |
| **6. Known Unknowns & Critical Assumptions** *(Neyi bilmiyoruz?)* | What dependencies, third-party limitations, or unproven assumptions are we relying upon? | Never leave unstated assumptions to chance. Document every unknown with a review trigger. | **Game**: "Will Godot 4 HTML5 export have audio stutter on Safari iOS?"<br>**Macro**: "Does the target website change its DOM class names weekly to deter scraping?"<br>**Server Panel**: "Can we reliably stream Docker socket stdout over secure WebSockets on low-bandwidth links?" |

---

## Dimension Health Matrix (Evaluation Rubric)

During each round of the interview, evaluate the completeness of each dimension in `INTERVIEW_STATE.md`:

```
[ ] EMPTY       : No verified information. Must formulate discovery inquiry.
[-] PARTIAL     : Surface-level idea mentioned, but lacking boundaries, edge cases, or specifics.
[?] ASSUMED     : Filled by agent recommendation or user "don't know / you decide" with [Gözden Geçir] flag.
[X] SOLIDIFIED  : Concrete, validated by user, consistent with other architectural constraints.
```

### Transition Rule
The interview **cannot conclude** if any of the 6 dimensions remains `[ ] EMPTY`. Every dimension must be promoted to either `[X] SOLIDIFIED` or `[?] ASSUMED` (with explicit rationale documented in `DECISIONS.md`).
