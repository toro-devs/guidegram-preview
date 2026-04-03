<div align="center">
  <img src="logo guidegram.png" alt="Guidegram Logo" width="120" />

  # Guidegram

  ### Telegram commerce bot for selling digital products

  [![Made with grammY](https://img.shields.io/badge/Made%20with-grammY-00BFFF?logo=telegram)](https://grammy.dev)
  [![TypeScript](https://img.shields.io/badge/TypeScript-strict-3178C6?logo=typescript&logoColor=white)](https://www.typescriptlang.org)
  [![Payments Ready](https://img.shields.io/badge/Payments-YooKassa%20%7C%20Robokassa-brightgreen)](https://yookassa.ru)
  [![CI/CD](https://img.shields.io/badge/CI%2FCD-automated-blue)](https://github.com)

  
  <img src="https://www.evilsocket.net/images/human-coded.png" height="30px" alt="This project is 100% made by humans."/>

  *Built solo. Shipped to production. End-to-end ownership.*

</div>

---

## What it does

Guidegram lets content creators sell guides, checklists, courses, and any digital files directly through Telegram — no website needed, no third-party platforms, full payment control.

- Buyers browse, pay, and receive files — all within Telegram
- Full paywall: payment link → webhook confirmation → gated delivery
- Discount system and segmented broadcasts for owners

> This is a preview repository. The production codebase is private.

---

## Technical highlights

**Payment integration**
Full paywall logic on top of YooKassa and Robokassa APIs:
- Generate payment links per order
- Handle async webhook confirmation
- Gate content delivery until payment is verified

**Broadcast system**
Segmented messaging — target all users or buyers of a specific product. Built on BullMQ for reliable async job processing.

**Infrastructure**
Fully self-hosted. Automated CI/CD — server provisioning, build pipeline, domain setup, zero-downtime deploys.

---

## Stack

| Layer | Technology |
|---|---|
| Bot framework | grammY |
| Language | TypeScript |
| API layer | Hono |
| Database | PostgreSQL |
| Cache / queues | Redis + BullMQ |
| Deployment | CI/CD, VPS |

---

## Architecture overview

```
User (Telegram)
      │
      ▼
  grammY Bot
      │
      ├── Product catalog
      ├── Payment flow ──► YooKassa / Robokassa
      │         │
      │         └── Webhook handler ──► Verify ──► Deliver product
      │
      ├── Discount engine
      └── Broadcast system ──► BullMQ ──► Segmented delivery
```

---

<div align="center">

Built by [Aleksey Bykovskii](https://www.linkedin.com/in/aybykovskii/) — architecture, implementation, infrastructure, and deployment.

</div>
