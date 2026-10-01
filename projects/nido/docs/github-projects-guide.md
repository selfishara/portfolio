# 🧭 Guía: configurar GitHub Projects para Nido

Es tu primera vez con GitHub Projects, así que aquí tienes el paso a paso. 📸 marca los momentos que conviene capturar para el portfolio y LinkedIn.

## 1. Crear el repositorio del código
1. GitHub → **New repository** → nombre `nido` (o el definitivo) → Public → añadir README y `.gitignore`.
2. 📸 Captura del repo recién creado (el "día 0").

## 2. Crear el Project
1. Ve a tu perfil → pestaña **Projects** → **New project** → plantilla **Board**.
2. Ponle de nombre `Nido — Roadmap`.
3. En el Project: **⋯ → Settings → Manage access** y enlázalo al repo `nido` (**Link a repository**).

## 3. Campos personalizados (Settings → Custom fields)
| Campo | Tipo | Valores |
|---|---|---|
| Status | *Single select* (ya existe) | Backlog · Ready · In progress · In review · Done |
| Priority | *Single select* | P0 · P1 · P2 |
| Size | *Single select* | XS · S · M · L · XL |
| Sprint | **Iteration** | 2 semanas, empezando el lunes |
| Epic | *Single select* | EPIC-0 … EPIC-6 |

> 💡 El campo **Iteration** es el que convierte el tablero en sprints de verdad.

## 4. Vistas
1. **Board**, agrupado por Status y filtrado por `sprint:@current` → el tablero del sprint actual.
2. **Backlog**, en vista Table, agrupado por Epic y ordenado por Priority.
3. **Roadmap**, en vista Roadmap, usando el campo Sprint → la línea temporal. 📸 Esta captura luce mucho en LinkedIn.

## 5. Labels en el repo
`type:story` · `type:spike` · `type:bug` · `type:chore` · `security` · `ai` · `docs`

## 6. Plantillas de issue
En el repo, crea `.github/ISSUE_TEMPLATE/user-story.yml` y `spike.yml`. (Las crearemos juntas en el siguiente paso.)

## 7. Automatizaciones (Project → ⋯ → Workflows)
- *Item added to project* → Status = Backlog
- *Pull request merged* → Status = Done
- *Item closed* → Status = Done

## 8. Rutina de cada sprint
| Momento | Qué hacer | 📸 |
|---|---|---|
| Planning (lunes) | Pasar historias de Backlog a Ready y asignarles el sprint | Tablero al empezar |
| Durante el sprint | Una rama por issue (`feat/US-2.3-esfuerzo`) y un PR con `Closes #N` | — |
| Review (viernes, semana 2) | Demo y GIF de lo que funciona | GIF de la funcionalidad |
| Retro | Qué fue bien, qué mejorar y qué aprendí → [bitácora](bitacora.md) | Tablero al cerrar |
