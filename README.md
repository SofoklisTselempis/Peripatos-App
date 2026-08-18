# Deploying Peripatos as an installable app

This folder is a self-contained web app. It needs to be hosted over **HTTPS**
for location, microphone, and installability to work — opening the files
directly from your computer won't be enough.

The free, no-server way to do this is **GitHub Pages**.

## Steps (no coding required beyond uploading files)

1. Go to github.com and sign in (or create a free account).
2. Click the **+** in the top right → **New repository**.
   - Name it something like `peripatos`.
   - Keep it **Public** (required for free GitHub Pages).
   - Click **Create repository**.
3. On the new repo page, click **uploading an existing file**.
4. Drag in all four files from this folder: `index.html`, `manifest.json`,
   `service-worker.js`, `icon.svg`. Commit the changes.
5. Go to the repo's **Settings** tab → **Pages** (left sidebar).
6. Under **Source**, choose **Deploy from a branch**, branch `main`, folder
   `/ (root)`. Save.
7. GitHub will give you a URL after a minute or two, usually:
   `https://<your-username>.github.io/peripatos/`

## Installing it on your phone

1. Open that URL in Chrome (Android) or Safari (iPhone) on your phone.
2. Android Chrome: tap the **⋮** menu → **Install app** (or **Add to Home
   screen**).
   iPhone Safari: tap the **Share** icon → **Add to Home Screen**.
3. It now opens full-screen from your home screen like any other app, and
   location/microphone permission prompts will work normally since the site
   is served over HTTPS.

## What changed from the version you tried before

- Walk data now saves via **IndexedDB** (built into every browser) instead
  of Claude's internal storage bridge, so it works outside Claude entirely.
- Added a **manifest.json** and **service worker** — the two things Chrome
  requires before it will offer to install a site as an app.
- Everything else (GPS tracking, recording, path drawing, history) is
  unchanged.

## Known limits, still true here

- Everything is stored **only on this device's browser**. Clearing your
  browser data or uninstalling will erase your walks. There's still no
  backend, so "Friends" / "Everyone" privacy tiers don't actually share
  anything yet.
- Recording is capped at 3 minutes and there's no transcription — both need
  a real backend to lift.
