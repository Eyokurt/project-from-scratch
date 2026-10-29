# Architectural Trigger Reminders (`triggers.md`)

> **Notice**: These are **NOT canned interview questions**. They are **heuristic risk alarms** for the agent. Whenever the user's project touches any of the domains below, the agent must check this list internally to ensure that the associated architectural risks, edge cases, and non-functional requirements are not forgotten.

---

## 1. User Authentication & Account Lifecycles
*Triggered when*: Users can sign up, log in, manage profiles, or have private data.
- **Session & Identity Strategy**: Will this support passwordless magic links, OAuth providers (Google, GitHub), or standard email/password?
- **Account Recovery**: What happens when a user forgets their credentials or loses their 2FA device?
- **Multi-Tenancy & Authorization**: Is data strictly isolated per user or per organization/team? Who can invite whom?
- **Guest / Anonymous State**: Can users interact with the product before authenticating? What happens to their temporary state upon signup?
- **Account Deletion (Right to be Forgotten)**: When an account is deleted, what happens to their logs, uploaded assets, or relational rows?

## 2. Payments, Billing & Commercial Transactions
*Triggered when*: Paid subscriptions, one-time checkout, credits, or digital commerce are mentioned.
- **Payment Provider Choice**: Stripe, Paddle, Lemon Squeezy, or app store in-app purchases (Apple/Google 30% cut)?
- **Tax & Statutory Compliance**: Merchant of Record (MoR) requirement for international VAT/GST.
- **Lifecycle Edge Cases**: Failed payments (dunning), card expiration, subscription upgrades/downgrades with proration.
- **Refund & Chargeback Policy**: Automated self-serve refunds vs. manual admin approval; dispute defense logging.
- **Audit Ledger**: Double-entry accounting for credits or virtual currencies; avoiding floating-point rounding bugs.

## 3. User-Generated Content (UGC) & Media Uploads
*Triggered when*: Users can upload images, videos, audio, PDF attachments, or publish rich text.
- **Storage & Ingestion**: Direct-to-S3/GCS presigned uploads vs. proxying through application server.
- **Payload Sanitization**: Virus/malware scanning, image dimension compression, metadata (EXIF/GPS) stripping.
- **Abuse & Moderation**: Reporting workflow, automated text/image screening, automated rate limits on uploads.
- **Storage Cost Inflation**: Orphaned file cleanup (user uploads a picture but abandons the form draft).
- **Copyright & DMCA**: Safe harbor compliance, terms of service indemnification.

## 4. Real-Time State & Synchronous Interaction
*Triggered when*: Live chat, collaborative editing, multiplayer gameplay, live notifications, or WebSockets are involved.
- **Connection Drops & Reconnects**: Client network drops in an elevator or tunnel—how does the client resynchronize state?
- **Conflict Resolution**: Two users edit or move the same entity simultaneously (CRDTs, OT, or Last-Write-Wins)?
- **Server Backpressure & Resource Leaks**: What happens if 5,000 clients hold open connections? Heartbeat ping/pong intervals.
- **Message Ordering & Idempotency**: Can messages arrive out of sequence or duplicate on cellular networks?

## 5. Minors, Children & Sensitive Audiences
*Triggered when*: Educational software, games appealing to youth, or underage audiences might participate.
- **Statutory Restrictions**: COPPA (USA), GDPR-K (EU), UK Age-Appropriate Design Code.
- **Neutral Age Gating**: Neutral birthdate entry (no default "18+" preselected).
- **Prohibited Data Harvesting**: Ban on third-party behavioral analytics, persistent ad trackers, or location sharing.
- **Parental Consent Verification**: Verifiable parental consent before collecting personal identifiers.

## 6. Automation, Botting, Macros & External Integrations
*Triggered when*: Scraping websites, automating desktop tasks, interacting with unofficial APIs, or robotic macros.
- **Anti-Ban & Rate Throttling**: Humanized randomized jitter, rate limiting, header rotation, exponential backoff.
- **Emergency Kill Switch**: Instant hotkey or system tray trigger to abort all automated keystrokes/actions immediately.
- **Breaking Interface Resiliency**: What happens if the target application updates its UI, DOM selectors, or API payloads?
- **Session Expiration Handling**: How does the bot recover if the target session logs out mid-execution?

## 7. Hardware, Embedded Systems & Microcontrollers
*Triggered when*: Sensors, microcontrollers (ESP32, STM32, Arduino, Raspberry Pi), BLE, or custom PCBs are involved.
- **Power Envelope & Sleep Modes**: Battery-powered vs. continuous mains power; deep-sleep cycles.
- **Flaky Connectivity**: Store-and-forward telemetry caching when Wi-Fi/LTE is offline.
- **Firmware Lifecycle (OTA)**: Over-The-Air firmware updates with safe rollback (dual-bank flash) to prevent bricking.
- **Sensor Drift & Noise Calibration**: Outlier rejection, moving averages, baseline recalibration.

## 8. High-Security, Health & Regulated Data
*Triggered when*: Personal health data (HIPAA), financial credentials, legal contracts, or classified data.
- **Encryption Topology**: End-to-end encryption (E2EE) vs. encryption at rest and in transit.
- **Immutable Audit Trails**: Append-only tamper-evident logs for administrative actions.
- **Data Minimization**: Never collecting PII unless functionally indispensable.
- **Retention & Purge Policies**: Automated cron for hard deletion after retention expiration.

## 9. Destructive Actions, Data Mutations & Admin Overrides
*Triggered when*: Bulk deletions, configuration updates, server shutdowns, or critical database modifications.
- **Soft Deletion & Recovery**: Soft delete flag with 30-day trash bin vs. irreversible immediate hard purge.
- **Two-Step Confirmation**: Typing the exact entity name to confirm destructive changes.
- **Audit Logging**: Recording IP, timestamp, user ID, and diff for every administrative action.
