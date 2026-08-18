# Scratch Desktop — Test Channel

Packaged releases for the **test channel** of the Scratch Desktop app ("Scratch (Test)").

> ⚠️ **Internal test builds — not for end users.** The apps published here point at Whalesync's **test** backend (`test-api.scratch.md`) and can change, break, or be replaced at any time. For the real app, use the production builds (see [Production app](#production-app) below).

## What this repo is

This repository holds **only the packaged releases** of the test build of Scratch Desktop — the installers plus the `electron-updater` metadata the "Scratch (Test)" app uses to update itself. There's no source code here; the app is built from Whalesync's internal monorepo and published to this repo automatically by CI.

Keeping the test channel in its own repository — separate from the production repo, [`whalesync/scratch-desktop`](https://github.com/whalesync/scratch-desktop) — gives each channel its own GitHub **"latest"** pointer. A test build then always auto-updates to the newest *test* release and can never be offered a production build (and vice-versa).

## Auto-update

The "Scratch (Test)" app checks this repo for updates via `electron-updater` (on launch and periodically). It resolves the newest release through GitHub's **latest** pointer and reads the channel manifest (`desktop-test-*.yml`) attached to that release. Test releases are published as **full, non-prerelease** releases so that pointer always resolves to the newest one.

- Release tags: `vX.Y.Z-test`
- Latest release: **[/releases/latest](../../releases/latest)**

## Downloads

Grab a build from the [**Releases**](../../releases) page. Each release attaches:

- **macOS** — `.dmg` (installer) and `.zip` (used by the auto-updater); Apple Developer ID–signed and notarized; Apple Silicon (arm64).
- **Windows** — `.exe` (NSIS installer). **Shipped unsigned on purpose**, so Windows SmartScreen may warn on first launch.
- **Linux** — `.AppImage` and `.deb`.
- `checksums.txt` (SHA-256 of the installers) plus the `electron-updater` manifests and delta blockmaps.

## How releases are produced

Releases here are cut **automatically** by a scheduled pipeline in Whalesync's internal monorepo — they aren't authored by hand. A scheduled job also prunes old test releases, always keeping the newest as the channel's "latest". Please treat this repo as **CI-managed**: don't manually create, edit, or delete releases.

This repo hosts build artifacts only and isn't monitored for issues — please raise bugs through the usual internal Whalesync channels.

## Production app

Looking for the real thing? Production builds live in **[`whalesync/scratch-desktop`](https://github.com/whalesync/scratch-desktop)**, and the current release is available from the Scratch web app's downloads page.

## About Scratch

Scratch is a content management system that syncs data between external services (Airtable, Webflow, Notion, and more) and a git-based storage layer, giving knowledge workers a VS Code–like workspace for managing content. Learn more at [scratch.md](https://scratch.md).
