# Project Specification: {{PROJECT_NAME}}

> **Document Status**: `[DRAFT / SOLIDIFIED]`  
> **Initial Idea Date**: {{DATE}}  
> **User Profile**: `[{{USER_LEVEL}}]` (Calibrated: {{CALIBRATION_NOTES}})  
> **Domain Archetype**: `[{{DOMAIN_ARCHETYPE}}]` (e.g., Game, Server Tool, Macro, Web Platform, IoT)

---

## 1. Vision & Core Problem
### 1.1 Executive Summary
- **1-Sentence Definition**: {{ONE_SENTENCE_DEFINITION}}
- **The Core Problem**: What real-world friction, deficit, or desire does this solve?
- **Why Existing Solutions Fall Short**: What makes current alternatives unacceptable or inadequate for this specific context?

### 1.2 The Distinguishing Facets
What 2–3 unfamiliar, unique, or non-standard qualities separate this project from conventional templates?
1. **{{FACET_1_NAME}}**: {{FACET_1_DESCRIPTION}}
2. **{{FACET_2_NAME}}**: {{FACET_2_DESCRIPTION}}
3. **{{FACET_3_NAME}}**: {{FACET_3_DESCRIPTION}}

---

## 2. Target Audience & Personas
- **Primary Beneficiary**: Exact user persona, technical background, and operational context.
- **Trigger Scenario**: What specific situation or frustration drives them to use this system?
- **Secondary Stakeholders**: (If applicable) Admins, operators, or downstream consumers.

---

## 3. Scope & Non-Goals (Hard Boundaries)
### 3.1 In-Scope (Phase 1 / MVP)
- [ ] **{{FEATURE_OR_CAPABILITY_1}}**: Concrete observable capability.
- [ ] **{{FEATURE_OR_CAPABILITY_2}}**: Concrete observable capability.
- [ ] **{{FEATURE_OR_CAPABILITY_3}}**: Concrete observable capability.

### 3.2 Explicit Non-Goals (What Will NOT Be Built)
*Drawing a strict boundary to prevent feature creep and distraction.*
- [-] **{{NON_GOAL_1}}**: Explicitly out of scope and reason why.
- [-] **{{NON_GOAL_2}}**: Explicitly out of scope and reason why.
- [-] **{{NON_GOAL_3}}**: Explicitly out of scope and reason why.

---

## 4. Operational & Environmental Constraints
- **Timeframe & Velocity**: Target milestone for Phase 1.
- **Budget & Hosting Economics**: Acceptable infrastructure spend ($0, $10/mo, corporate budget).
- **Target Platforms & Runtime Environment**: Supported OS, hardware minimums, runtime dependencies.
- **Team & Skill Constraints**: Solo developer vs. multi-person team; primary maintainer skills.

---

## 5. Blast Radius & Reliability Model
- **Failure Impact**: If this system crashes, freezes, or corrupts data, what is the exact consequence?
- **Worst-Case Scenario**: Financial loss, account suspension, data corruption, user frustration?
- **Fail-Safe Mechanism**: How does the system degrade gracefully or alert the user upon failure?

---

## 6. Dynamic Domain Modules (Project-Specific)

<!-- 
NOTE FOR AGENT: Dynamically generate 1-3 modules matching the project archetype.
Delete unneeded modules below and populate the relevant ones.
-->

### [Archetype: Game] Core Loop & Game Feel
- **Core Loop**: Minute-to-minute interaction loop (e.g., Action -> Reward -> Upgrade -> Repeat).
- **Game Feel & Input Handling**: Deterministic physics, responsiveness, input buffer, frame rate target.
- **Save State & Progression**: Checkpoint vs. persistent save files, offline compatibility.

### [Archetype: Automation / Macro] Target System Interaction & Kill Switch
- **Target Surface**: DOM, private API, desktop GUI automation, accessibility tree.
- **Emergency Kill Switch**: Hardware hotkey or trigger to instantly kill execution.
- **Anti-Ban & Throttling**: Random jitter, rate limiting, session refresh.

### [Archetype: Server Control Panel / DevOps] RBAC & Disaster Recovery
- **Permission & Role Hierarchy**: Who can trigger destructive actions?
- **Audit Logging**: Structured log trail for state mutations.
- **Rollback & State Recovery**: 1-click restore or rollback mechanism.

### [Archetype: Social / Community] Abuse Defense & UGC
- **Content Moderation**: Automated filters, reporting queue, spam prevention.
- **Data Privacy & Ephemerality**: Expiration of messages, data export, account deletion.

### [Archetype: Embedded / Hardware] Power & Hardware Interface
- **Power Budget**: Battery consumption, sleep intervals.
- **Connectivity Resilience**: Offline store-and-forward caching.
- **Firmware Lifecycle**: Failsafe OTA updates with fallback.

---

## 7. Definition of Done (Observable Acceptance Gates)
Phase 1 is officially "DONE" when the following observable criteria are met:
- [ ] **Gate 1 (Core Workflow)**: {{GATE_1_CRITERIA}}
- [ ] **Gate 2 (Reliability / Edge Case)**: {{GATE_2_CRITERIA}}
- [ ] **Gate 3 (Operational Delivery)**: {{GATE_3_CRITERIA}}

---

## 8. Risks, Assumptions & Open Questions
### 8.1 Critical Assumptions (Tagged for Review)
*Decisions or premises accepted without definitive empirical proof.*
- `[ASSUMED / REVIEW_REQUIRED]` **{{ASSUMPTION_1}}**: {{ASSUMPTION_1_DETAILS}} (Rationale: {{ASSUMPTION_1_RATIONALE}})

### 8.2 Pre-Mortem Findings (Identified Fatal Risks)
*"Suppose this project failed 6 months after release: why did it die?"*
1. **Fatal Risk 1**: {{FATAL_RISK_1}}  
   *Mitigation / Architectural Defense*: {{FATAL_RISK_1_DEFENSE}}
2. **Fatal Risk 2**: {{FATAL_RISK_2}}  
   *Mitigation / Architectural Defense*: {{FATAL_RISK_2_DEFENSE}}

### 8.3 Remaining Open Questions (If Concluded Early)
- `[OPEN]` **{{QUESTION_1}}**: Impact if unresolved.
