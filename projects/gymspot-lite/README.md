# 🏋️ GymSpot Lite

Fitness app built with **Kotlin Multiplatform (KMP)** and **Compose Multiplatform** — a single shared codebase targeting Android, Desktop (JVM), Web (WASM), and iOS. Users browse real exercises from the Wger API, build routines saved to the cloud, track favorites, and execute workouts with sets, reps, and rest timers.

> **My role:** Solo developer — architecture, implementation, and deployment across all platforms.

---

## Tech Stack

| Library | Version | Role |
|---|---|---|
| Kotlin Multiplatform | 2.x | Shared logic across all targets |
| Compose Multiplatform | 1.10.3 | Unified UI: Android, Desktop, Web, iOS |
| Navigation 3 (JetBrains) | 1.0.0-alpha06 | Back-stack navigation with serializable routes |
| Ktor Client | 3.4.2 | HTTP — Wger API |
| Supabase (Postgrest + Auth) | 3.2.2 | Cloud DB + user authentication |
| Kotlinx Serialization | 1.10.0 | Routes + JSON DTOs |
| Kotlin Coroutines | 1.10.2 | Async data loading |

---

## Architecture

```
commonMain/kotlin/
├── data/
│   ├── remote/       # Wger API (Ktor): WgerApi, WgerDataSource, WgerExerciseRepository
│   ├── supabase/     # Exercises cache, routines, favorites, auth session
│   ├── sync/         # ExerciseSyncService — Supabase-first, Wger fallback
│   └── dto/ + mapper/
├── model/            # Exercise, Routine, RoutineTemplate, MuscleGroup, ExerciseLanguage
├── state/            # AuthState, RoutineState, RoutinesListState, FavoritesState,
│                     #   AppSettingsState, WorkoutSessionState
├── navigation/       # Navigation3 routes + NavigationWrapper
└── screens/ + components/
```

**Data flows:**
- Exercises: language change → `ExerciseSyncService` checks Supabase; on miss, fetches Wger API and upserts to cloud
- Routines: login → `loadAll(userId)` → every mutation syncs to Supabase immediately

**State:** Compose singletons (`mutableStateOf`, `mutableStateListOf`) — no ViewModel layer, state objects expose read-only views and mutate through named methods only.

---

## Demo

![Explore](https://raw.githubusercontent.com/selfishara/portfolio/main/projects/gymspot-lite/gifs/explore.gif)
![Exercise detail](https://raw.githubusercontent.com/selfishara/portfolio/main/projects/gymspot-lite/gifs/exercise.gif)
![Workout execution](https://raw.githubusercontent.com/selfishara/portfolio/main/projects/gymspot-lite/gifs/workout.gif)

---

## Screenshots

<p align="center">
  <img src="https://raw.githubusercontent.com/selfishara/portfolio/main/projects/gymspot-lite/gifs/screenshot_explore.png" width="22%"/>
  <img src="https://raw.githubusercontent.com/selfishara/portfolio/main/projects/gymspot-lite/gifs/screenshot_exercise.png" width="22%"/>
  <img src="https://raw.githubusercontent.com/selfishara/portfolio/main/projects/gymspot-lite/gifs/screenshot_workout.png" width="22%"/>
  <img src="https://raw.githubusercontent.com/selfishara/portfolio/main/projects/gymspot-lite/gifs/screenshot_routines.png" width="22%"/>
</p>

---

## Features

- Browse real exercises from the Wger API, filtered by language (EN/ES) and muscle group
- Create, name, and manage multiple workout routines saved per user to the cloud
- Execute workouts with sets/reps tracking, 60s rest timer, and completion summary
- Save exercises to favorites, accessible from your profile
- Supabase email/password authentication — each user's data fully isolated with Row-Level Security
- Quick Start Templates: Push Day, Pull Day, Leg Day, Full Body, Upper Body, Core Blast

---

## Database Schema (Supabase)

| Table | Purpose |
|---|---|
| `exercises` | Language-keyed exercise cache from Wger API |
| `routines` | Named routines per user (`session_id = auth.uid()`) |
| `routine_exercises` | Exercises within each routine, ordered by position |
| `favorites` | User's saved exercises |

Row-Level Security enabled on all user tables.

---

## Build & Run

```bash
# Desktop (JVM)
./gradlew :composeApp:run

# Android debug APK
./gradlew :composeApp:assembleDebug

# Web (WASM)
./gradlew :composeApp:wasmJsBrowserDevelopmentRun
```

iOS: open `iosApp/iosApp.xcodeproj` in Xcode. Requires JDK 17.

---

## Repository

[github.com/selfishara/MULTIPLATFORM](https://github.com/selfishara/MULTIPLATFORM)
