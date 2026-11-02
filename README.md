# Arfa McClain

Building [Novis](https://novis.study), a study platform for busy students on web, Windows, iPhone
and iPad. It plans each day up to an exam, tutors, and builds flashcards from your own material.

Before Novis, I built healthcare operations and interoperability projects: intake and scheduling
workflows, FHIR data exchange, and the governance and audit controls that make automation safe to
put in front of clinical staff.

M.S. Health Administration, Georgia State University. B.S. Biology, Georgia Gwinnett College.
Previously a medical scribe and a clinical volunteer at a nonprofit safety-net clinic, which is
where the interest in operations started.

---

## Building now

**[Novis](https://novis.study)** ([downloads](https://github.com/belowthestack/novis-downloads))
Shipped study application with paid plans. Web, Electron desktop, and iPhone and iPad apps on the
App Store. Supabase, Stripe, spaced repetition, AI-generated decks, and a 3D knowledge graph.
Scoped, built, deployed, and security red-teamed solo. Source is private.

---

## Earlier work: healthcare operations

Every project in this section uses synthetic data on public sandboxes. No PHI, and nothing here
is a production EHR integration.

**[epic-result-triage](https://github.com/belowthestack/epic-result-triage)**
SMART-on-FHIR result worklist tested against Epic's public sandbox. OAuth2 with PKCE,
authenticated FHIR R4 reads, explainable ranking of clinical results, a mandatory human approval
step, and a SHA-256 audit chain.

**[voice-ops-core](https://github.com/belowthestack/voice-ops-core)**
Governance and audit layer for healthcare voice AI. A tool-policy gateway that validates and
refuses unsafe model tool calls before any side effect, an append-only audit trail, and an
evaluation harness.

**[fhir-ops-layer](https://github.com/belowthestack/fhir-ops-layer)**
Standards-based FHIR R4 connector. Recall and retention scoring, US Core conformance pre-check,
and SMART Backend Services against public sandboxes.

**[aba-note-risk-checker](https://github.com/belowthestack/aba-note-risk-checker)**
Single-page, no-backend rules engine that flags payer-specific documentation risk in ABA session
notes. A self-directed red team disproved the original premise, and both the tool and its
positioning were rebuilt around the corrected finding.

**[safe-scraper](https://github.com/belowthestack/safe-scraper)**
Web scraper with built-in credibility-risk detection for signal manipulation.

### How I built these

- **Human in the loop on anything clinical.** The systems surface eligibility, missing
  documentation, and risk. Licensed people stay the decision-makers.
- **Auditable by default.** Append-only logging, idempotency keys, and a real approval step
  rather than a log line after the fact.
- **BAA and PHI boundaries checked before a tool goes near patient data**, and stated plainly
  when a tool is demo-only.
- **Documented for handoff.** A system nobody on staff can operate is a system that quietly dies.

---

## Stack

Python · JavaScript / TypeScript · SQL · FHIR R4 · US Core · SMART-on-FHIR · HL7 v2 · n8n ·
Supabase · Electron · Cloudflare Workers

## Contact

[LinkedIn](https://www.linkedin.com/in/arfa-mcclain/) · info@arfaconsults.com
