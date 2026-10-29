<!-- DO NOT COPY VERBATIM - REFERENCE FOR DIVERSE MENTAL MODELS ONLY -->
# Reference Example 1: 2D Pixel Roguelike ("Abyss Crawler")

> **Domain**: Desktop Video Game (Godot / C# or Rust)  
> **Persona Level**: Mid (Developer knows coding, but wants to keep scope strictly achievable)  
> **Notice**: Shows how the 6 dimensions and interview stages adapt to game development without assuming a web backend or SaaS metrics.

---

## 1. Vision & Core Problem
- **1-Sentence Definition**: A lightning-fast, run-based 2D subterranean extraction roguelike where players dive into procedurally shifting mines, grab relic ores, and must decide whether to bank them at drill stations or risk losing everything for deeper veins.
- **The Core Problem**: Most extraction games (e.g. Tarkov) are brutal 40-minute multiplayer sessions with massive inventory downtime. Players with only 15 minutes of free time have no offline, instant-restart equivalent.
- **Distinguishing Facets**:
  1. *Sub-8-Minute Runs*: Hard time limit per floor enforced by rising toxic gas.
  2. *Deterministic Physics Movement*: Tight grapple-hook traversal with zero input float.
  3. *Single-File Offline Saves*: Zero online account requirement; entirely playable offline on Steam Deck.

---

## 2. In-Scope vs. Non-Goals
- **In-Scope (MVP)**:
  - 3 mining biomes with distinct hazard types (toxic gas, falling stalactites, volcanic heat).
  - 1 playable miner class with 4 upgradable gadgets (grapple, seismic drill, sonar beacon, heat shield).
  - Local SQLite/JSON persistent run progression and run history.
  - Native controller support with custom rebinding and Steam Deck 60 FPS profile.
- **Explicit Non-Goals**:
  - [-] No multiplayer or co-op netcode (avoids netcode synchronization nightmares).
  - [-] No narrative voice acting or complex cinematic dialogue trees.
  - [-] No mobile touch controls or in-app microtransactions.

---

## 3. Blast Radius & Worst-Case Failure
- **Worst-Case**: Corrupted save file deleting 20 hours of meta-progression, or physics jitter trapping the player in terrain mid-run.
- **Mitigation Architecture**: Double-buffered atomic save writes (`save.json.tmp` renamed to `save.json`) with an automatic rolling backup of the last 3 runs.

---

## 4. Definition of Done
1. Complete run loop playable from title screen to death/extraction in under 8 minutes without crashes.
2. Stable 60 FPS verified on target low-spec profile (Steam Deck / Intel Iris Xe).
3. Save state survives hard application crash without file corruption.
