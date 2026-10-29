# Discovery Interview State Tracker: {{PROJECT_NAME}}

> **Session State**: This living tracker persists the current state of the interview. If the conversation is interrupted, paused, or transferred, the agent resumes seamlessly from this file.

---

## 1. Session Metadata
- **Project Name**: {{PROJECT_NAME}}
- **Current Lifecycle Stage**: `Stage [1-8]: {{STAGE_NAME}}`
- **User Declared Level**: `[Vibe-coder / Junior / Mid / Senior]`
- **Calibrated Level**: `[{{CALIBRATED_LEVEL}}]` (Calibration notes: {{CALIBRATION_NOTES}})
- **Total Interaction Turns**: `{{TURN_COUNT}}` (Checkpoint triggered every 15 turns)
- **Saturation Counter**: `{{SATURATION_ROUNDS_COUNT}}/2` (Consecutive rounds without new decisions or contradictions)

---

## 2. Dimension Solidification Status

| Dimension | Status | Summary of Current Understanding |
| :--- | :---: | :--- |
| **1. Target Audience & Problem** | `[EMPTY / PARTIAL / ASSUMED / SOLIDIFIED]` | {{SUMMARY_OR_GAP}} |
| **2. Non-Goals & Boundaries** | `[EMPTY / PARTIAL / ASSUMED / SOLIDIFIED]` | {{SUMMARY_OR_GAP}} |
| **3. Operational Constraints** | `[EMPTY / PARTIAL / ASSUMED / SOLIDIFIED]` | {{SUMMARY_OR_GAP}} |
| **4. Blast Radius & Reliability** | `[EMPTY / PARTIAL / ASSUMED / SOLIDIFIED]` | {{SUMMARY_OR_GAP}} |
| **5. Definition of Done** | `[EMPTY / PARTIAL / ASSUMED / SOLIDIFIED]` | {{SUMMARY_OR_GAP}} |
| **6. Known Unknowns** | `[EMPTY / PARTIAL / ASSUMED / SOLIDIFIED]` | {{SUMMARY_OR_GAP}} |

---

## 3. Prioritized Gap Queue (Decision Tree Logic)
*Sorted by Reversibility Cost: Items with high cost of reversal must be inquired first.*

1. **[CRITICAL - HIGH COST]**: {{HIGH_COST_GAP_TOPIC}} -> Status: `[OPEN / IN_PROGRESS / RESOLVED]`
2. **[SIGNIFICANT - MEDIUM COST]**: {{MEDIUM_COST_GAP_TOPIC}} -> Status: `[OPEN / IN_PROGRESS / RESOLVED]`
3. **[TACTICAL - LOW COST]**: {{LOW_COST_GAP_TOPIC}} -> Status: `[OPEN / IN_PROGRESS / RESOLVED]`

---

## 4. User Fatigue & Engagement Monitor
- **Consecutive Monosyllabic / Minimal Answers**: `{{COUNT}}`
- **Repeated "I Don't Know / Whatever" Answers**: `{{COUNT}}`
- **Fatigue Action Threshold Reached?**: `[YES / NO]`  
  *(If YES: Cease deep probing immediately. Propose sensible defaults, record as [ASSUMED], and move to document closure).*

---

## 5. Next Immediate Inquiries (Derived from Top Gaps)
- **Primary Gap to Address**: {{PRIMARY_GAP}}
- **Formulated Question (Adapted to User Level)**: {{FORMULATED_QUESTION}}
