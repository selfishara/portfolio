# ADR-0001 · Base tech stack

- **Status:** Proposed
- **Date:** 2026-10-01

## Context
Nido must run on **mobile (Android/iOS) and web**, handle sensitive data and integrate AI. It's a solo project meant to grow in backend, AI and cybersecurity, building on previous experience with Spring Boot, hexagonal architecture and KMP.

## Decision
| Layer | Choice | Why |
|---|---|---|
| Backend | Java 21 + Spring Boot 3, hexagonal architecture | Already practised at Belgem; mature security ecosystem (Spring Security) |
| Client | Kotlin Multiplatform + Compose Multiplatform (Android, iOS, Web/Wasm) | One codebase for mobile and web; prior experience from GymSpot Lite |
| Database | PostgreSQL + pgvector | Relational data and RAG embeddings in the same engine |
| AI | Claude API (structured output, tool use) | Strong at legal-text analysis and reliable JSON |
| Auth | OAuth2/OIDC + PKCE (IdP decided in ADR-0002) | Industry standard, and a learning goal |
| Infra | Docker Compose + GitHub Actions | Reproducible, and what job offers ask for |
| IDE | IntelliJ IDEA (backend) + Android Studio (KMP client) | Best-in-class tooling for each side |

## Alternatives considered
- **Flutter / React Native**: they don't reuse the Kotlin experience.
- **Supabase as the whole backend**: fast, but hides exactly the backend and security work this project wants to learn.
- **Microservices from day one**: too complex for the MVP. Start with a modular monolith.

## Consequences
- ➕ A single language (Kotlin) on the client; a Java backend strengthens the profile.
- ➖ Compose for Web/Wasm is less mature than on Android: validate early (Sprint 1 risk).
- ➖ AI API cost must be controlled (caching, per-user limits).
