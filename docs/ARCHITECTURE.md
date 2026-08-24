# LaterBox Architecture

## Overview

LaterBox is designed as a local-first Kotlin Multiplatform application with shared business logic and shared UI for Android, iOS, and Desktop.

The main product goal is simple: save a URL, extract metadata, classify the content, and keep it organized for later consumption.

## Core Flow

1. A user saves a URL.
2. The app fetches and parses the HTML metadata.
3. The parser extracts title, description, image, source site, and content signals.
4. The domain layer maps the result into a content item.
5. The repository persists the item locally.
6. The UI updates from local state.

## Main Layers

### Presentation

The presentation layer is implemented with Compose Multiplatform and Material 3.

Responsibilities:

- render screens and reusable components
- observe view model state
- trigger user actions
- expose platform-adaptive behavior where needed

### Domain

The domain layer contains business models and rules.

Responsibilities:

- represent content items and content types
- define mode logic such as `FOCUS` and `CHILL`
- keep business decisions independent from UI or storage details

### Data

The data layer owns persistence and metadata collection.

Responsibilities:

- local database operations through SQLDelight
- repository abstractions for content access
- HTML metadata parsing
- URL classification heuristics

## Metadata Parsing

One of the more interesting technical parts of the project is the metadata parser.

It uses:

- HTML parsing through `Ksoup`
- Open Graph and Twitter card extraction
- schema.org signals
- URL and keyword heuristics

The parser attempts to infer content type across:

- article
- video
- book
- podcast
- movie
- series

This makes the saved list much more useful than a plain bookmark store.

## Local-First Direction

The long-term sync model is local-first:

- local database is the main source of truth
- remote sync is a transport and backup layer
- merge decisions are driven by timestamps

This keeps the app responsive and reduces coupling between product logic and backend decisions.

## Why This Project Is Worth Showing

LaterBox demonstrates several useful engineering concerns in one app:

- Kotlin Multiplatform structure
- shared UI with Compose Multiplatform
- layered application design
- parser and heuristic-based classification logic
- local-first data modeling
- platform-specific integrations behind shared abstractions
