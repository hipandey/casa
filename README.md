# Casa — Home & Shopping Lists

A simple, installable checklist app for home tasks and shopping runs (Home Showing, Costco, Walmart, Indian Store, and any lists you add). Works on iPhone and web, saves everything on your device, and lets you share a list to WhatsApp so someone else can add it to their own copy of the app.

It is a self-contained `index.html` file plus a small `sw.js` (service worker for offline use) — no build step, no server, no dependencies.

## Features

- Multiple lists with add / edit / delete for both items and lists
- Auto-assigned icons per item (home + grocery aware), editable
- Live progress ring, "done today / remaining" stats, and a day streak
- Optional showing-time countdown bar that changes color as the time approaches
- Daily auto-reset of checkmarks
- Data saved on-device (persists after closing the app and restarting the phone)
- Installable to the iPhone home screen as a standalone app (PWA)
- Fully offline after first load — launches with no internet (airplane mode, after reboot)
- Share a list to WhatsApp as a tap-to-open link; the recipient gets an "Add to my lists" prompt

## Run it locally

Just open `index.html` in any browser. That's it.

## Host it (needed for install + sharing)

Installing to the home screen and sharing tap-to-open links both require the app to be served from an `https://` address rather than a local file.

### GitHub Pages

1. Create a new **public** GitHub repository (e.g. `casa`).
2. Upload **both `index.html` and `sw.js`** to the repo (Add file → Upload files → Commit). Both files are required for offline to work.
3. Go to **Settings → Pages**, set **Branch** to `main` and folder to `/ (root)`, then **Save**.
4. After ~1 minute your app is live at `https://<your-username>.github.io/casa/`.

To update the app later, upload a new `index.html`. If you changed the app and want installed phones to pick it up immediately, also bump the `CACHE` version at the top of `sw.js` (e.g. `casa-v1` → `casa-v2`) and upload it too.

## Install on iPhone

Open your GitHub Pages URL in **Safari**, then tap **Share → Add to Home Screen**. Launches full-screen with its own icon; your data is durable across restarts.

## Share a list

Tap **↗ Share** on any list → pick WhatsApp. The recipient taps the link, and if they've installed the app from the same URL it opens right in their copy with an **Add to my lists** button.

## Tech

Plain HTML, CSS, and vanilla JavaScript. State is stored in the browser's `localStorage`. A web app manifest and Apple meta tags make it installable as a PWA, and `sw.js` (a service worker) caches the app for full offline use. No frameworks required.
