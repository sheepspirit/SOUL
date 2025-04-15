# SOUL Architecture — MVP (Genesis Layer)

This document outlines the technical architecture of the SOUL system at its MVP stage.

## Core Components

### 1. SOUL Node
A local agent installed on the user’s machine, responsible for:
- Monitoring idle system resources
- Executing incoming cloud tasks
- Communicating with SOUL Cloud

### 2. SOUL Cloud
A decentralized coordination layer that:
- Manages task distribution
- Tracks availability of nodes
- Ensures fairness and redundancy

### 3. SOUL Token Engine
Tracks resource contribution and usage:
- Measures CPU/GPU time, bandwidth, memory
- Issues tokens for contribution
- Burns tokens on task execution

...

## System Flow (Simplified)

1. Alice installs SOUL Node → enters idle mode
2. Node reports availability to SOUL Cloud
3. Bob submits a heavy task via SOUL Dashboard
4. Task is token-paid → Cloud assigns it to available nodes
5. Nodes execute task → result is sent to Bob
6. Alice receives token reward
