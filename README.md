# ANOM — Virtual AI Companion 🤖

A cute 3D robot companion built with Three.js, vanilla HTML/CSS/JavaScript, browser speech APIs, local memory, and an optional Node.js AI backend.

## Features

- Animated 3D robot rendered with Three.js (CDN module)
- Wave, dance, sleep and cheer animations
- Mood states and friendly demo-mode replies
- Text chat and optional AI replies through a private backend
- Speech input (Web Speech API) and spoken replies (Speech Synthesis)
- Local memory bank stored in browser LocalStorage
- Three mini-games: Number Quest, Reaction Rush and Color Memory
- Robot color, personality, voice and reduced-motion settings
- Responsive layout for mobile and desktop

## Run locally

1. Install Node.js 18 or newer.
2. In this folder, run:

   ```bash
   npm install
   ```

3. Optional: copy `.env.example` to `.env` and set `OPENAI_API_KEY`.
4. Start the server:

   ```bash
   npm start
   ```

5. Open `http://localhost:3000`.

Without an API key, ANOM still works in demo mode with local responses, robot animations, browser voice, memory and games.

## Connect a real AI brain

The server reads secrets from environment variables:

- `OPENAI_API_KEY` — required for AI replies
- `AI_MODEL` — optional model name (defaults to `gpt-4o-mini`)
- `AI_BASE_URL` — optional OpenAI-compatible Chat Completions URL
- `PORT` — optional server port

Do not put an API key in `app.js`, `index.html`, GitHub Pages files, or any public repository. Deploy `server.js` to a backend host that supports Node.js and environment secrets. Set the frontend's `/api/chat` request to your backend URL if the frontend and backend are hosted separately. For example, replace `fetch('/api/chat', ...)` in `app.js` with your backend's HTTPS `/api/chat` URL. Configure CORS on the backend if the frontend and backend use different origins.

## Publish the frontend on GitHub Pages

GitHub Pages can host the static frontend, but it cannot run the Node.js server. For Pages-only hosting:

1. Create a GitHub repository and upload `index.html`, `styles.css`, and `app.js`.
2. Open **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, select `main` and `/ (root)`, then save.
4. Wait for the Pages URL to appear.

The static site will run in demo mode unless you connect it to a separately hosted backend. GitHub Pages uses HTTPS, which is important for microphone permissions and browser speech features.

## Browser notes

- Chrome/Edge generally provide the best Web Speech API support. Voice recognition support varies by browser and device.
- Three.js is loaded from jsDelivr, so the first load needs an internet connection.
- Memory and settings are stored in the current browser on the current device. They do not automatically sync between devices.
- This starter does not upload memories to a database. When AI is enabled, the current saved-memory list is sent to your configured backend along with each message so ANOM can use it as context.

## Project structure

```text
anom-virtual-companion/
├── index.html
├── styles.css
├── app.js
├── server.js
├── package.json
├── .env.example
├── .gitignore
└── README.md
```

## Safety and privacy

Keep API credentials in your backend environment settings. Do not commit `.env`. The memory bank is editable and deletable in the browser. Avoid saving passwords, financial details, or other sensitive information in companion memory.
