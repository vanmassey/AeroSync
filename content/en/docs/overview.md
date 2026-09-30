---
title: "System Overview"
linkTitle: "Overview"
weight: 1
description: "A high-level look at the AeroSync edge-to-cloud telemetry ecosystem and its primary components."
---

# AeroSync System Overview

AeroSync is an enterprise-grade IoT edge data orchestration engine. It acts as an intelligent intermediary layer between distributed industrial hardware and centralized cloud computing analytics suites. 

By running lightweight runtime agents directly on your edge gateways, AeroSync bridges the gap between unstable field operating environments and modern data warehouses.

## Architecture Ecosystem

The AeroSync framework consists of three core structural modules working in tandem:

[ Industrial Sensors ] ---> ( AeroSync Edge Agent ) ---> [ Cellular/Satellite ] ---> [ AeroSync Cloud Hub ]
| (Local SQLite Cache)


1. **AeroSync Edge Agent:** A lightweight daemon optimized for ARM and x86 architectures. It ingests data directly from local industrial buses (Modbus, OPC-UA, MQTT) and manages local data delivery pipelines.
2. **Resilient Cache Layer:** An integrated database engine sitting inside the Edge Agent that acts as a secure container for encrypted telemetry records when external routing links fail.
3. **AeroSync Cloud Hub:** The ingestion target cluster deployed within your cloud environment (AWS, Azure, or GCP). It processes incoming data, decrypts payloads, verifies device signatures, and hands off clean data to your visualization or ML pipelines.

## Target Use Cases

AeroSync is purpose-built for industries where data drops equal financial or operational losses:

* **Renewable Energy Infrastructure:** Monitoring remote wind and solar farms where cellular connections degrade under severe weather conditions.
* **Maritime & Fleet Logistics:** Aggregating diagnostic engines data on cargo vessels passing through low-bandwidth satellite zones.
* **Smart Smart Manufacturing:** Maintaining continuous telemetry loops inside highly shielded industrial facilities experiencing high electromagnetic interference.

---

## Where to Go Next

* Ready to see the pipeline in action? Head straight over to the **[Getting Started](../getting-started/)** guide to pull down a local sandbox agent.
* Want to look under the hood at our storage logic? Read the **[Core Concepts](../concepts/)** architectural manual.
