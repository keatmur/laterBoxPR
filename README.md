# LaterBox

LaterBox is a Kotlin Multiplatform app for saving things to watch or read later across Android, iOS, and Desktop.

This public repository is a showcase and release hub for the project. It contains product overview, architecture notes, screenshots, and downloadable builds. The full production repository remains private.

## What It Does

- Save links from articles, videos, books, podcasts, movies, and series
- Parse page metadata automatically from the URL
- Classify content into meaningful content types
- Organize items by mode: `FOCUS` and `CHILL`
- Track progress for reading and watching
- Follow a local-first architecture with planned cross-device sync

## Tech Stack

- Kotlin Multiplatform
- Compose Multiplatform
- SQLDelight
- Koin
- Ktor Client
- Ksoup
- Material 3

## Platforms

- Android
- iOS
- Desktop (JVM)

## Architecture

LaterBox follows a clean layered structure:

- `presentation` for Compose UI, screens, and view models
- `domain` for business models and rules
- `data` for repositories, local persistence, and metadata parsing

More details are available in [docs/ARCHITECTURE.md](./docs/ARCHITECTURE.md).

## Highlights

- Shared business logic across mobile and desktop targets
- Local-first storage design
- Metadata extraction from arbitrary URLs
- Heuristic content type detection for article, video, book, podcast, movie, and series pages
- Compose Multiplatform UI with platform-specific integrations where needed

## Screenshots And Diagrams

- Domain model diagram: [media/domain-model-diagram.png](./media/domain-model-diagram.png)
- Progress flow diagram: [media/progress-flow-diagram.png](./media/progress-flow-diagram.png)

## Public Site

This repository is intended to work as both:

- a public product page through GitHub Pages
- a download hub through GitHub Releases

Recommended Pages URL:

- `https://keatmur.github.io/LaterBox/`

If you later connect a custom domain, replace canonical URLs and sitemap entries accordingly.

## Downloads

Published builds are attached to GitHub Releases in this repository.

- Android: `apk`
- Windows: `msi`

Release notes and the publishing flow are documented in [docs/PUBLISHING.md](./docs/PUBLISHING.md).

## Repository Scope

This repository intentionally does not contain the full production source code.

It is meant to show:

- the product direction
- the technical stack
- the architecture decisions
- the release artifacts

## Contact

If you want a private walkthrough of the full implementation for interview or review purposes, contact the repository owner.
