# Sec+ Cards — PWA Deployment Guide

## What's in this folder

```
secplus-pwa/
├── index.html       ← The full app (React + your flashcards)
├── manifest.json    ← PWA config (app name, icons, theme)
├── sw.js            ← Service worker (enables offline use)
└── icons/
    ├── icon-192.png ← Home screen icon
    └── icon-512.png ← Splash screen icon
```

## Deploy to GitHub Pages (Free)

### 1. Create a repo

```bash
cd secplus-pwa
git init
git add .
git commit -m "Sec+ Cards PWA"
```

### 2. Push to GitHub

```bash
# Using GitHub CLI (if installed):
gh repo create secplus-cards --public --source=. --push

# OR manually:
# - Create a new repo on github.com called "secplus-cards"
# - Then run:
git remote add origin https://github.com/YOUR_USERNAME/secplus-cards.git
git branch -M main
git push -u origin main
```

### 3. Enable GitHub Pages

1. Go to your repo on GitHub
2. **Settings** → **Pages** (left sidebar)
3. Under "Source", select **Deploy from a branch**
4. Branch: **main**, folder: **/ (root)**
5. Click **Save**
6. Wait ~1 minute, your app will be live at:
   `https://YOUR_USERNAME.github.io/secplus-cards/`

### 4. Install on iPhone

1. Open `https://YOUR_USERNAME.github.io/secplus-cards/` in **Safari** on your iPhone
2. Tap the **Share** button (square with arrow at bottom)
3. Scroll down and tap **"Add to Home Screen"**
4. Name it **Sec+ Cards** → tap **Add**

That's it! It will appear on your home screen as a standalone app with:
- Full-screen mode (no Safari toolbar)
- Your custom app icon
- Offline support (works without internet after first load)
- Persistent progress and daily streak data via localStorage

## Updating the App

After making changes:

```bash
git add .
git commit -m "description of changes"
git push
```

GitHub Pages will auto-deploy in ~1 minute. On your phone, just open and close the app to get the latest version (the service worker will update in the background).

To force an update, bump the `CACHE_NAME` version in `sw.js`:
```js
const CACHE_NAME = "secplus-cards-v2";  // change v1 → v2
```
