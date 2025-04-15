# SOUL Token Engine

## Purpose

**SOUL Tokens (ST)** are the heartbeat of the trust-based economy within the SOUL ecosystem.  
They are fairly earned by sharing computational resources — primarily during idle times, and optionally during light usage.  
Tokens are spent to access powerful, distributed cloud computation, enabling users to amplify their capabilities on demand.

---

## Token Lifecycle

### 1. Earning Tokens — Proof-of-Contribution (PoC)

Tokens are issued proportionally to the user’s contribution to the network.

**Metrics Tracked:**
- CPU time
- GPU time
- RAM usage
- Bandwidth
- Node uptime & responsiveness

**Modes of Contribution:**
- 💤 *Standby Mode:* Full earning — 100% of available idle resources
- 🌓 *Active Mode:* Partial earning — up to 10–20% of system power may be shared during light user activity, based on preferences

**Verification & Fairness:**
- All completed tasks are hashed and cryptographically verified
- Work units are signed and traceable
- Nodes must maintain reputation scores based on success rate and behavior

**Reward Calculation:**
- Dynamic, adjusted by:
  - Resource demand across network
  - Task complexity
  - Scarcity of available nodes

---

### 2. Spending Tokens — Compute Access

When a user performs a task that exceeds their local compute capacity, the system evaluates whether it can be:

- Distributed across SOUL Cloud
- Accelerated using shared power from other contributors

**Prompt Example:**
> “This task requires additional compute power. Spend 12 ST to run via SOUL Cloud?”

**User Options:**
- ✅ Manual confirmation per task
- 🔁 Enable *Auto-spend Mode* up to a custom monthly cap (e.g. 100 ST/month)
- 💰 Purchase additional tokens via:
  - Built-in crypto/fiat marketplace
  - Peer-to-peer token exchange

---

### 3. Token Management Features

Accessible via the **SOUL Dashboard:**
- 💼 View balance, token flow history, and earning statistics
- ⚙️ Set auto-spend limits and energy contribution preferences
- 🧠 See insights:  
  - “You earned 8 ST today by sharing idle time”  
  - “You saved 3.5 hours of compute time this week”

**Advanced (optional):**
- 🔒 Stake tokens for access priority or governance rights
- 📊 Visual analytics of contribution vs consumption over time

---

## Use Cases

SOUL Tokens enable real, valuable interaction with the network:

- 🚀 High-performance tasks: rendering, AI model training, batch computation
- 🧬 Distributed collaboration: open scientific or civic projects
- 🗳 Governance: voting on upgrades, system policies, reputation models
- 🤝 Marketplace: buying/selling compute power between users

---

## Economics & Fairness

- 🌀 **Elastic supply** — new tokens minted based on real-world contribution
- 🔥 **Token burn** — a small % of spent tokens is burned to control inflation
- 🧾 **Transparent accounting** — all transactions recorded on the SOUL Chain
- ⚖️ **Cheat protection:**
  - Redundant verification by independent nodes
  - Task fragmentation with consistency checking
  - Zero-knowledge proof support (planned)

---

## Next Steps

- ✅ Choose token protocol (Substrate native / EVM-compatible)
- ✅ Define Proof-of-Contribution algorithm
- ⬜ Implement token tracker inside SOUL Node
- ⬜ Integrate payment gateway (crypto + fiat options)
- ⬜ Build token-aware UX components in SOUL Dashboard

---

> *“Value is not mined. It is earned — by contribution, by care, by presence.”*
