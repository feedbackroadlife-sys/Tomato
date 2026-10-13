# Tomato Focus

Pomodoro timer with tasks and daily, weekly and monthly focus analytics. Signs in with Google and syncs automatically across devices.

## Files

- `index.html` the app
- `manifest.webmanifest`, `sw.js`, `icons/` make it installable and usable offline
- `netlify/functions/api.mjs` the sync API (Netlify Function, data kept in Netlify Blobs)
- `package.json`, `netlify.toml` Netlify settings

## Deploy

1. Create a GitHub repo and upload everything, keeping the folder structure
   (`icons/` and `netlify/functions/api.mjs`). On GitHub, Add file > Create new file lets you type a path like
   `netlify/functions/api.mjs` to create folders.
2. In Netlify: Add new site > Import from GitHub > pick the repo. Leave the build command empty. Publish directory is `.`
3. Open your Netlify URL.

## Google sign-in

The Client ID is already in `index.html` and `api.mjs`. In Google Cloud Console, open that OAuth client
(APIs & Services > Credentials) and add your site address under **Authorised JavaScript origins**:

- `https://your-site.netlify.app` (your real Netlify URL, no trailing slash)

It can take a few minutes to apply.

## Install as an app

Open the site in Chrome, then menu (three dots) > Add to Home screen or Install app.

## How sync works

- Tasks, settings and per-day focus time are saved on the device first, then synced to the server when you are signed in and online.
- Each Google account has its own record. Signing in on another device pulls it down.
- If two devices record time on the same task and day while offline, the larger total is kept.
- Signing in with a different account on the same device clears the previous account's local copy first.

## Updating

After you change any file, change `CACHE` in `sw.js` (for example `tomato-focus-v3`) so installed copies update.
