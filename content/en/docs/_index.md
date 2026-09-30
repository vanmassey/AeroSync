---
title: "AeroSync Documentation Hub"
linkTitle: "Documentation"
weight: 1
description: "The complete technical manual resource for the AeroSync Edge-to-Cloud industrial data pipeline framework."
---

# AeroSync Technical Documentation

Welcome to the central knowledge repository for **AeroSync**, an enterprise-grade orchestration framework designed for continuous, resilient data streaming from the industrial edge to the cloud.

Whether you are a field technician deploying an agent on a remote gateway, a software engineer writing custom telemetry parsers, or a systems architect planning an enterprise cloud data lake, this hub contains the resources you need.

---

## Quick Navigation Matrix

Get started immediately by choosing the entry path that matches your current goal:

| Section | Focus Area | Intended Audience |
| :--- | :--- | :--- |
| **[System Overview](./overview/)** | High-level ecosystem architecture and industrial hardware use cases. | Systems Engineers, CIOs, Architects |
| **[Getting Started](./getting-started/)** | A 10-minute technical sandbox deployment guide using Docker container runtimes. | DevOps, Operations Technicians |
| **[Core Concepts](./concepts/)** | Architectural deep dive into data drop handling, dual-queues, and TPM cryptography. | Core Developers, Security Teams |
| **[Configuration Examples](./examples/)** | Production-ready YAML reference templates for mapping Modbus or MQTT sensor nodes. | Deployment Technicians, Field Crews |
| **[Developer Guidelines](./contribution-guidelines/)** | Code quality requirements, repository lifecycles, and pull request submission steps. | Open Source Contributors, Plugin Writers |

---

## Platform Support & Lifecycle Status

The AeroSync framework maintains strict backward compatibility for data schemas. The current system architecture supports the following operational environments out of the box:

*   **Supported Input Buses:** Modbus TCP/RTU, OPC-UA, MQTT, Kafka, HTTP Webhooks.
*   **Supported Cloud Ingestion Targets:** AWS IoT Core, Azure IoT Hub, Google Cloud Pub/Sub, custom REST endpoints.
*   **Operating Footprint:** Minimal resource consumption (under 50MB RAM at idle), fully optimized for headless Linux gateways.
