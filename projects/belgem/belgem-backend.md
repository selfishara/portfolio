# 💎 Belgem Backend

Backend of the **Belgem ERP system** — a business management platform developed with Java 17, Spring Boot, and PostgreSQL, following a modular hexagonal architecture.

> **My role:** Co-technical lead and backend developer. I co-led a team of 7 developers (5 backend, 2 frontend), contributed to architectural decisions, implemented core backend modules, and coordinated development workflows alongside the other team lead.

---

## Tech Stack

| Layer | Technology | Notes |
|---|---|---|
| Backend | Java 17 + Spring Boot | Main framework |
| Security | Spring Security + JWT | Token-based auth |
| Database | PostgreSQL + Supabase | Local persistence + remote collaboration |
| ORM | JPA / Hibernate | Data layer |
| Build | Maven | Dependency management |
| Testing | JUnit | Automated testing |
| CI/CD | GitHub Actions | 71 pipeline runs, all passing |
| Version control | GitHub | Branch-based workflow with PRs |

---

## Architecture

The project follows a **modular monolith** based on **hexagonal (clean) architecture** principles — domain logic has zero external dependencies, adapters handle all I/O.

![Hexagonal Architecture](architecture.png)

---

## Database Model

PostgreSQL schema `v1` with core ERP entities.

![Data Model](data-model.png)

---

## CI/CD Pipeline

71 automated pipeline runs on GitHub Actions — triggered on every push and pull request, including feature branches.

![CI/CD Pipeline](ci-pipeline.png)

---

## Key Features

- JWT-based authentication and authorization via Spring Security
- RESTful API design with structured endpoints per business module
- Clean separation between domain logic and infrastructure
- PostgreSQL integration with JPA/Hibernate for data persistence
- CI/CD pipeline with GitHub Actions — 71 runs, all green
- Feature branch workflow with pull request reviews

---

## My Contributions

- Co-led technical direction alongside the other team lead
- Implemented backend modules: business logic, service layer, REST controllers
- Contributed to architecture decisions: module structure, layering, naming conventions
- Coordinated tasks and pull request reviews across the backend team
- Set up and maintained development workflow on GitHub

---

## Team

7-person cross-functional team: 5 backend developers (DAM) + 2 frontend developers (DAW), co-led by Alfredo Noriega and Sara Martínez.

---

## Repository

[github.com/Alfre-dev2004/Belgem-Backend](https://github.com/Alfre-dev2004/Belgem-Backend)
