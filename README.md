# መልክእ Memory Garden — GitHub Pages web app

A free, offline-capable Progressive Web App (PWA) based on Memory Garden v4.5. No buildtools, npm dependencies, database, or web server are required for hosting.

## Publish on GitHub Pages

1. Sign in to GitHub and create a new repository, e.g. `melkea-memory-garden` (a public repository is the simplest option for a free GitHub Pages site).
2. Extract `melkea-github-pages.zip` on your device.
3. Upload **the contents** of that folder to the **root** of the repository, keeping `icons/` as a folder. Do **not** upload the ZIP without extracting it.
4. In GitHub, go to repository **Settings → Pages → Build and deployment → Source: Deploy from a branch**. Set branch `main` and folder `/(root)`, then save.
5. After GitHub publishes it, your site is typically `https://YOUR-USERNAME.github.io/melkea-memory-garden/`. Check **Settings → Pages** for the exact URL.
6. Open the site once online. On Android/desktop use Chrome menu **Install app / Add to Home screen** (or the in-app **More → Install app**). On iPad/iPhone use Safari **Share → Add to Home Screen**.

To update later, replace `index.html` in the repo with the newer version and, for offline cache changes, increment `CACHE_NAME` in `sw.js`. Reload the site with internet to pick up the new files. A newly installed service worker may take one more navigation to control an open tab.

## VERY IMPORTANT: back up old progress first

**GitHub Pages creates a new web origin.** Browsers do not automatically migrate localStorage/IndexedDB from local `file://` HTML files or a different URL to the new site.

- In your old v4.5 HTML app, go to **Library → Export Complete Archive** and save the `.zip` backup (this includes audio recordings where supported).
- Open the new GitHub Pages site and restore that archive via **Library → Import** / **Restore Archive**.
- Confirm that your collections, study history and attached recordings are available before removing the old file.

## Where is my data?

Collection texts, progress, review history and recorded audio are kept on each browser/device using localStorage and IndexedDB. **GitHub Pages does not provide accounts or cross-device sync.** The source repository contains only starter text and the app itself; do not commit your personal backup ZIP or private recordings to a public GitHub repo. Use export/import to transfer data between devices.

## Offline operation and microphone access

The service worker saves the app shell for offline use after the first successful HTTPS visit. Audio that you attach or record is available offline if the browser permits persistent storage. Chrome/Safari may evict stored data under low storage; keep backups. Microphone recording requires browser permission and may vary on iOS/iPadOS.

## Files

- `index.html` — app, styles, study features, offline-first local data
- `manifest.webmanifest` — install-to-home-screen information
- `sw.js` — offline app shell and cache update logic
- `icons/icon-192.png`, `icons/icon-512.png` — install icons
- `.nojekyll` — serve files directly without a Jekyll build

No external scripts, CDNs, or tracking services are included.
