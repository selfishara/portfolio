# 🎧 SongSwipe
Android music discovery app built with **Kotlin** and **Clean Architecture**. Users swipe through song recommendations powered by the **Spotify Web API**, save favorites, and get personalized suggestions — built as a collaborative academic project with a team of 9.

> **My role:** Software Architect — designed and implemented the app's Clean Architecture structure, defined layer boundaries and module organization, and led technical decisions on the Android frontend.

---

## Tech Stack

| Layer | Technology |
|---|---|
| Language | Kotlin |
| Architecture | Clean Architecture (Data · Domain · Presentation) |
| UI | Jetpack Compose |
| Dependency Injection | Koin |
| Local DB | Room |
| Networking | Retrofit + OkHttp |
| Backend | Supabase |
| External API | Spotify Web API |
| Min SDK | Android 8.0 (API 26) |

---

## Architecture

Clean Architecture with strict layer separation — no framework dependencies in the domain layer.

```
app/src/main/java/
├── core/           # Config, network, utilities
├── data/           # DataSources, repositories, mappers
├── domain/         # Models, use cases, interfaces
├── presentation/   # UI, ViewModels, activities/fragments
└── di/             # Koin dependency injection modules
```

---

## Demo

![Swipe interaction](https://raw.githubusercontent.com/selfishara/portfolio/main/projects/songswipe/gifs/swipe.gif)
![Vibe selection](https://raw.githubusercontent.com/selfishara/portfolio/main/projects/songswipe/gifs/vibe.gif)
![Playlists](https://raw.githubusercontent.com/selfishara/portfolio/main/projects/songswipe/gifs/playlists.gif)

---

## Screenshots

<p align="center">
  <img src="https://raw.githubusercontent.com/selfishara/portfolio/main/projects/songswipe/gifs/screenshot_vibe.png" width="23%"/>
  <img src="https://raw.githubusercontent.com/selfishara/portfolio/main/projects/songswipe/gifs/screenshot_swipe.png" width="23%"/>
  <img src="https://raw.githubusercontent.com/selfishara/portfolio/main/projects/songswipe/gifs/screenshot_card.png" width="23%"/>
  <img src="https://raw.githubusercontent.com/selfishara/portfolio/main/projects/songswipe/gifs/screenshot_playlist.png" width="23%"/>
</p>

---

## Key Features

- Swipe-based music discovery interface (like/dislike)
- Spotify API integration for real-time song recommendations
- Personalized suggestions based on user interaction history
- Local favorites storage with Room
- User authentication and cloud sync via Supabase
- Offline support through local database caching

---

## My Contributions

- Defined and implemented the Clean Architecture structure from scratch
- Designed the layer boundaries: data, domain, presentation
- Set up Koin dependency injection modules
- Implemented core domain use cases and repository interfaces
- Coordinated technical decisions across the team as Software Architect

---

## Team

9-person academic team (DAM · ILERNA): Product Owners, Scrum Master, Software Architects, UX/UI Designers, DevOps — with full agile workflow including sprints, backlog, and PR-based development.

| Role | Members |
|---|---|
| Software Architects | Federico Sánchez Vidarte, **Sara Martínez Bascuas** |
| UX/UI Designers | Javier Tolosana, Jonathan Villamizar, Bianca Sánchez |
| Scrum Master / DevOps | Kevin Nahuel Ramírez |
| Product Owners | Biel Ramos Rifà |

---

## Repositories

- Frontend: [github.com/selfishara/song-swipe-frontend](https://github.com/selfishara/song-swipe-frontend)
- Docs: [Technical documentation](https://github.com/fedesanchezilerna/song-swipe-docs)
