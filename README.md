# Recomp Tracker — Install on GitHub Pages

## 1. Create the repo
1. Go to https://github.com/new
2. Name it something like `recomp-tracker` (repo can be public or private — Pages works either way on a free personal account, though private repos need GitHub Pro for Pages; public is simplest).
3. Don't initialize with a README (we already have one).

## 2. Push these files
From this folder, run:
```bash
git init
git add .
git commit -m "Recomp tracker PWA"
git branch -M main
git remote add origin https://github.com/<your-username>/recomp-tracker.git
git push -u origin main
```

## 3. Enable Pages
1. In the repo: **Settings → Pages**
2. Under "Build and deployment" → Source: **Deploy from a branch**
3. Branch: **main**, folder: **/ (root)**
4. Save. Wait ~1 minute.
5. Your app will be live at:
   `https://<your-username>.github.io/recomp-tracker/`

## 4. Install on your phone
1. Open that URL in **Chrome** on Android.
2. Tap the **⋮ menu** → **"Add to Home screen"** (or Chrome may show an install banner automatically).
3. Confirm. You'll get a real home-screen icon that opens standalone (no browser bar).

## 5. Updating later
Whenever you edit `index.html`:
1. Bump `CACHE_NAME` in `sw.js` (e.g. `v1` → `v2`) so the service worker knows to refresh the cache.
2. `git add . && git commit -m "update" && git push`
3. GitHub Pages redeploys automatically in ~1 minute.
4. Reopen the app on your phone (may need to force-close and reopen once for the new service worker to take over).

## Notes
- All your data (weights, exercise logs, measurements) lives in the phone's local storage — nothing is sent anywhere. It's tied to that specific browser/app instance, so it won't sync across devices, and clearing Chrome's site data will wipe it.
- The app works offline after the first load, since the service worker caches the shell.
- Chart.js is still pulled from a CDN — charts need internet the first time they load per session, then they're cached too.
