# ADR-0001 · Stack tecnológico base

- **Estado:** Propuesta
- **Fecha:** 2026-10-01

## Contexto
Nido tiene que funcionar en **móvil (Android/iOS) y web**, tratar datos sensibles e integrar IA. Es un proyecto individual para crecer en backend, IA y ciberseguridad, aprovechando la experiencia previa en Spring Boot, arquitectura hexagonal y KMP.

## Decisión
| Capa | Elección | Motivo |
|---|---|---|
| Backend | Java 21 + Spring Boot 3, arquitectura hexagonal | Dominio ya practicado en Belgem y un ecosistema de seguridad maduro (Spring Security) |
| Cliente | Kotlin Multiplatform + Compose Multiplatform (Android, iOS y Web/Wasm) | Un único código para móvil y web; base previa en GymSpot Lite |
| Base de datos | PostgreSQL + pgvector | Datos relacionales y embeddings para RAG en el mismo motor |
| IA | API de Claude (salida estructurada y *tool use*) | Calidad en el análisis de textos legales y JSON fiable |
| Autenticación | OAuth2/OIDC con PKCE (el proveedor de identidad se decide en ADR-0002) | Estándar del sector y lo que se quiere aprender |
| Infraestructura | Docker Compose + GitHub Actions | Reproducible, y es lo que piden las ofertas |

## Alternativas descartadas
- **Flutter / React Native**: no aprovechan la experiencia en Kotlin.
- **Supabase como backend completo**: rápido, pero esconde justo la parte de backend y seguridad que se quiere aprender.
- **Microservicios desde el principio**: demasiada complejidad para el MVP; se parte de un monolito modular.

## Consecuencias
- ➕ Un solo lenguaje (Kotlin) en el cliente; el backend en Java refuerza el perfil.
- ➖ Compose para Web/Wasm es menos maduro que en Android: hay que validarlo pronto (riesgo del Sprint 1).
- ➖ Hay que controlar el coste de la API de IA (caché, límites por usuario).
