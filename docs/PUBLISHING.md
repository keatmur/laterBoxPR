# Publishing Guide

This public repository is the release hub and website for LaterBox. The production source code lives in a private repository, where this repository is included as the `showcase-repo` git submodule.

## Website

The landing page is served by GitHub Pages from the `main` branch root:

- https://keatmur.github.io/laterBoxPR/
- https://keatmur.github.io/laterBoxPR/ru.html

If the repository is renamed or a custom domain is connected, update the URLs in `index.html`, `ru.html` (canonical, hreflang, Open Graph, download links), `sitemap.xml`, `robots.txt`, and `README.md`.

## Release Assets

Binaries are attached to GitHub Releases and are never committed. Asset names do not contain a version, so the website links to `releases/latest/download/<name>` always serve the newest build:

| Asset | Source in the private repository |
|---|---|
| `LaterBox-android.apk` | `composeApp/build/outputs/apk/release/composeApp-release.apk` |
| `LaterBox-windows.msi` | `composeApp/build/compose/binaries/main-release/msi/LaterBox-<version>.msi` |
| `LaterBox-windows.exe` | `composeApp/build/compose/binaries/main-release/exe/LaterBox-<version>.exe` |

## Build Commands

Run from the private repository root:

```powershell
.\gradlew.bat :composeApp:assembleRelease
.\gradlew.bat :composeApp:packageReleaseMsi :composeApp:packageReleaseExe
```

Before building, bump `versionCode` / `versionName` (Android) and `packageVersion` (Desktop) in `composeApp/build.gradle.kts`.

## Release Workflow

1. Build the artifacts listed above.
2. Copy them under the asset names from the table.
3. Create the release (requires [GitHub CLI](https://cli.github.com/), authenticated with `gh auth login`):

```powershell
gh release create v1.1.0 `
  LaterBox-android.apk LaterBox-windows.msi LaterBox-windows.exe `
  --repo keatmur/laterBoxPR --title "LaterBox 1.1.0" --notes-file notes.md
```

4. Check that the download buttons on the website work.
5. If the website changed, commit and push this repository, then update the submodule pointer in the private repository.

## What Not To Publish

- secrets, signing keys, `keystore.properties`, `local.properties`
- internal planning documents
- the private production source code
