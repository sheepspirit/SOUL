# SOUL — Proof-of-Contribution Protocol (PoC)

> Authored by Sergei Kokurin (sheepspirit), 2025  
> This document defines the reward, verification, and trust mechanisms behind resource sharing in the SOUL Network.

---

## Purpose

**Proof-of-Contribution (PoC)** is the cryptographic trust layer that ensures every SOUL Node is rewarded fairly — based on actual, measurable, and verifiable work.  
It is the invisible contract between your machine and the network: *“I helped. Here’s the proof.”*

---

## Core Objectives

- 🔍 **Accuracy** — Precisely measure all real resource usage  
- 🔐 **Integrity** — Sign and verify all contributions cryptographically  
- 🛡️ **Anti-fraud** — Prevent idle-farming and fake execution  
- ⚖️ **Fairness** — Adjust rewards dynamically by reliability and demand  
- 🔄 **Scalability** — Efficient across thousands of machines  
- 👁️ **Transparency** — Let every user see what their machines have done  

---

## Contribution Flow

When a SOUL Node completes a distributed task, it generates a **Proof Package** containing:

### 🧩 Components:

1. **Task Hash**  
   Unique identifier of the assigned workload

2. **Resource Log**  
   Real-time, high-resolution metrics:
   - CPU cycles (user/kernel space)
   - GPU operations
   - RAM usage over time
   - Bandwidth consumed
   - Execution duration

3. **Execution Metadata**
   - Start and end timestamps
   - Requester ID / Task origin
   - Node fingerprint (public key + anonymized signature)

4. **Output Hash**  
   Checksum of the result (validated by requester or network)

### 🔏 Verification Path:

- Proof Package is **digitally signed**  
- Encrypted and sent to **SOUL Cloud**  
- Optionally hashed on-chain  
- **Verified** by peers or redundant tasks before reward issuance

---

## Multi-Layer Verification

### 1. **Local Logging**
- Linux-native metrics: `perf`, `/proc`, `cgroups`, `netstat`
- Logged by SOUL Agent, signed in real-time

### 2. **Peer Validation**
- Random nodes check anonymized task summary
- Validate resource claims and output hash
- Optionally simulate task fragment for critical validation

### 3. **Redundant Execution**
- High-value tasks may run on 2–3 nodes
- Majority result determines final proof
- Prevents fake or manipulated output

---

## Reward Calculation

Rewards are based on **real work**, scaled by **trust and uptime modifiers**:

```plaintext
Reward = Σ (Resource_weight × Resource_usage) × UptimeMultiplier × ReputationScore
```

### 🔍 Parameters:

| Term              | Meaning                                                  |
|-------------------|-----------------------------------------------------------|
| Resource_usage    | Normalized units (e.g. CPU seconds, RAM GB-hours)         |
| Resource_weight   | Dynamically adjusted based on global demand               |
| UptimeMultiplier  | Reflects average availability over the past 7 days        |
| ReputationScore   | Trust index based on task success rate and honesty        |

### ⚖️ Uptime Multiplier (Max = 1.0):

| Uptime (7-day avg) | Multiplier |
|--------------------|------------|
| ≥ 95%              | 1.00       |
| 80–94%             | 0.95       |
| 60–79%             | 0.80       |
| 30–59%             | 0.60       |
| < 30%              | 0.40       |

> 💡 Uptime doesn’t increase rewards — it **protects them**. Only verified contribution earns tokens.

---

## Multi-Device Contribution

- Users may run **multiple SOUL Nodes** under a single account/wallet  
- Each device contributes independently  
- Tokens are aggregated per user and shown in the Dashboard  
- SOUL Cloud handles routing, task balancing, and credit assignment

---

## Anti-Cheating & Defense

- 🔐 Signed logs + encrypted proof packages  
- 🔁 Peer validation + redundant execution  
- 📉 Penalties for dishonest nodes  
- 🧬 Public node trust/reputation score  
- 🕵️ Random challenge-response tasks  
- 🧠 Future layer: zk-proofs for full integrity

---

## User Transparency

All user-visible data via SOUL Dashboard:

- ✅ Tasks executed per device  
- 💰 Tokens earned by type (CPU, GPU, RAM, bandwidth)  
- 📊 Uptime stats and reputation score  
- 🔍 Downloadable Proof-of-Contribution log

---

## Extensions (Future)

- 📱 Lightweight PoC for mobile, ARM, edge devices  
- 🆔 Decentralized ID integration  
- 🤖 AI-based anomaly detection  
- 🔗 Public proof registry for transparent auditing

---

## Next Steps

- [ ] Finalize Linux resource logging spec for SOUL Agent  
- [ ] Implement Proof Package format and signing protocol  
- [ ] Build peer validation logic with quorum rules  
- [ ] Link PoC output to Token Engine for reward generation
