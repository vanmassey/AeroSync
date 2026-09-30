---
title: "Core Concepts"
linkTitle: "Concepts"
weight: 3
description: "Understand the foundational architecture of AeroSync, including edge storage, dual-queue mechanics, and data resiliency."
---

# AeroSync Core Concepts

AeroSync is engineered from the ground up to solve a critical industrial problem: **unreliable network connectivity at the edge.** 

Whether your nodes are deployed on remote wind turbines, maritime vessels, or factory floors with severe electrical interference, AeroSync guarantees that your critical telemetry data reaches your cloud analytics layer safely.

## The Three Pillars of AeroSync Resiliency

To ensure zero-loss data delivery without blowing out edge hardware costs, AeroSync relies on three distinct architectural concepts:

### 1. Dual-Queue Pipeline Mechanics
Every incoming sensor payload hits an ultra-fast, volatile in-memory queue. If network latency spikes or a total drop occurs, the pipeline instantly splits:
* **High-Priority Data:** Critical alerts remain in memory to be retried instantly.
* **Bulk Diagnostic Data:** Telemetry streams are immediately written to local disk space to clear system RAM.

### 2. State Synchronization & Backpressure Control
When the network link comes back online, the Edge Agent doesn't just flood your cloud servers with historical data. It uses built-in backpressure tokens to gently throttle older messages alongside real-time metrics. This prevents your cloud databases from hitting bottleneck errors.

### 3. Hardware Root-of-Trust Security
Data integrity is pointless without tamper-proofing. AeroSync authenticates edge nodes using local hardware cryptographic keys (like TPM 2.0 modules). This ensures payload data cannot be spoofed or intercepted during transmission over public cellular networks.
