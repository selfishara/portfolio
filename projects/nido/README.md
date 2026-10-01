# 🏠 Nido — housing & money for young people

> **Status:** 🟡 Sprint 0 · Discovery · *(working name)*

Nido helps young people **find a place to rent without getting scammed** and **understand and organise their money** so they can move out.
**Mobile + web** app (Android · iOS · Web) built with Kotlin Multiplatform and a Spring Boot backend.

---

## 🎯 The problem

Moving out as a young person in Spain mixes two problems that feed each other:

1. **Housing**: rents that eat a large share of your salary, fierce competition for each flat, **rental scams** (pay the deposit before seeing the flat, landlord "living abroad", cloned listings) and contracts with abusive clauses nobody reviews.
2. **Money**: first salaries, payslips nobody understands, little financial literacy and no tool that answers *"can I afford this flat?"*

> 📌 Specific figures (rent-to-income ratio, emancipation age, scam volume) are researched in **Sprint 0** ([spikes S0-1 and S0-2](docs/backlog.md#sprint-0--discovery)) and cited here with sources.

## 💡 The proposal

| Module | What it does | Key tech |
|---|---|---|
| 💸 **My money** | Income, expenses, savings goal (deposit, moving costs) and **rent-to-income ratio** | Backend domain logic |
| 🚩 **Scam detector** | Paste a listing or URL → risk score with reasons | AI with structured output + rules |
| 📄 **Contract reviewer** | Upload your lease → flags dubious clauses under Spanish tenancy law (LAU) | RAG with pgvector |
| 🧾 **Payslip explainer** | Explains your payslip line by line (income tax, social security) | AI + privacy by design |
| 🎁 **Grants** | Rental grants you may qualify for | Open data / APIs |

## 🧱 Planned architecture

```
 Android ─┐
 iOS ─────┼── Compose Multiplatform (KMP) ──HTTPS + OAuth2/OIDC (PKCE)──▶ Spring Boot API (hexagonal)
 Web ─────┘                                                              │
                                                                         ├── PostgreSQL + pgvector
                                                                         ├── Claude API (AI)
                                                                         └── Open data APIs
```

Architecture decisions live in [`docs/adr`](docs/adr).

## 🔐 Security at the core

Nido handles sensitive data (payslips, IDs, contracts), so security is a central piece of the design:

- OAuth2/OIDC with PKCE, short-lived tokens, refresh token rotation
- STRIDE threat model per module
- OWASP Top 10 + **OWASP Top 10 for LLM applications** (prompt injection via contracts or listings)
- GDPR: data minimisation, encryption, right to erasure
- SAST, dependency scanning and secret scanning in CI

## 🗂️ How it's built

- **Methodology:** Scrum adapted for a solo developer · 2-week sprints
- **Spec-Driven Development:** every feature starts as a spec → [`specs/`](specs)
- **Backlog:** GitHub Projects ([setup guide](docs/github-projects-guide.md))
- **Process log:** [process log](docs/process-log.md) with screenshots
- **Learning notes:** theory + practice of every concept applied → [`docs/learning`](docs/learning)
- **AI-assisted dev:** Claude Code with `CLAUDE.md`, custom skills and subagents

## 🛠️ Tooling

| Tool | Used for |
|---|---|
| **IntelliJ IDEA** | Backend (Java · Spring Boot · Gradle · DB tools) |
| **Android Studio** | KMP client, Android emulator |
| **Terminal** | Git, Docker, Gradle |
| **VS Code** *(optional)* | Quick edits to Markdown/YAML |

## 📚 Docs

- [Initial backlog & epics](docs/backlog.md)
- [GitHub Projects guide](docs/github-projects-guide.md)
- [Specs (SDD)](specs)
- [ADRs](docs/adr)
- [Process log](docs/process-log.md)
- [Learning notes](docs/learning)
