---
title: "Configuration Examples"
linkTitle: "Examples"
weight: 5
description: "Production-ready YAML configuration templates for mapping industrial sensor inputs to AeroSync."
---

# AeroSync Configuration Examples

AeroSync agents are configured using simple, human-readable YAML files. Below is a production deployment example showcasing how to pull data from an industrial sensor bus and route it to your cloud hub.

## Standard Edge Pipeline Configuration

Save the following file framework as `aerosync.yaml` inside your local deployment directory. This template tells the agent to collect temperature data from a factory floor Modbus sensor every 5 seconds, cache it locally using SQLite, and forward it via standard HTTPS.

```yaml
version: "2.4"
node_identity:
  device_id: "edge-node-manchester-01"
  cluster_group: "uk-manufacturing-north"

# Ingestion Source (Where data comes from)
sources:
  - type: "modbus"
    name: "factory_floor_temp_sensor"
    connection: "192.168.1.50:502"
    scan_interval_ms: 5000
    metrics:
      - register: 40001
        type: "float32"
        label: "core_temperature_celsius"

# Storage Resiliency Layer (What happens if connection drops)
cache:
  storage_backend: "sqlite"
  directory: "/var/lib/aerosync/cache"
  max_cache_size_gb: 5
  eviction_policy: "fifo" # First In, First Out if storage fills up

# Outbound Routing Pipeline (Where data goes)
sinks:
  - type: "cloud_hub"
    endpoint: "https://aerosync.io"
    compression: "gzip"
    retry_policy:
      initial_interval_sec: 2
      max_interval_sec: 60
      max_retries: 5
```

## Running the Example

Once you have written your configuration file, mount it directly into your runtime container to launch the automated data pipeline pipeline:

```bash
docker run -d \
  --name aerosync-agent \
  -v \$(pwd)/aerosync.yaml:/etc/aerosync/aerosync.yaml \
  -v aerosync-storage:/var/lib/aerosync/cache \
  cr.aerosync.io/edge/agent:latest
```

---

## Next Steps

* Need to customize how your developers contribute updates or custom plugins to this repository framework? Head directly over to our **[Contribution Guidelines](../contribution-guidelines/)**.
