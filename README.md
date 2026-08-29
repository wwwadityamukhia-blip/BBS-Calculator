# Rebar BBS Calculator — installable app

This folder is a installable web app (PWA). Once hosted anywhere over
HTTPS, it installs to your phone's home screen like a real app, works
fully offline, and opens without browser address bars.

Files:
- `index.html` — the calculator
- `manifest.json` — app name, icon, colors
- `service-worker.js` — enables offline use
- `icons/` — app icons

## Why it needs hosting

Browsers only allow the offline/install features (service worker) over
`https://` or `localhost` — not when opening `index.html` directly from
a phone's file storage. You need to put these files on any free static
host. Pick whichever is easiest:

### Option A — GitHub Pages (free, permanent link)
1. Create a new GitHub repo, upload all files in this folder (keep the
   `icons/` folder structure).
2. Repo Settings → Pages → Source: `main` branch, `/ (root)` → Save.
3. GitHub gives you a URL like `https://yourname.github.io/reponame/`.
4. Open that URL on your phone.

### Option B — Netlify Drop (free, fastest, no account needed)
1. Go to https://app.netlify.com/drop on a computer.
2. Drag this whole folder onto the page.
3. Netlify gives you a live URL instantly — open it on your phone.

### Option C — test locally first (same WiFi network)
From a computer in this folder:
```
python3 -m http.server 8000
```
Then on your phone (same WiFi), open `http://<computer-ip>:8000`.
Good for testing — not for daily site use, since the computer must
stay on and both devices must share a network.

## Installing on your phone

**Android (Chrome):** open the hosted URL → menu (⋮) → "Install app" or
"Add to Home screen".

**iPhone (Safari):** open the hosted URL → Share button → "Add to Home
Screen".

After installing, it launches full-screen with its own icon and keeps
working with no signal — useful on site where connectivity is patchy.

## Updating it later

If you edit `index.html` and re-upload, bump `CACHE_NAME` in
`service-worker.js` (e.g. `bbs-calc-v2`) so installed devices pick up
the new version instead of serving the cached one.
