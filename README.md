# ⚡ Enterprise Inbound Lead Sanitizer & Resilient Outreach Engine

An enterprise-grade n8n inbound pipeline built for sub-5-second speed-to-lead execution, defensive data cleansing, hybrid AI qualification, and automated multi-channel routing.

![Inbound Lead Sanitizer Workflow Architecture](Inbound-Lead-Sanitizer-Engine.png)

---

## 🎯 Business ROI & Prevention
* **⚡ Sub-5-Second Speed-to-Lead:** Triggers instant Slack VIP alerts and automated WhatsApp engagement to capture high-intent buyers before competitors reply.
* **🛡️ Defensive CRM Hygiene:** Filters out bots, honeypots, disposable email domains, and invalid phone formats before touching HubSpot records.
* **🧠 Hybrid Qualification:** Combines deterministic business rules (budget, company size) with Gemini AI intent and urgency scoring (`HIGH`, `MED`, `LOW`).
* **🚨 Production Resilience:** Centralized audit logs in Airtable and engine-level incident monitoring ensure zero data loss during API downtime.

---

## 🏗️ Workflow Architecture

```text
[ Incoming Webhook ] ──► [ Phase 1: Ingestion & Security ] ──( Spam/Bot )──► [ Phase 6: Security Audit Log ]
                                  │
                                  ▼
                        [ Phase 2: CRM & AI Triage ] (HubSpot + Gemini AI)
                                  │
                                  ▼
                        [ Phase 3: Airtable Audit Persistence ]
                                  │
                                  ▼
                        [ Multi-Tier Score Router ]
                           ├── Score ≥ 70 (HOT)  ──► [ Phase 4: Slack VIP + WhatsApp + Sales Call ]
                           └── Score < 70 (WARM) ──► [ Phase 5: Gmail Auto-Reply + HubSpot Queue ]


🛠️ Key Technical Features
Phase 1: Ingestion, Security & Deep Data Cleansing
Honeypot Validation: Silently captures and isolates automated form spam via Inbound Gatekeeper.

Data Sanitization: Trims whitespace and enforces international E.164 phone formatting.

Spam Domain Lookup: Real-time checking against disposable and high-risk email domains.

Phase 2: CRM Sync & Hybrid AI Scoring
HubSpot Integration: Upserts contact profiles based on clean email and phone metrics.

Deterministic Scoring Matrix: Calculates base fit using hard lead criteria (Budget, Company Size, Role).

Gemini AI Intent Analyzer: Evaluates unstructured lead messages to output structured JSON intent, urgency levels, and executive summaries.

Phase 3 & 6: Audit Logging & Security Isolation
Airtable Audit Trail: Writes permanent execution logs for both qualified and low-priority paths.

Security Isolation: Logs honeypot triggers and invalid submissions to Airtable - Log Bot, Spam & Incomplete Leads away from primary CRM pipelines.

Phase 4 & 5: Multi-Tier Sales Routing
Hot Leads (Score ≥ 70): Pushes rich-formatted notifications to #sales-hot-leads in Slack, queues phone tasks, and initiates instant WhatsApp outreach.

Warm / Cold Leads (Score < 70): Triggers auto-reply emails, schedules secondary sales calls, and tags contacts in HubSpot for nurture campaigns.

🚀 Setup & Installation
Import Workflow:

Download Inbound Lead Sanitizer, Multi-Criteria Scoring & Resilient Outreach Engine.json.

Open n8n and go to Workflows > Import from File.

Configure Credentials:

HubSpot API: Private App Access Token with contact read/write permissions.

Google Gemini API: API Key for structured output generation.

Airtable / Slack / WhatsApp / Gmail: Authorized service connections.

Activate:

Set workflow status to Active and link your webhook entry point to your lead capture form.
