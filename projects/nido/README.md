# 🏠 Nido — vivienda y dinero para gente joven

> **Estado:** 🟡 Sprint 0 · Descubrimiento · *(nombre provisional)*

Nido ayuda a gente joven a **encontrar piso sin que la estafen** y a **entender y organizar su dinero** para poder independizarse.
Es una app **móvil y web**: Android, iOS y web con Kotlin Multiplatform, y backend en Spring Boot.

---

## 🎯 El problema

Independizarse siendo joven en España combina dos problemas que se alimentan entre sí:

1. **Vivienda**: alquileres que se comen buena parte del sueldo, mucha competencia por cada piso y **estafas en anuncios** (pagar la señal sin haber visto el piso, propietarios "en el extranjero", anuncios clonados) y contratos con cláusulas abusivas que casi nadie revisa.
2. **Dinero**: primeros sueldos, nóminas que no se entienden, poca cultura financiera y ninguna herramienta que responda a *"¿me puedo permitir este piso?"*

> 📌 Las cifras concretas (esfuerzo salarial, edad de emancipación, volumen de estafas) se investigan en el **Sprint 0** ([spikes S0-1 y S0-2](docs/backlog.md#sprint-0--descubrimiento)) y se citan aquí con sus fuentes.

## 💡 La propuesta

| Módulo | Qué hace | Tecnología clave |
|---|---|---|
| 💸 **Mi dinero** | Ingresos, gastos, objetivo de ahorro (fianza, mudanza) y **% de esfuerzo** del alquiler | Backend con lógica de dominio |
| 🚩 **Detector de estafas** | Pegas un anuncio o una URL y recibes una puntuación de riesgo con sus motivos | IA con salida estructurada y reglas |
| 📄 **Revisor de contratos** | Subes el contrato y te marca las cláusulas dudosas según la LAU | RAG con pgvector |
| 🧾 **Explicador de nómina** | Te explica la nómina línea a línea (IRPF, Seguridad Social) | IA y privacidad desde el diseño |
| 🎁 **Ayudas** | Ayudas al alquiler a las que podrías optar | Datos abiertos y APIs |

## 🧱 Arquitectura prevista

```
 Android ─┐
 iOS ─────┼── Compose Multiplatform (KMP) ──HTTPS + OAuth2/OIDC (PKCE)──▶ API Spring Boot (hexagonal)
 Web ─────┘                                                              │
                                                                         ├── PostgreSQL + pgvector
                                                                         ├── API de Claude (IA)
                                                                         └── APIs de datos abiertos
```

Decisiones de arquitectura documentadas en [`docs/adr`](docs/adr).

## 🔐 La seguridad como eje del proyecto

Nido trata datos sensibles (nóminas, DNI, contratos), así que la seguridad es una pieza central:

- OAuth2/OIDC con PKCE, tokens de vida corta y rotación de *refresh tokens*
- Modelo de amenazas STRIDE por cada módulo
- OWASP Top 10 y **OWASP Top 10 para aplicaciones LLM** (inyección de prompts a través de contratos o anuncios)
- Cumplimiento del RGPD: minimización de datos, cifrado y derecho al olvido
- Análisis estático, escaneo de dependencias y de secretos en el CI

## 🗂️ Cómo se trabaja

- **Metodología:** Scrum adaptado a una persona, con sprints de 2 semanas
- **Backlog:** GitHub Projects ([guía de configuración](docs/github-projects-guide.md))
- **Bitácora:** [diario del proceso](docs/bitacora.md), con capturas para LinkedIn
- **IA en el desarrollo:** Claude Code con `CLAUDE.md`, skills propias y subagentes

## 📚 Documentación

- [Backlog inicial y épicas](docs/backlog.md)
- [Guía de GitHub Projects](docs/github-projects-guide.md)
- [ADRs (decisiones de arquitectura)](docs/adr)
- [Bitácora del proceso](docs/bitacora.md)
