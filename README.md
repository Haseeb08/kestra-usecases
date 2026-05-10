# 🌊 Kestra Usecases Portfolio

This repository is a curated collection of workflow orchestration solutions built using **Kestra OSS**. It demonstrates how to unify disparate technical stacks—from APIs and databases to system scripts—into observable, event-driven pipelines.

## 🛠️ What is Kestra?

Kestra is a language-agnostic, open-source orchestrator that allows you to define complex logic using YAML. It bridges the gap between Development and Operations by providing a high-performance engine capable of handling millions of executions with native observability.  
[Learn more at kestra.io](https://kestra.io/)

## 🚀 Projects in this Repo

- **[Smart Weather Alert](./smart-weather-alert/)**
  - **Core Concept:** Event-driven alerting, Secret management, and Conditional branching.
  - **Tech Stack:** Kestra, HTTP API, Discord Webhooks.

## 🎓 Concepts Covered

- **Orchestration Logic:** Sequential and parallel execution, branching (`If/Then`), and workflow modularity.
- **Security & Secret Management:** Handling sensitive API endpoints via environment variables and the `secret()` function.
- **Dynamic Workflows:** Leveraging runtime `inputs` and task `outputs` to create flexible automation.
- **System Integration:** Connecting disparate services via REST APIs and Webhooks.
- **Infrastructure as Code:** Managing workflows in a version-controlled environment deployed on Docker/Linux.

## ⚙️ Requirements

- **Kestra (Open Source Edition)**
- **Docker & Docker Compose**

Follow the [Kestra Quickstart Guide](https://kestra.io/docs/getting-started/quickstart) to run your own instance locally.

---

_Maintained by Abdul | Certified Kestra Fundamentals Associate_
