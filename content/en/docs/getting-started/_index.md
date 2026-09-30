---
title: "Getting Started"
description: "Everything you need to know to install and configure your first AeroSync Edge node."
categories: [Documentation]
tags: [setup, deployment]
weight: 2
---

{{% pageinfo color="warning td-max-width-on-larger-screens mx-0" %}}
**Production Alert:** This guide covers deploying a single AeroSync node for testing. For high-availability Kubernetes or cluster deployments, please refer to our Advanced Operations manual.
{{% /pageinfo %}}

Information in this section helps your operators and engineers test the AeroSync Data Pipeline engine in a sandboxed local environment.

## Prerequisites

Before deploying the runtime agent, ensure your host environment meets the following baseline requirements:

*   **Operating System:** Linux (Ubuntu 22.04+, RHEL 8+), macOS 13+, or Windows 11 with WSL2 enabled.
*   **Hardware:** Minimum 1 vCPU, 512MB RAM available, and 10GB of storage space for local data caching.
*   **Software Containers:** Docker Engine 20.10+ or Podman installed and running.

## Installation

The AeroSync Edge runtime engine is packaged as an optimized scratch-base image container hosted via our public registry. Pull the container directly down to your system terminal:

```bash
docker pull cr.aerosync.io/edge/agent:latest
```

Alternatively, for native deployments on Linux servers without a container runtime, you can install the standalone binary using our shell deployment script:

```bash
curl -fsSL https://aerosync.io | sh
```

## Setup

Before launching the pipeline, your agent requires an environment key to safely authenticate back to your management dashboard hub. 

1. Generate a secure fallback cryptographic folder on your storage layer to cache messages if internet access drops out:
   ```bash
   docker volume create aerosync-storage
   ```
2. Export your credentials parameter as a secure environment variable on your machine:
   ```bash
   export AS_API_KEY="aero_sandbox_test_key_99120"
   ```

## Try it out!

Test your node setup immediately by initializing a standard telemetry daemon container. Run the command below to start monitoring and streaming your hardware pipeline:

```bash
docker run -d \
  --name aerosync-agent \
  -e AS_API_KEY=$AS_API_KEY \
  -v aerosync-storage:/var/lib/aerosync \
  cr.aerosync.io/edge/agent:latest
```

Verify your node successfully launched and connected by reading the runtime streaming logs:

```bash
docker logs aerosync-agent
```
You should see a clean sequence showing `[INFO] AeroSync connected safely to regional cluster hub. Processing engine status: OK.`
