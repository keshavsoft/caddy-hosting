# Caddy Hosting Ecosystem

[![GitHub Pages](https://img.shields.io/badge/docs-GitHub_Pages-blue)](https://keshavsoft.github.io/caddy-hosting/)
[![KeshavSoft](https://img.shields.io/badge/org-KeshavSoft-purple)](https://github.com/keshavsoft)
[![License: ISC](https://img.shields.io/badge/License-ISC-blue.svg)](LICENSE)
[![Caddy](https://img.shields.io/badge/Caddy-v2.8+-black?logo=caddy)](https://caddyserver.com)

> **The unified portal and architecture guide for the KeshavSoft native Caddy JSON hosting ecosystem.**

---

## 🌐 Live Portal

Explore the interactive ecosystem dashboard and architecture visualizer:  
👉 **[https://keshavsoft.github.io/caddy-hosting/](https://keshavsoft.github.io/caddy-hosting/)**

---

## 🧩 The KeshavSoft Caddy Toolkit

Instead of maintaining brittle monolithic scripts or wrestling with manual Caddyfile syntax, KeshavSoft splits Caddy cloud hosting into single-purpose, focused micro-tools:

| Tool | Role | Registry / Link | Quick Command |
| :--- | :--- | :--- | :--- |
| **[`caddy-cli`](https://github.com/keshavsoft/caddy-cli)** | Observability & Inspection | [![npm](https://img.shields.io/npm/v/caddy-cli.svg)](https://www.npmjs.com/package/caddy-cli) | `npx caddy-cli -p` |
| **[`caddy-template`](https://github.com/keshavsoft/caddy-template)** | Route Blueprint Generation | [![npm](https://img.shields.io/npm/v/caddy-template.svg)](https://www.npmjs.com/package/caddy-template) | `npx caddy-template proxy <host> <port>` |
| **[`caddy-hosting`](https://github.com/keshavsoft/caddy-hosting)** | Ecosystem Hub & Guide | [GitHub Pages Portal](https://keshavsoft.github.io/caddy-hosting/) | Gateway Site |
| **[`appointment-notifier`](https://github.com/keshavsoft/appointment-notifier)** | Real-world Production App | [GitHub Repo](https://github.com/keshavsoft/appointment-notifier) | Real-time WebSocket clinic calling |

---

## 🏗️ Architecture & 3-Step Hosting Workflow

```
                             ┌─────────────────────────────────┐
                             │       caddy-hosting (Hub)       │
                             │  The Architecture & Ecosystem   │
                             └───────────────┬─────────────────┘
                                             │
             ┌───────────────────────────────┴──────────────────────────────┐
             ▼                                                              ▼
 ┌────────────────────────┐                                     ┌────────────────────────┐
 │       caddy-cli        │                                     │     caddy-template     │
 │  Inspection / Port Map │                                     │  JSON Route Generator  │
 └───────────┬────────────┘                                     └───────────┬────────────┘
             │                                                              │
             └───────────────────────────────┬──────────────────────────────┘
                                             ▼
                             ┌─────────────────────────────────┐
                             │       Production VPS Caddy      │
                             │   (/etc/caddy/caddy.json)       │
                             └─────────────────────────────────┘
```

### 1. Inspect Occupied Ports
```bash
npx caddy-cli -p
```
Discovers all ports dialed by Caddy (`3001`, `3025`, `8080`, `9010`, `9328`...) and reveals open port slots (e.g., `3000`).

### 2. Generate Route Blueprint
```bash
npx caddy-template proxy appointment.keshavsoft.com 3000
```
Produces a pristine, schema-compliant Caddy JSON route block for reverse proxying HTTP and WebSockets.

### 3. Hot Reload Caddy (Zero Downtime)
```bash
caddy reload --config /etc/caddy/caddy.json
```
or push dynamically via Caddy's RESTful Admin API (`http://localhost:2019/config/...`) without terminating active WebSocket sessions.

---

## 🎯 Why Standardize on Native Caddy JSON?

- **Zero Downtime**: Caddy dynamically reloads JSON configurations in-memory without restarting the server or dropping connections.
- **Programmatic Control**: Native JSON allows CLI tools and automation pipelines to safely read, query, and inject routes.
- **Full Module Access**: Every Caddy feature is natively defined in JSON.

---

## 📚 Official Upstream References

- [Caddyserver Official Website](https://caddyserver.com/)
- [Caddy Architecture Overview](https://caddyserver.com/docs/architecture)
- [Caddy JSON Structure Documentation](https://caddyserver.com/docs/json/)
- [Caddy Admin API Reference](https://caddyserver.com/docs/api)
- [Caddy Reverse Proxy Module](https://caddyserver.com/docs/modules/http.handlers.reverse_proxy)

---

## 📄 License

ISC © [KeshavSoft](https://github.com/keshavsoft)
