<!-- DO NOT COPY VERBATIM - REFERENCE FOR DIVERSE MENTAL MODELS ONLY -->
# Reference Example 3: Edge Server Control Panel ("FleetNode")

> **Domain**: Infrastructure / DevOps / SRE Management Panel (Go + Lightweight React / HTMX)  
> **Persona Level**: Senior (DevOps Lead; deeply concerned with threat modeling, blast radius, and network partition resiliency)  
> **Notice**: Demonstrates rigorous senior-level probing: failure modes, cryptographic authentication, state recovery during network partitions, and zero unsolicited hand-holding.

---

## 1. Vision & Core Problem
- **1-Sentence Definition**: A lightweight, single-binary daemon and web interface for orchestrating containerized services across 10–50 air-gapped or low-bandwidth edge servers with automatic rollback on health-check failure.
- **The Core Problem**: Full Kubernetes (K8s/K3s) consumes too much RAM and network bandwidth on edge gateways (2GB RAM devices), and commercial solutions require permanent cloud outbound telemetry connections.
- **Distinguishing Facets**:
  1. *Sub-30MB Static Binary*: Written in Go; zero external runtime dependencies on the target host.
  2. *Autonomous Local State Reconciliation*: Edge nodes continue enforcing their declared container states even if disconnected from the central panel for 30 days.
  3. *Cryptographic Audit Trail*: All deploy commands signed with ed25519 keys; append-only tamper-evident log.

---

## 2. In-Scope vs. Non-Goals
- **In-Scope (MVP)**:
  - Agent daemon communicating via mTLS WebSockets to a lightweight management hub.
  - 1-click rolling deploy of Docker Compose manifests with automated rollback if `/healthz` fails within 60s.
  - Role-based permissions: Admin (deploy/stop/rollback) vs. Viewer (logs/metrics only).
- **Explicit Non-Goals**:
  - [-] No dynamic cluster autoscaling (edge hardware is fixed physical nodes).
  - [-] No built-in billing, tenant invoicing, or SaaS multi-cloud federation.
  - [-] No proprietary storage mesh (relies on host-mounted NVMe/eMMC paths).

---

## 3. Blast Radius & Worst-Case Failure
- **Worst-Case**: Bad deploy bricks remote server at an unmanned cell tower 300km away, requiring physical technician dispatch.
- **Mitigation Architecture**: Watchdog timer and dual-container swapping: previous container is never stopped until new container passes 3 consecutive HTTP health probes. Automatic fallback to golden image on crash-loop.

---

## 4. Definition of Done
1. Deploy command successfully updates a live container on an edge simulator node within 15 seconds.
2. Simulated bad deployment triggers automatic rollback and alerts within 75 seconds.
3. System survives power disconnect mid-deployment and restores valid operational state upon boot.
