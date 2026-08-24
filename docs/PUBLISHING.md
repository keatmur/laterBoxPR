# Publishing Guide

This repository is intended to be public and act as the release hub for LaterBox.

## Recommended Setup

- Keep the full production repository private.
- Keep this repository public.
- Attach ready-to-install artifacts to GitHub Releases in this repository.

## Release Artifacts

Recommended public assets:

- `LaterBox-android-vX.Y.apk`
- `LaterBox-windows-vX.Y.msi`

## Build Commands

From the private main repository:

### Android

```powershell
.\gradlew.bat :composeApp:assembleRelease
```

Expected output is the Android release artifact under the module build outputs directory.

### Windows

```powershell
.\gradlew.bat :composeApp:packageReleaseMsi
```

The project is currently configured to package Windows as `msi`, not `exe`.

## Public Release Workflow

1. Build the Android release artifact in the private repository.
2. Build the Windows `msi` artifact in the private repository.
3. Open the public GitHub repository.
4. Create a new GitHub Release with version tag such as `v1.1.0`.
5. Upload the `apk` and `msi` files as release assets.
6. Update release notes with user-facing changes.

## Public Repository Content

This public repository should contain:

- `README.md`
- screenshots and diagrams
- architecture overview
- release notes
- downloadable binaries through GitHub Releases

This public repository should not contain:

- secrets
- signing files
- local environment files
- internal planning documents
- the full private production implementation unless you intentionally decide to publish it
