# The Thinking Lab — MVP v0.1

A mobile-first, offline-capable Progressive Web App (PWA) for capturing, challenging, and evolving ideas across Science, Build, and Life Labs.

## Features
- Create, edit, search, filter, and delete thoughts.
- Save historical revisions automatically when editing a thought.
- Intellectual sparring prompts tailored to each laboratory.
- Save reflections to prompts; copy a full discussion prompt to ChatGPT.
- Dictation using browser SpeechRecognition where supported; otherwise use Android keyboard microphone.
- JSON export/import and browser-local persistence.
- Installable manifest and service worker for offline use after first load.

## Run locally
From this folder run `python3 -m http.server 8000`, then visit `http://localhost:8000`.

## Install on Pixel
Host this folder on an HTTPS static host (e.g. GitHub Pages, Cloudflare Pages, or Netlify). Open the HTTPS URL in Chrome on the Pixel, then use Chrome's menu > Add to Home screen / Install app. Files opened directly via `file://` won't support service workers.

## Architecture
Vanilla JavaScript + HTML + CSS; `localStorage` holds an array of thought records (`id`, `title`, `body`, `lab`, timestamps, `revisions`, `reflections`). No server, accounts, analytics, or API keys. A service worker caches the app shell. No information is transmitted to AI providers automatically.

## Known limitations / next steps
- Browser storage can be cleared by OS or user; export backups frequently. It is not encrypted and should not be used for sensitive research data or unpublished confidential information without stronger controls.
- Sparring is structured questions, not a live AI assistant. Add a server-side AI endpoint with authentication and privacy controls before enabling AI.
- No cross-device sync, attachments, or collaboration.
- No production test suite or formal security review yet.
- For future scale, migrate to IndexedDB or encrypted server storage and add a real data migration system.
