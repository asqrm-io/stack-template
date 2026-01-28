# 🚀 QRM Stack Catalog (Stack Templates)

## Overview

**QRM Stack Catalog** is a centralized library of pre-configured application stacks, services, and deployment templates. It enables teams to quickly discover, configure, and deploy production-ready workloads using best-practice defaults.

Instead of building infrastructure from scratch every time, teams can launch complete environments in minutes using reusable, standardized stack templates.

---

## Purpose

The Stack Catalog helps teams:

- Deploy apps and services faster  
- Reuse proven infrastructure patterns  
- Enforce security and best practices  
- Standardize environments across teams  
- Simplify container and cloud deployments  

---

## What is a Stack Template?

A **Stack Template** is a predefined blueprint that describes:

- Application containers
- Required services (DB, cache, queue, etc.)
- Environment variables
- Networking and ports
- Storage volumes
- Scaling and resource limits

Each template is designed to be **ready-to-run** with minimal configuration.

---

## Catalog Structure

Each stack in the catalog includes:

| Field | Description |
|------|-------------|
| **ID** | Unique identifier |
| **Name** | Stack display name |
| **Category** | e.g. Web App, Database, Monitoring |
| **Description** | What the stack does |
| **Version** | Template version |
| **Maintainer** | Team or author | Github link
| **Tags** | Search keywords |
| **Services** | Containers included in the stack |
| **Resources** | CPU / RAM defaults |
| **Volumes** | Persistent storage definitions |
| **Ports** | Exposed service ports |
| **Environment** | Required environment variables |

---

## 📄 Example Registry Template

```yaml
id: postgres
name: postgres
title: PostgreSQL
description: A powerful open-source relational database system known for reliability, robustness, and advanced SQL capabilities.
version: 1.0.0

files:
  - compose.d/postgres.yml

logo: logos/postgres.png
category: Database
popular: true
github: https://www.postgresql.org

tags:
  - sql
  - relational
  - database

```

## 📄 Example Stack Template
```yaml
services:
  postgres:
    image: postgres:16
    ports:
      - "5432:5432"
    environment:
      POSTGRES_DB: appdb
      POSTGRES_USER: appuser
      POSTGRES_PASSWORD: securepassword
    volumes:
      - postgres_data:/var/lib/postgresql/data
    resources:
      cpu: "500m"
      memory: "512Mi"

  adminer:
    image: adminer:latest
    ports:
      - "8080:8080"
    depends_on:
      - postgres

volumes:
  postgres_data:
