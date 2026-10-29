<!-- DO NOT COPY VERBATIM - REFERENCE FOR DIVERSE MENTAL MODELS ONLY -->
# Reference Example 5: Academic Micro-Community ("ScholarMesh")

> **Domain**: Social / Niche Community Platform (Next.js / PostgreSQL / Supabase)  
> **Persona Level**: Junior (Founder with bootcamp coding background, understands web dev basics, needs guidance on moderation and compliance)  
> **Notice**: Demonstrates how trigger reminders (UGC, authentication, moderation, email deliverability) surface naturally through guided options with pros/cons.

---

## 1. Vision & Core Problem
- **1-Sentence Definition**: An invite-only, peer-reviewed discussion platform for computational biology researchers to annotate preprint papers, debate methodology openly, and exchange reproducible notebook snippets without academic paywalls or Twitter noise.
- **The Core Problem**: Academic discourse on Twitter/X is fragmented and noisy; traditional academic journals take 9 months to publish critique letters. Researchers need an authenticated, high-signal, semi-private venue.
- **Distinguishing Facets**:
  1. *ORCID Institutional Verification*: Only verified researchers with an ORCID ID can publish root posts.
  2. *Inline PDF Margin Annotations*: Discussions are anchored to specific paragraphs in arXiv/bioRxiv PDFs.
  3. *Reputation via Verifiable Code Replicability*: Upvotes tied to confirmed test reproductions.

---

## 2. In-Scope vs. Non-Goals
- **In-Scope (MVP)**:
  - ORCID OAuth integration with auto-populated publication history.
  - Interactive PDF viewer with shared margin commenting and Markdown/LaTeX rendering.
  - Basic reporting queue for community moderators.
- **Explicit Non-Goals**:
  - [-] No native mobile iOS/Android app (responsive web only for MVP).
  - [-] No real-time video conferencing or audio breakout rooms.
  - [-] No monetization, paywalled subscriptions, or ads in Phase 1.

---

## 3. Blast Radius & Worst-Case Failure
- **Worst-Case**: Targeted academic defamation or harassment through margin notes damaging a junior scholar's career.
- **Mitigation Architecture**: Real-name policy enforced via ORCID; 1-click author blocking; automatic quarantine of annotations reported by 2+ verified members until human moderator review.

---

## 4. Definition of Done
1. Researcher can sign in via ORCID, paste a bioRxiv URL, and render the paper in the custom viewer in <3 seconds.
2. Annotations can be placed on paragraph text and render LaTeX equations accurately.
3. Moderator test dashboard allows approving/dismissing reported notes within 2 clicks.
