# Bella's Brain

A TikTok-style GCSE microlearning feed covering all 24 subjects with their exam boards, papers and topics (2025-2027 specifications). Swipe through bite-size lessons, take quick quizzes, save collections, and let the app build a personalised pathway from what you watch, like and answer.

It is a single-file app (React via CDN) and works as an installable PWA, so it can be added to a phone's home screen and opened fullscreen. It stores progress on the device.

## Files

| File | Purpose |
|------|---------|
| `index.html` | The whole app |
| `manifest.webmanifest` | Makes it installable (name, icon, fullscreen) |
| `sw.js` | Service worker — offline use after the first visit |
| `icon-192.png`, `icon-512.png`, `icon-512-maskable.png` | App icons |
| `apple-touch-icon.png`, `favicon.png` | iOS / browser icons |
| `.nojekyll` | Tells GitHub Pages to serve files as-is |

## Deploy to GitHub Pages

### Option A — upload in the browser (no command line)

1. Create a new repository on GitHub, e.g. `bellas-brain`.
2. Click **Add file -> Upload files**, drag in **every file in this folder** (including the hidden `.nojekyll`), and commit.
3. Go to **Settings -> Pages**. Under *Build and deployment*, set **Source: Deploy from a branch**, branch **main**, folder **/ (root)**. Save.
4. Wait a minute, then open `https://dlockwood13.github.io/bellas-brain/`.

> If `.nojekyll` is hard to drag (some systems hide dotfiles), you can skip it — the app still works, it just helps avoid edge cases.

### Option B — command line

```bash
cd path/to/this/folder
git init
git add -A
git commit -m "Bella's Brain"
git branch -M main
git remote add origin https://github.com/dlockwood13/bellas-brain.git
git push -u origin main
```

Then enable Pages as in step 3 above.

## Install on a phone (add to home screen)

- **iPhone (Safari):** open the Pages URL, tap the Share button, then **Add to Home Screen**.
- **Android (Chrome):** open the URL, tap the menu, then **Install app** / **Add to Home screen**.

It then opens fullscreen with its own icon, like a normal app.

## Updating later

Edit `index.html`, re-upload it, and bump the `CACHE` version near the top of `sw.js` (e.g. `bellas-brain-v3`) so phones pick up the new version instead of the cached one.

## Notes

- Progress (likes, saves, quiz history, pathway) is saved in the browser on each device. Use the **Export** button on the *You* tab to back it up.
- Offline works after the first online visit, once the service worker has cached the app and its libraries.
