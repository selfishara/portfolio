# GymSpot Lite

GymSpot Lite is a fitness app built with Kotlin Multiplatform (KMP) and Compose Multiplatform. Users browse real exercises from the Wger API, create and manage multiple workout routines saved to the cloud, track favorites, and execute workouts with sets, reps, and rest timers. Targets Android, Desktop (JVM), Web (WASM), and iOS from a single shared codebase.

## Technologies

- Kotlin Multiplatform
- Compose Multiplatform
- Ktor Client
- Supabase (Postgrest + Auth)
- Navigation 3 (JetBrains)
- Kotlinx Serialization
- Kotlin Coroutines

## Features

- Exercise browsing with real Wger API data, filtered by language (EN/ES) and organized by muscle group
- Multiple routines per user — create, name, manage, and delete; all persisted in Supabase
- Full workout execution: sets/reps tracking, 60s rest timer, and completion summary
- Favorites system — save exercises and access them from your profile
- Supabase Auth: email/password login with per-user data isolation via Row-Level Security
- Quick Start templates: Push Day, Pull Day, Leg Day, Full Body, Upper Body, Core Blast
- English and Spanish exercise libraries

## Architecture

Clean layer separation: remote API → sync service → Supabase cache → domain state → UI. All business logic lives in commonMain with platform specifics isolated to each target. State management uses MVP-grade Compose singletons exposing read-only views and mutating only through named methods.

## Developer Role

- Full-stack KMP architecture design and implementation
- Wger API integration with DTO + mapper system and paginated fetch
- Supabase schema design (exercises, routines, routine_exercises, favorites) with RLS policies
- Authentication flow and persistent session management across platforms
- Compose Multiplatform UI with custom dark design system (GymSpot design language)
- CI pipeline on GitHub Actions

## Links

- **Repository:** https://github.com/selfishara/MULTIPLATFORM