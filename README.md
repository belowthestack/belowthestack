# Arfa McClain

I build healthcare workflow automation: document intake, payer rules, care-coordination tracking, and
the governance that makes AI safe to put in front of clinical staff. Most recently I shipped
[Novis](https://novis.study), a study platform on web, Windows, iPhone, and iPad.

M.S. Health Administration, Georgia State University. B.S. Biology, Georgia Gwinnett College.
Former medical scribe and safety-net clinic volunteer, and nine years managing operations for a
small service business.

---

## Healthcare automation

Builds below use synthetic data. No PHI, and nothing here is a production EHR integration.

**Clinical lab fax intake** ([live demo](https://arfa-lab-ops.pages.dev/?live=0))
Prototyped in Make.com, rebuilt on self-hosted n8n with Claude on AWS Bedrock and NocoDB (SQL) so
patient data only touches BAA-eligible services. AI vision reads faxed orders into structured fields
with confidence scores, low-confidence reads go to a human review queue, idempotency keys block
duplicate orders, failures land in a dead-letter queue with alerts, and every step writes to an
append-only audit log with no medical values. Custom AWS SigV4 request signing inside n8n; a Python
harness proves a replayed fax creates exactly one order.

**ABA operations layer** ([live demo](https://aba-ops-layer.pages.dev/app.html))
Deterministic, explainable rules (not AI) on top of EHR exports: authorization unit-burn
forecasting, BACB supervision monitoring, waitlist-to-provider matching, cancellation backfill, and
payer contract tracking.

**[aba-note-risk-checker](https://github.com/belowthestack/aba-note-risk-checker)** ([live demo](https://safetylayer-mvp.pages.dev))
Payer-aware rules engine that flags ABA session-note documentation risk before the BCBA signs. A
self-directed red team disproved the original premise, and the tool was rebuilt around the finding.

**Chronic care management engine**
Eight n8n workflows that read problem lists and coverage over FHIR, track monthly care minutes, and
block billing until consent, a signed care plan, and the time requirement are met. AI time is never
billable, and a person approves every claim.

**[epic-result-triage](https://github.com/belowthestack/epic-result-triage)**
SMART-on-FHIR worklist tested against Epic's public sandbox: OAuth2 with PKCE, FHIR R4 reads,
explainable ranking, a mandatory human approval step, and a SHA-256 audit chain.

**[voice-ops-core](https://github.com/belowthestack/voice-ops-core)**
Governance layer for healthcare voice AI: a tool-policy gateway that refuses unsafe tool calls
before any side effect, an append-only audit trail, and an evaluation harness.

**[fhir-ops-layer](https://github.com/belowthestack/fhir-ops-layer)**
Standards-based FHIR R4 connector: recall scoring, US Core conformance pre-check, and SMART Backend
Services against public sandboxes.

---

## Shipped products

**[Novis](https://novis.study)** ([downloads](https://github.com/belowthestack/novis-downloads))
Study platform with paid plans, live on the App Store and the web. OCR and document AI for PDFs and
handwriting, FSRS spaced repetition, Postgres with row-level security, verified Stripe webhooks,
AI routing with provider failover, validators on AI output, and 8,000+ automated tests. Source is
private.

**Gym CRM and lead automation** (in daily use, source private)
Replaced a paid CRM with a custom React + TypeScript + MySQL app and n8n automations: Facebook Lead
Ads API and website webhooks, rule-based routing with logged decisions, Telegram and email alerts,
nurture sequences, and signature-tracked waivers with approved follow-ups.

---

## How I build

- **Human in the loop on anything clinical or financial.** AI drafts; rules decide; people approve.
- **Auditable by default.** Append-only logs, idempotency keys, dead-letter queues, alerts on failure.
- **BAA and PHI boundaries first.** Patient data only goes to BAA-covered services; secrets stay out of git.
- **Documented for handoff.** Runbooks, build logs, and plain-language guides for staff.

## Stack

TypeScript · JavaScript · React · SQL (Postgres, MySQL) · Python · n8n · FHIR R4 · SMART-on-FHIR ·
AWS Bedrock · Supabase · Stripe · Cloudflare · Vercel · DigitalOcean

## Contact

[LinkedIn](https://www.linkedin.com/in/arfa-mcclain/) · info@arfaconsults.com
