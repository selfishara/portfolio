# 📋 Initial backlog

This document is the **source** of the backlog: each story becomes a GitHub issue in the Project.
Story format: *As a [user], I want [action] so that [benefit]*, plus acceptance criteria (AC).
Every story marked P0 or P1 gets a **spec** in [`specs/`](../specs) before any code is written.

**Size:** XS (<1h) · S (2–3h) · M (half a day) · L (1–2 days) · XL (split it)
**Priority:** P0 (MVP) · P1 (right after MVP) · P2 (later)

---

## Sprint 0 · Discovery

Spikes are time-boxed research tasks. Their output is a document, not code.

| ID | Spike | Output | Size |
|---|---|---|---|
| S0-1 | Youth housing data in Spain: rent-to-income ratio, emancipation, prices | `docs/research/housing.md` with sources | M |
| S0-2 | Rental scam patterns (Police, INCIBE, OCU) | `docs/research/scams.md` → red flags | M |
| S0-3 | APIs & data map: Idealista API, Cadastre, rental price index, INE, grants | `docs/research/apis.md` (access, limits, licence) | M |
| S0-4 | Identity provider: Keycloak vs Supabase Auth vs Spring Authorization Server | ADR-0002 | M |
| S0-5 | Competitor benchmark (portals, finance apps) | Comparison table | S |
| S0-6 | User personas & value proposition | `docs/personas.md` | S |
| S0-7 | Define the MVP and lock the scope | Update this backlog | S |
| S0-8 | Repo + GitHub Projects + issue templates | Board screenshot 📸 | S |

---

## Epics

### EPIC-0 · Platform & DevOps · P0
- **US-0.1** As a developer, I want a monorepo with the Spring Boot backend and the KMP app so that I work in a single place.
  - AC: builds locally · README with run instructions
- **US-0.2** As a developer, I want Docker Compose (API + Postgres/pgvector + IdP) so that the environment starts with one command.
- **US-0.3** As a developer, I want CI (build, tests, lint, dependency and secret scanning) so that broken or insecure code never gets merged.
- **US-0.4** As a developer, I want a `CLAUDE.md` and custom skills so that the AI assistant follows my conventions.

### EPIC-1 · Account & security · P0
- **US-1.1** As a user, I want to sign in with Google so that I don't need another password.
  - AC: OIDC + PKCE on mobile and web · backend validates JWTs as a resource server
- **US-1.2** As a user, I want to delete my account and all my data (GDPR right to erasure).
- **US-1.3** As a developer, I want a STRIDE threat model of the system so that I can prioritise controls.
- **US-1.4** As the system, I want rate limiting and security headers so that abuse is mitigated.

### EPIC-2 · My money · P0
- **US-2.1** As a user, I want to record my monthly net income so that I know what rent I can afford.
- **US-2.2** As a user, I want to record fixed expenses by category so that I see what's left each month.
- **US-2.3** As a user, I want to see the **rent-to-income ratio** of a rent with a traffic light so that I decide with data.
  - AC: green < 30% · amber 30–40% · red > 40% (configurable thresholds)
- **US-2.4** As a user, I want a savings goal (deposit, moving, furniture) with progress tracking.

### EPIC-3 · Scam detector · P0
- **US-3.1** As a user, I want to paste a listing and get a risk score with reasons.
  - AC: JSON response validated against a schema · reasons explained · never presented as an absolute verdict
- **US-3.2** As the system, I want deterministic rules (abnormal price, upfront payment, WhatsApp-only contact) that complement the AI.
- **US-3.3** As a developer, I want the prompt protected against injection inside the listing (OWASP LLM01).
- **US-3.4** As a developer, I want a test dataset of legit and scam listings so that I can measure precision and recall.

### EPIC-4 · Contract reviewer · P1
- **US-4.1** As a user, I want to upload my lease PDF and see dubious clauses with a reference to the LAU article.
- **US-4.2** As the system, I want the LAU indexed in pgvector (RAG) so that answers are grounded.
- **US-4.3** As a user, I want my contract not to be stored unless I ask for it (privacy).

### EPIC-5 · Payslip explainer · P1
- **US-5.1** As a user, I want to upload my payslip and get every item explained.
- **US-5.2** As the system, I want to anonymise personal data (ID number, social security number, IBAN) before sending it to the model.

### EPIC-6 · Grants · P2
- **US-6.1** As a user, I want to know which rental grants I may qualify for based on age, income and region.

---

## 🎯 MVP (proposal, confirmed in S0-7)
EPIC-0 + EPIC-1 + EPIC-2 + EPIC-3: **money + scam detector, with serious authentication**.
