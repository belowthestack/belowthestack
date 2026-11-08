# Arfa McClain

I build software and workflow automation with AI coding agents. I shipped [Novis](https://novis.study),
a study platform on web, Windows, iPhone, and iPad, and the CRM my gym uses every day. I also build
healthcare automation: document intake, payer rules, care-coordination tracking, and the governance
that makes AI safe to put in front of clinical staff.

M.S. Health Administration, Georgia State University. B.S. Biology, Georgia Gwinnett College.
Former medical scribe and safety-net clinic volunteer, and nine years managing operations for a
small service business.

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
nurture sequences, Stripe memberships and recurring payments, and signature-tracked waivers with
approved follow-ups.

---

## Healthcare automation

I built these to learn how to combine healthcare compliance and AI governance with AI coding agents:
where patient data is allowed to go, what has to be audited, and what a person must approve. They are
learning builds and pilots on synthetic data, so the focus is the architecture and the controls, not
polished UI. No PHI, and nothing here is a production EHR integration.

**Fax intake and denial routing** ([source](https://github.com/belowthestack/fax-denial-routing); [live dashboard](https://fax-denial-routing.pages.dev/); [video walkthrough](https://youtu.be/S2JZgYhIlCU?t=19))
Started as a fax intake pilot for a clinical lab (prototyped in Make.com, rebuilt on n8n), now rebuilt as a
pilot on synthetic payer letters. It reads each faxed letter, decides whether it is an approval, a full
denial, a partial denial, or not a payer letter, and routes denials to work queues by reason. Two Claude
models on AWS Bedrock read each page independently and must agree, a deterministic rules layer makes every
decision and cites the rule that fired, anything uncertain goes to a person, and nothing is sent until a
person approves it. Duplicate faxes are blocked before any model call, failures are kept and retried, and
an append-only audit log stores no medical values. Tests replay real captured model outputs.

**ABA operations layer**
Deterministic, explainable rules (not AI) on top of EHR exports: authorization unit-burn
forecasting, BACB supervision monitoring, waitlist-to-provider matching, cancellation backfill, and
payer contract tracking.

**[aba-note-risk-checker](https://github.com/belowthestack/aba-note-risk-checker)**
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
