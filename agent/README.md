# L7S Agent System

> Internal AI automation backbone for L7S Inc. operations.

## Mission

Automate and manage all aspects of L7S Inc. company operations, including:
- **Client Processing** — onboarding, intake, document collection
- **Billing** — Stripe subscriptions, invoicing, failed payment recovery
- **Compliance** — contract tracking, regulatory deadlines, filing reminders
- **CRM / Customer Service** — pipeline management, support tickets, follow-ups
- **Content Marketing & VSLs** — automated distribution, social posting, email sequences
- **Bookkeeping** — income/expense tracking, P&L reporting, monthly close
- **Overhead Management** — vendor payments, subscriptions, recurring cost tracking

---

## Branded Deliverable Product Lines

These are the three subscription PWA products delivered under the L7S Inc. brand:

### 1. L7S Analytics™
- **Type:** Subscription PWA
- **Purpose:** Data dashboards and business intelligence for clients
- **Delivers:** KPI tracking, revenue dashboards, growth metrics, custom reports
- **Target:** Founders and executives who need visibility into their business performance

### 2. L7S Blueprints™
- **Type:** Subscription PWA
- **Purpose:** Strategic frameworks and business structure documents
- **Delivers:** Business plans, org charts, brand strategy docs, scaling roadmaps, BXBlueprints™
- **Target:** Entrepreneurs structuring or restructuring their operations

### 3. L7S Checklists™
- **Type:** Subscription PWA
- **Purpose:** Compliance, onboarding, and process checklists
- **Delivers:** State filing checklists, employee onboarding flows, SOP templates, compliance calendars
- **Target:** Business owners navigating regulatory requirements or scaling their team

---

## Tech Stack

| Layer | Tool | Purpose |
|-------|------|---------|
| Automation | [n8n](https://n8n.io) (self-hosted) | Workflow orchestration, webhook handling, API glue |
| Scheduling | [Cal.com](https://cal.com/l7sinc) | Client booking, R&R Meetings, hero assignment |
| Billing | [Stripe](https://stripe.com) | Subscriptions, invoicing, payment recovery |
| CRM | [GoHighLevel (GHL)](https://gohighlevel.com) | Pipeline, contacts, follow-up sequences |
| Email | SMTP / Gmail API | Transactional and marketing emails |
| Hosting | GitHub Pages / Cloudflare | Static site delivery |

---

## Directory Structure

```
agent/
├── README.md                        # This file — system overview
├── skills.json                      # Agent skill definitions (all automatable capabilities)
└── workflows/
    ├── client-onboarding.json       # n8n workflow: new client intake automation
    ├── billing-events.json          # n8n workflow: Stripe payment event handling
    ├── compliance-reminders.json    # n8n workflow: deadline and contract alerts
    └── content-distribution.json   # n8n workflow: content posting and VSL sequences
```

---

## Key Contacts

| Role | Email |
|------|-------|
| R&R Meeting Lead | luckieg@l7sinc.com |
| Admin | admin@l7sinc.com |
| Hero Operations | hero@l7sinc.com |

---

## Getting Started

1. **Configure environment variables** — copy `.env.example` to `.env` and fill in keys:
   - `STRIPE_SECRET_KEY`
   - `GHL_API_KEY`
   - `N8N_WEBHOOK_SECRET`
   - `CALCOM_API_KEY`

2. **Import workflows** — in your n8n instance, import JSON files from `workflows/`

3. **Set up Cal.com webhooks** — point `BOOKING_CREATED` / `BOOKING_CANCELLED` events to your n8n instance URL

4. **Connect Stripe webhooks** — point payment events to your n8n Stripe webhook node

5. **Test end-to-end** — make a test booking via `cal.com/l7sinc` and verify the full automation chain fires

---

## The A.B.C.S. Framework (L7S Hero S.O.S.™)

All client interactions are structured around L7S Inc.'s proprietary framework:
- **A** — Awareness (marketing, VSLs, content)
- **B** — Building (onboarding, structuring, compliance)
- **C** — Cashflow (billing, financial reporting, funding)
- **S** — Scaling (CRM, retention, growth automation)

Automations in this agent system map directly to each pillar.
