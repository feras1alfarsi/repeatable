# Loopify — Privacy-First Audio & Video Repeater

**Repeat any audio or video file 1–1000 times. Entirely in your browser. No uploads. No servers.**

---

## Features

- **File Repetition** — Repeat MP3, WAV, M4A, AAC, OGG, MP4, MOV, WEBM files 1 to 1,000 times
- **A–B Loop** — Define a start and end time to repeat only a specific segment
- **Pause Between Reps** — Add 0, 5, 10, 30, or 60 second gaps between repetitions
- **Playback Speed** — 0.5× to 2× speed control
- **Progress Tracking** — Per-repetition counter, overall progress bar, elapsed time, ETA
- **Dark Mode** — Full dark/light theme toggle
- **Bilingual** — English and Arabic (RTL) interface
- **PWA** — Installable as a native-like app on any device
- **Offline** — Works without internet after first load
- **100% Private** — Zero server contact for media data

---

## Installation

### Deploying the Web App

The entire app is a single HTML file with companion assets. Deploy it anywhere:

**Option 1 — GitHub Pages (free)**
```bash
# Create a new repo, push all files, enable GitHub Pages in Settings → Pages
git init && git add . && git commit -m "Initial" && git push origin main
```

**Option 2 — Netlify (drag & drop)**
1. Go to netlify.com → Sites → Drag the `loopify/` folder
2. Done. Live in seconds.

**Option 3 — Vercel**
```bash
npm install -g vercel
cd loopify
vercel --prod
```

**Option 4 — Local server (development)**
```bash
# Python
python3 -m http.server 8080

# Node.js
npx serve .

# Then open http://localhost:8080
```

> **Note:** The app must be served over HTTP/HTTPS (not opened as a `file://` URL) for PWA and Service Worker features to work.

---

## PWA Installation — User Instructions

### Desktop (Chrome, Edge)
1. Open the app URL in Chrome or Edge
2. Look for the **install icon** (⊕) in the address bar — click it
3. Or use the **Install banner** that appears at the bottom
4. Click **Install** in the confirmation dialog

### iPhone / iPad (Safari)
1. Open the app URL in Safari
2. Tap the **Share** button (box with arrow)
3. Scroll down and tap **Add to Home Screen**
4. Tap **Add**

### Android (Chrome)
1. Open the app URL in Chrome
2. Tap the **three-dot menu** (⋮)
3. Tap **Add to Home screen** or **Install app**
4. Tap **Install**

---

## Files

```
loopify/
├── index.html      — Main application (all logic, UI, styling)
├── manifest.json   — PWA manifest
├── sw.js           — Service worker (offline caching)
├── icon-192.svg    — App icon 192×192
├── icon-512.svg    — App icon 512×512
└── README.md       — This file
```

---

## Browser Compatibility

| Browser         | Audio | Video | PWA Install | Offline |
|-----------------|-------|-------|-------------|---------|
| Chrome 90+      | ✅    | ✅    | ✅          | ✅      |
| Edge 90+        | ✅    | ✅    | ✅          | ✅      |
| Firefox 88+     | ✅    | ✅    | ❌          | ✅      |
| Safari 14+ iOS  | ✅    | ✅    | ✅          | ✅      |
| Safari macOS    | ✅    | ✅    | ✅          | ✅      |
| Samsung Browser | ✅    | ✅    | ✅          | ✅      |

> **MOV files** on non-Safari browsers may not be supported due to codec limitations. Use MP4 as a universal alternative.

---

## Supported Formats

| Format | Type  | Notes                              |
|--------|-------|------------------------------------|
| MP3    | Audio | Universal support                  |
| WAV    | Audio | Universal support                  |
| M4A    | Audio | Safari/Chrome; Firefox limited     |
| AAC    | Audio | Wide support                       |
| OGG    | Audio | Firefox/Chrome; not Safari         |
| MP4    | Video | Universal support (H.264/H.265)    |
| WEBM   | Video | Chrome/Firefox; limited Safari     |
| MOV    | Video | Safari best; others vary           |

---

## Keyboard Shortcuts

| Key         | Action              |
|-------------|---------------------|
| `Space`     | Play / Pause        |
| `S`         | Stop                |
| `→`         | Skip to next rep    |
| `←`         | Go to previous rep  |

---

## Privacy Architecture

- **No server contact** — Media files are loaded using the browser's File API and played via `URL.createObjectURL()`. They never leave the device.
- **No analytics** — No tracking scripts, no third-party resources loaded at runtime.
- **No storage** — No localStorage, no IndexedDB, no cookies used for media.
- **No network requests** — After initial page load, the service worker serves everything from cache.

---

## Architecture Notes

The app is intentionally a **single HTML file** with embedded CSS and JavaScript. This approach:
- Maximizes portability (one file to deploy/share)
- Eliminates build steps and dependencies
- Simplifies offline caching
- Keeps the codebase auditable (users can inspect the source directly)

Key APIs used:
- `File API` — Read file from disk
- `URL.createObjectURL()` — Create in-memory URL for local file
- `HTMLMediaElement` — Native audio/video playback with full control
- `Service Worker` — Offline caching and PWA lifecycle
- `Web App Manifest` — PWA metadata, icons, installation

---

## Accessibility

- All interactive elements are keyboard-accessible
- `aria-label` attributes on icon-only buttons
- Sufficient color contrast in both light and dark mode
- Respects `prefers-reduced-motion` for animations
- RTL layout fully supported for Arabic

---

## License

MIT — free to use, modify, and distribute.
