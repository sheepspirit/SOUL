# SOUL Node — Architecture & Functionality

> Authored by Sergei Kokurin (sheepspirit), 2025  
> This document describes the local daemon that powers the SOUL Network from within the user's system.

## Purpose

The **SOUL Node** is the local daemon that powers the entire SOUL ecosystem from within the user’s machine.  
It observes system activity, accepts distributed tasks, verifies and logs resource usage, and communicates securely with SOUL Cloud and the Token Engine.

It is lightweight, self-managed, privacy-conscious, and open-source.

---

## Core Responsibilities

- ⚙️ Monitor and log available resources
- 📥 Accept and execute distributed tasks from SOUL Cloud
- 🔏 Package cryptographic Proof-of-Contribution
- 🔄 Receive software updates from SOUL Update Core
- 🧠 Report node status, uptime, performance
- 💼 Interact with local SOUL Dashboard

---

## Node Architecture Overview

```plaintext
+------------------------+
|     SOUL Dashboard     | ← UI layer for status, settings, logs
+------------------------+
           ↑
           ↓
+------------------------+
|      SOUL Node Daemon   | ← Core service (Python or Rust)
+------------------------+
| Submodules:             |
|                        |
| • Task Runner           | ← Executes workloads
| • Resource Monitor      | ← Tracks CPU, GPU, RAM, Net
| • PoC Engine            | ← Builds proof packages
| • Updater Client        | ← Fetches updates
| • RPC Interface         | ← Communicates with Dashboard & Cloud
+------------------------+
           ↓
+------------------------+
|      Linux System       | ← /proc, perf, cgroups, etc.
+------------------------+
```

## 🔧 Main Components

### 1. 🧪 Task Runner

- Pulls tasks from SOUL Cloud  
- Executes safely in sandboxed environments (e.g. Docker)  
- Supports CPU/GPU-intensive workloads  
- Measures and logs execution performance in real time  

---

### 2. 📊 Resource Monitor

- Uses trusted Linux-native interfaces:  
  `/proc/stat`, `/proc/meminfo`, `nvidia-smi`, `netstat`, `cgroups`, `perf`  
- Logs high-resolution usage data  
- Functions in both standby and low-usage modes  

---

### 3. 🔐 PoC Engine (Proof-of-Contribution)

- Collects detailed resource logs  
- Computes and signs task output hashes  
- Packages verifiable PoC reports  
- Submits to SOUL Cloud or peer verifiers  

---

### 4. 🌐 Updater Client

- Receives verified updates, patches, and modules  
- Validates signatures before applying  
- Supports zero-downtime hotfixes and plugins  

---

### 5. 📡 RPC Interface

- Serves the local API for:  
  - SOUL Dashboard  
  - Developer tools  
  - Optional CLI  
- Uses gRPC or Unix sockets

---

## 🌀 Operational Modes

SOUL Node operates in three adaptive modes:

| Mode      | Description                                                                 |
|-----------|-----------------------------------------------------------------------------|
| 🟢 Standby   | Full resource sharing. Node contributes maximum available power.            |
| ⚙️ Active    | Limited contribution (10–30%) during light user activity.                  |
| 🛑 Opt-Out   | No resource sharing. Only self-monitoring and update functions active.     |

Users can switch modes via Dashboard or CLI.  
Auto-mode dynamically adjusts based on system load, time of day, or user preferences.

---

## 🔐 Privacy & Security

- ✅ No access to user files or personal data  
- ✅ All outbound communication encrypted (TLS)  
- ✅ Workloads executed in sandboxed environments  
- ✅ Source code and binaries are open and auditable  
- ✅ No background data exfiltration — consent required

---

## 📉 Resource Footprint

- **CPU**: Idle ~99% of time; spikes only during task execution  
- **RAM**: Lightweight footprint (~100–200MB average)  
- **Disk**: Stores temporary logs and task cache (~100MB typical)  
- **Network**: Optimized for low-traffic operations

---

## 📦 Installation & Distribution

Available as:

- `.deb`, `.rpm`, `.AppImage`, `.tar.gz` packages for major Linux distros  
- Docker container image

Requirements:

- One-time system-level access (root/sudo)  
- Persistent network connection (recommended)  
- Optional wallet for token rewards

---

## 🔮 Future Enhancements

- ✅ Plugin system for new task types (e.g. ML, rendering, compiling)  
- ✅ Portable version for edge devices (e.g. Raspberry Pi, Jetson Nano)  
- ✅ Idle-time estimator for smoother contribution scheduling  
- ✅ Optional GPU priority tuning during user activity

## Summary

The SOUL Node is the smallest unit of distributed intelligence within the SOUL network.It listens, contributes, learns, and evolves — silently and respectfully — to make the whole system more powerful, transparent, and humane.

“It’s not just running on your machine. It’s working with you — and for the world.”
