# 📐 Spec-Driven Development (SDD)

## Theory

**What:** the **specification** is the main artefact. Code is derived from it, and the spec is kept up to date.
Instead of "idea → code", the flow is:

```
Spec (what & why) → Plan (how) → Tasks (steps) → Implement (tests first) → Validate against the spec
```

**Why it's trending now:** AI coding agents produce much better code when they get a precise spec instead of a vague prompt. The spec becomes the shared context between you, the agent and future you. Tools like GitHub Spec Kit or Kiro popularised this workflow.

**Key ideas:**
| Concept | Meaning |
|---|---|
| **Constitution** | Non-negotiable project principles that every spec and plan must respect |
| **Spec** | *What* and *why*, with no technology: user stories, acceptance criteria, edge cases |
| **Plan** | *How*: architecture, data model, API contract, security, test strategy |
| **Tasks** | Small ordered steps, each one verifiable |
| **Clarifications** | Open questions are marked `[NEEDS CLARIFICATION]` and are never guessed |

**How it relates to what you already know:**
- **User story → spec:** the spec is a user story that grew up. It adds edge cases, rules and explicit acceptance criteria.
- **Acceptance criteria → tests:** writing them as *Given / When / Then* lets them become tests directly (BDD, TDD).
- **Plan ↔ ADR:** if the plan makes an important architectural decision, it gets its own ADR.

## Practice in Nido
- Every P0/P1 story gets a folder in [`specs/`](../../specs): `NNN-feature-name/{spec,plan,tasks}.md`.
- [`specs/constitution.md`](../../specs/constitution.md) holds the principles.
- Workflow per story: write the spec → review it (with Claude as a critic) → write the plan → split into tasks → TDD → PR that links the spec.
- Later on: a custom Claude skill (`/spec`) that generates the skeleton and checks the spec against the constitution.

## 🧠 My own words
> *Why write the spec before the code? What goes in the spec and what goes in the plan?*
