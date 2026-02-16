# Monitoring_project

## 📌 Project Overview

This project solves ACCENT's log monitoring fragmentation: sysadmins manually juggling 3 SSH terminals to correlate Apache + MySQL + system logs — taking 4+ minutes per incident.

I designed and deployed a lightweight Grafana Loki stack that:
→ Unified all logs into one dashboard  
→ Cut detection time from **4 min 12 sec → 28 sec** (96% faster)  
→ Eliminated routine SSH dependency  
→ Runs in **387 MB RAM** (under 500 MB VirtualBox constraint)

This reflects real-world DevOps practice: identify pain point → design constraint-aware solution → deliver production-ready tooling.

## 🏗️ Architecture

[Apache Logs] ───┐
[MySQL Logs] ────┼──→ Promtail (collector) ──→ Loki (storage) ──→ Grafana (dashboard)
[Syslog] ────────┘ job="apache" job="mysql" Unified view

## 🧰 Tools & Technologies

- **Docker** (containerization)
- **Docker Compose** (orchestration)
- **Grafana** (visualization)
- **Loki** (log aggregation)
- **Promtail** (log shipping)
- **YAML** (infrastructure as code)

## 🚀 What I Built

### 1️⃣ Architecture Design
Defined label-based correlation strategy (`job="apache"`, `job="mysql"`) to enable cross-service queries without path dependencies.

### 2️⃣ Declarative Deployment
Created 3 YAML files for reproducible deployment:
docker compose up -d
→ Entire stack (Grafana + Loki + Promtail) running in one command.
```
📂 Repository Structure
accent-monitoring/
├── docker-compose.yml          # Stack orchestration
├── loki-config.yaml            # Storage & retention
├── promtail-config.yaml        # Log paths + labels
├── README.md
└── screenshots/
    ├── dashboard-apache.png
    ├── dashboard-mysql.png
    ├── dashboard-system.png
    └── dashboard-correlation.png
```
🎯 What I Learned
Real monitoring isn't about big tools — it's about solving actual constraints
Labels > paths for cross-service correlation
Lightweight ≠ limited: 387 MB stack outperformed enterprise alternatives
Production value comes from adoption — ACCENT's team now uses this daily


💼 Why This Project Matters
This isn't a tutorial demo — it's a solution deployed in ACCENT's real VirtualBox environment, solving a documented pain point with measurable impact (96% faster detection, zero SSH dependency).

📌 Author
KHEMIRI DOUAA | DevOps & Observability Enthusiast 
