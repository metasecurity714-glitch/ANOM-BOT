# ANOM — Pixel Cat Companion v2

A GitHub Pages-ready virtual cyber-cat companion. ANOM is now a crisp pixel-art cat robot with expressive moods, touch interactions, affection/energy stats, local memory, voice input/output (browser support required), small games, and a lightweight offline Q&A brain.

## Run locally

Open `index.html` in a modern browser, or use VS Code Live Server. No build step is required.

## Publish on GitHub Pages

1. Create a repository (for example `ANOM`).
2. Upload the contents of this folder to the repository root.
3. Open **Settings → Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**, branch `main`, folder `/ (root)`, then Save.

## Interactions

- Tap/pet ANOM's head or body for an affectionate response.
- Tap the nose area for a surprised boop.
- Use Pet, Boop, Play, and Treat controls.
- Affection and energy persist in this browser.
- Save facts in the memory box; they remain in localStorage and can be deleted.
- Basic questions, greetings, simple arithmetic, capitals, jokes, and companion chat work offline.
- Voice uses Web Speech APIs. Recognition availability varies by browser; Chrome is recommended.

## Optional real AI backend

The frontend attempts `POST /api/chat` and gracefully falls back to its local response engine when no backend is available. GitHub Pages is static hosting and cannot run `server.js`. To enable a real AI model, deploy the included Node backend separately and configure its API key as a server environment variable. Never put a secret API key in `app.js` or any GitHub Pages file.

## Privacy

Memories, affection, energy, and appearance settings are stored locally in this browser using `localStorage`. Clearing site data removes them. This is not cloud sync.
