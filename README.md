# AKS Observability Stack — Managed Prometheus & Grafana on Azure

> Production-ready setup guide for Azure Managed Prometheus and Azure Managed Grafana on AKS — complete with alerting, dashboards, and SRE best practices.

[![Azure](https://img.shields.io/badge/Microsoft_Azure-0078D4?style=flat-square&logo=microsoft-azure&logoColor=white)](https://azure.microsoft.com)
[![Kubernetes](https://img.shields.io/badge/AKS-Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white)](https://azure.microsoft.com/services/kubernetes-service)
[![Prometheus](https://img.shields.io/badge/Prometheus-Managed-E6522C?style=flat-square&logo=prometheus&logoColor=white)](https://prometheus.io)
[![Grafana](https://img.shields.io/badge/Grafana-Managed-F46800?style=flat-square&logo=grafana&logoColor=white)](https://grafana.com)
[![Stars](https://img.shields.io/github/stars/SauravSrivastav/Azure-Managed-Prometheus-and-Grafana?style=flat-square)](https://github.com/SauravSrivastav/Azure-Managed-Prometheus-and-Grafana)

---

## Overview

This guide covers setting up **Azure Managed Prometheus** and **Azure Managed Grafana** for production AKS clusters — eliminating the operational overhead of self-managed monitoring infrastructure.

Built by a **DevOps Manager** with real-world experience operating Kubernetes platforms at scale in the UAE enterprise and fintech sectors.

---

## What You Get

- **Zero-ops monitoring** — Azure manages Prometheus and Grafana infrastructure
- **Pre-built dashboards** — Node, pod, namespace, and workload metrics out of the box
- **Alerting integration** — Alert rules connected to Azure Monitor and Action Groups
- **Long-term retention** — Metrics stored in Azure Monitor workspace
- **Cost-efficient** — Pay only for metrics ingested, no VM management

---

## Architecture

```
AKS Cluster
    │
    ├── Azure Monitor Agent (DaemonSet)
    │       └── Scrapes pod/node metrics
    │
    ▼
Azure Monitor Workspace
    │
    ├── Azure Managed Prometheus
    │       └── Stores time-series metrics
    │
    └── Azure Managed Grafana
            └── Visualizes metrics + alerts
```

---

## Prerequisites

- Azure subscription with Contributor access
- AKS cluster (any version)
- Azure CLI (`az`) installed and authenticated
- `kubectl` configured for your cluster

---

## Quick Setup

### Step 1 — Enable Azure Monitor on AKS

```bash
az aks update   --resource-group <rg-name>   --name <aks-name>   --enable-azure-monitor-metrics
```

### Step 2 — Create Azure Managed Grafana

```bash
az grafana create   --name <grafana-name>   --resource-group <rg-name>
```

### Step 3 — Link Grafana to Prometheus

```bash
az aks update   --resource-group <rg-name>   --name <aks-name>   --grafana-resource-id <grafana-id>
```

> Full step-by-step guide in [steps.md](./steps.md) | Troubleshooting in [error.md](./error.md) | FAQs in [FAQ.md](./FAQ.md)

---

## Files

| File | Description |
|------|-------------|
| `steps.md` | Complete setup walkthrough with CLI commands |
| `FAQ.md` | Common questions and answers |
| `error.md` | Known issues and fixes |
| `immportant_urls.md` | Reference links and documentation |

---

## SRE Best Practices Covered

- Alert fatigue prevention with proper threshold tuning
- Recording rules for expensive PromQL queries
- Namespace-level resource quotas monitoring
- Node pressure alerts (CPU, memory, disk)
- Pod crash loop and OOMKilled detection

---

## Built By

**Saurav Srivastav** — DevOps Manager at Emirates Flight Catering | Azure · AKS · SRE · Zero Trust | Dubai, UAE

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0077B5?style=flat-square&logo=linkedin)](https://www.linkedin.com/in/sauravsrivastav2205/)
[![Portfolio](https://img.shields.io/badge/Portfolio-Visit-0078D4?style=flat-square&logo=vercel)](https://saurav-srivastav-portfolio.vercel.app)

---

<sub>Azure · AKS · Kubernetes · Prometheus · Grafana · SRE · Observability · Monitoring · DevOps · DevSecOps · Azure Monitor · Dubai UAE</sub>
