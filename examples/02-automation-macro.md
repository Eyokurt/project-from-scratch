<!-- DO NOT COPY VERBATIM - REFERENCE FOR DIVERSE MENTAL MODELS ONLY -->
# Reference Example 2: Financial Reconciliation Macro ("LedgerSync")

> **Domain**: Desktop Automation / CLI Tool (Python / Windows OS)  
> **Persona Level**: Vibe-Coder (Accountant with basic scripting familiarity, values immediate utility over code architecture)  
> **Notice**: Demonstrates how technical decisions (browser drivers, retry queues) are delegated to the agent while asking the user only about business outcomes and safety kill switches.

---

## 1. Vision & Core Problem
- **1-Sentence Definition**: A background Windows utility that monitors a dedicated inbox folder for vendor invoice PDFs, extracts table line-items via local parser, checks them against bank statements, and drafts matching ERP journal entries for human 1-click review.
- **The Core Problem**: The user spends 14 hours every Friday manually cross-checking invoice line items against a legacy banking portal with no public API.
- **Distinguishing Facets**:
  1. *Zero Cloud Uploads*: Financial PDFs never leave the local machine (client confidentiality).
  2. *Physical Emergency Stop*: Global hotkey (`Ctrl + Shift + Esc + K`) halts all automated keystrokes instantly.
  3. *Uncertainty Isolation*: Any confidence score below 98% is tagged yellow in Excel for human verification instead of auto-committing.

---

## 2. In-Scope vs. Non-Goals
- **In-Scope (MVP)**:
  - Local parsing of standard PDF invoices (text-based; non-scanned).
  - Browser automation script logging into the bank portal using existing desktop session cookies.
  - CSV exception report generated in `C:\LedgerSync\Reports` with clear error reasons.
- **Explicit Non-Goals**:
  - ❌ No automated submission button click on bank portal (human must click "Submit Transfer").
  - ❌ No OCR processing on low-resolution scanned image receipts (too error-prone for Phase 1).
  - ❌ No multi-user login or SaaS multi-tenant infrastructure.

---

## 3. Blast Radius & Worst-Case Failure
- **Worst-Case**: Script sending erroneous payment amounts or getting banking account frozen due to rapid request rate.
- **Mitigation Architecture**: Read-only extraction on bank side; writes only to a local draft spreadsheet. Jittered humanized mouse movements (200–800ms delays). Emergency kill switch terminates process tree immediately.

---

## 4. Definition of Done
1. Successfully parses a batch of 50 sample vendor invoices in under 4 minutes.
2. Accurately highlights all mismatched amounts in the output report.
3. Emergency hotkey aborts execution within 100 milliseconds when tested.
