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


Main Components

1. Task Runner

Pulls tasks from SOUL Cloud

Executes safely within Docker sandbox or similar isolated environment

Supports CPU- and GPU-intensive workloads

Measures execution performance in real-time

2. Resource Monitor

Uses trusted Linux-native interfaces:

/proc/stat, /proc/meminfo, nvidia-smi, netstat, cgroups, perf

Logs high-resolution usage data

Works in both standby and low-usage modes

3. Proof-of-Contribution (PoC) Engine

Collects resource logs

Computes output hash

Packages signed and encrypted PoC

Submits to SOUL Cloud or peer verifiers

4. Updater Client

Receives system updates securely

Validates signatures and integrity

Can install plugins, modules, or hotfixes without manual intervention

5. RPC Interface

Provides local API for:

Dashboard UI

Developer tooling

Optional CLI

Uses gRPC or Unix sockets

Operational Modes

Mode

Description

💤 Standby

Full resource sharing, max token earning

⚙️ Active

Limited contribution (e.g. 10–20%) during light user activity

🔒 Opt-Out

Paused sharing; only local updates and monitoring active

Users can switch modes via the Dashboard or CLI. Auto-mode may adjust dynamically based on CPU load or time of day.

Privacy & Security

✅ No user files or personal data ever accessed

✅ All outbound communication is encrypted (TLS)

✅ Workloads run in sandboxed environments

✅ Open-source and verifiable binaries

✅ Local data never leaves device without consent

Resource Footprint

CPU: Idle most of the time; minimal overhead

RAM: Lightweight, <200MB average

Disk: Stores task cache and logs (~100MB typical)

Network: Communicates only when needed; efficient payloads

Installation

Available as:

.deb, .rpm, .AppImage, .tar.gz for Linux

Docker container

Requires:

Root or system-level access (once)

Persistent connection (recommended)

Optional wallet setup for token rewards

Future Enhancements

✅ Plugin system for task types (e.g. ML, render, compile)

✅ Portable version for edge devices (Raspberry Pi, Jetson)

✅ Mobile adaptation (limited PoC)

✅ Remote node control from main dashboard

✅ Smart energy mode integration (e.g. stop on battery)

Summary

The SOUL Node is the smallest unit of distributed intelligence within the SOUL network.It listens, contributes, learns, and evolves — silently and respectfully — to make the whole system more powerful, transparent, and humane.

“It’s not just running on your machine. It’s working with you — and for the world.”
