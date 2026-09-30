---
title: "Contribution Guidelines"
linkTitle: "Contributions"
weight: 6
description: "How to contribute patches, bug fixes, and data pipeline plugins to the AeroSync project."
---

# AeroSync Contribution Guidelines

Thank you for your interest in improving the AeroSync Edge-to-Cloud framework! We welcome contributions from corporate engineering teams, independent developers, and open-source system operators.

## Development Workflow

To ensure stability across our distributed telemetry systems, all code modifications must follow our standard repository lifecycle:

1. **Fork the Repository:** Create a personal fork of the main repository framework on GitHub.
2. **Create a Feature Branch:** Isolate your code updates in a descriptive branch:
   ```bash
   git checkout -b feature/your-plugin-name
   ```
3. **Write Tests:** Every data pipeline connector or optimization block must include unit tests. Ensure your pipeline builds cleanly locally.
4. **Submit a Pull Request (PR):** Open a PR against our `main` branch. Provide a detailed summary explaining your patch.

## Code Quality Standards

* **Language Targets:** Core runtime agents are written in Rust. Command-line utilities use Go. Custom sensor parsing scripts should adhere to Python 3.10+ rules.
* **Security Constraints:** Any modification to our local file buffering system or network sockets must not leak unencrypted credentials or bypass TLS 1.3 protections.
* **Documentation updates:** If your feature adds a new keyword or parameter option to the `aerosync.yaml` model, you must update the core **[Configuration Examples](../examples/)** page alongside your code submission.

## Community Code of Conduct

We are dedicated to providing a professional, harassment-free environment for all engineering collaborators. Please ensure all code discussions, issue trackers, and pull request reviews remain respectful, concise, and focused entirely on the technical problem at hand.
