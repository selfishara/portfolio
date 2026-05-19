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
| CI/CD | GitHub Actions | Continuous integration pipeline |
| Version control | GitHub | Central repo with branch-based workflow |

---

## Architecture

The project follows a **modular monolith** structure based on **hexagonal (clean) architecture** principles, separating domain logic, application services, and infrastructure concerns.

```
src/
└── main/
    └── java/
        └── com.belgem/
            ├── domain/          # Business entities and rules
            ├── application/     # Use cases and services
            ├── infrastructure/  # Controllers, repositories, config
            │   ├── controller/
            │   ├── repository/
            │   └── security/
            └── BelgemApplication.java
```

---

## Key Features

- JWT-based authentication and authorization via Spring Security
- RESTful API design with structured endpoints per business module
- Clean separation between domain logic and infrastructure
- PostgreSQL integration with JPA/Hibernate for data persistence
- CI/CD pipeline with GitHub Actions for automated build and integration checks
- Modular structure enabling independent development across team members

---

## My Contributions

- Co-led technical direction alongside the other team lead
- Implemented backend modules including business logic, service layer, and REST controllers
- Contributed to architecture decisions: module structure, layering approach, naming conventions
- Coordinated tasks and pull request reviews across the backend team
- Set up and maintained the development workflow on GitHub (branches, PRs, CI)

---

## Team

7-person cross-functional team: 5 backend developers (DAM) + 2 frontend developers (DAW), co-led by Alfredo Noriega and Sara Martínez.

---

## What to look at

- **`src/`** — full project structure showing hexagonal layering
- **`.github/workflows/`** — CI/CD pipeline configuration
- **`docs/`** — additional project documentation

---

## Repository

[github.com/Alfre-dev2004/Belgem-Backend](https://github.com/Alfre-dev2004/Belgem-Backend)

---

## Screenshots

> *(Add here: Postman/Swagger endpoint list, IntelliJ project structure view, GitHub Actions pipeline passing)*
