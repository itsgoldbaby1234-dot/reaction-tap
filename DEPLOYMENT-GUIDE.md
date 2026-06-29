# Reaction Tap — Google Play Deployment Guide

## What you have
A complete PWA (Progressive Web App) with:
- `index.html` — the full game
- `manifest.json` — app metadata (name, icons, colors)
- `sw.js` — service worker for offline play
- `icons/` — folder where you add your app icons

---

## Step 1 — Create your app icons

You need two PNG icons:
- `icons/icon-192.png` — 192×192 pixels
- `icons/icon-512.png` — 512×512 pixels

**Free icon tool:** Go to https://favicon.io or https://www.canva.com
- Make a dark (#111) background with a green ✕ symbol
- Export at both sizes
- Save them into the `icons/` folder

---

## Step 2 — Host on GitHub Pages (free)

1. Go to https://github.com and create a free account
2. Click **New repository** → name it `reaction-tap`
3. Upload all your files (index.html, manifest.json, sw.js, icons folder)
4. Go to **Settings → Pages → Source → main branch**
5. Your game will be live at: `https://YOUR-USERNAME.github.io/reaction-tap/`

Test it on your phone browser first — it should work fully.

---

## Step 3 — Add to Home Screen (optional quick test)

On Android Chrome:
1. Open your GitHub Pages URL
2. Tap the 3-dot menu → **Add to Home screen**
3. It installs like a real app!

---

## Step 4 — Package for Google Play with Bubblewrap

### Install Node.js
Download from https://nodejs.org (LTS version)

### Install Bubblewrap
Open Terminal / Command Prompt and run:
```
npm install -g @bubblewrap/cli
```

### Create the TWA package
```
mkdir reaction-tap-twa
cd reaction-tap-twa
bubblewrap init --manifest https://YOUR-USERNAME.github.io/reaction-tap/manifest.json
```

Follow the prompts — it will ask for:
- Package name: `com.yourname.reactiontap`
- App name: `Reaction Tap`
- Signing key password (create a new one, save it somewhere safe!)

### Build the APK/AAB
```
bubblewrap build
```
This creates `app-release-bundle.aab` — the file you upload to Google Play.

---

## Step 5 — Google Play Developer Account

1. Go to https://play.google.com/console
2. Pay the one-time **$25 registration fee**
3. Create a new app → select **Free** → **Game**

### Required for submission:
- [ ] App icon (512×512 PNG — same as your icon-512.png)
- [ ] Feature graphic (1024×500 PNG — a banner image for the store)
- [ ] 2+ screenshots from a phone (you can take these from your browser)
- [ ] Short description (80 chars max)
- [ ] Full description
- [ ] Privacy policy URL (use https://www.privacypolicygenerator.info — free)
- [ ] Content rating questionnaire (takes ~5 minutes)

### Upload and submit:
1. Go to **Production → Create new release**
2. Upload your `.aab` file
3. Fill in release notes
4. Click **Review release → Start rollout**

---

## Step 6 — Wait for review

Google reviews new apps in **1–7 days**. You'll get an email when it's approved.

---

## Estimated total cost
| Item | Cost |
|------|------|
| GitHub Pages hosting | Free |
| Bubblewrap / Node.js | Free |
| Google Play developer account | $25 (one-time) |
| Domain name (optional) | ~$12/yr |
| **Total minimum** | **$25** |

---

## Need help?
The Bubblewrap documentation is at:
https://github.com/GoogleChromeLabs/bubblewrap

The TWA guide from Google is at:
https://developer.chrome.com/docs/android/trusted-web-activity
