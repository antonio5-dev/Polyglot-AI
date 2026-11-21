# Polyglot AI – AI Language Teacher with Voice (PWA)

A free, installable web app (PWA) that works as a language teacher: AI conversation, role-play scenarios, mini-lessons with exercises, listen & repeat (dictation), spaced-repetition flashcards, progress tracking and a small "student memory". Pure HTML/CSS/JavaScript: no build, no backend, no libraries.

- **Interface languages (8):** English (default), Português (BR), Español, Français, Deutsch, 中文, 한국어, 日本語
- **Practice languages (8):** English, Brazilian Portuguese, Spanish, French, German, Mandarin Chinese, Korean, Japanese
- **AI:** Google Gemini, called straight from your browser with **your own API key** (get a free one at <https://aistudio.google.com/apikey>)
- **Voice:** Chrome's Web Speech API (text-to-speech and speech recognition)

---

## Option 1 – Use the hosted version (recommended)

**Open the Vercel link of this project** (replace with your own deployment URL):

> `https://YOUR-PROJECT.vercel.app`

Why this is the best way to test: the voice system (microphone / speech recognition) **only works over HTTPS or `localhost`**, with internet access and microphone permission. The Vercel link is HTTPS, so everything works, including installing the app.

1. Open the link in **Google Chrome** (PC or Android).
2. Go to **Settings**, paste your **Gemini API key**, choose your interface language, your native language and the language(s) you practice.
3. Go to **Home** and start a conversation. Allow the microphone when Chrome asks.

### Install as an app (PC and phone)
- Click the green **Install app** button (top of the screen, on Home or in Settings).
- If the button does not appear: Chrome menu **⋮ → "Install Polyglot AI"** (PC: also the install icon at the right end of the address bar; Android: **⋮ → "Add to Home screen" / "Install app"**).

### Uninstall
- **Chrome on PC:** open the app, click **⋮** in its title bar → **Uninstall**. (Or open `chrome://apps`, right-click the app → **Remove**.)
- **Android:** long-press the app icon → **Uninstall** (or Settings → Apps → Polyglot AI → Uninstall).
- Your study data stays in the browser until you clear the site data (Chrome → Settings → Privacy → Site settings → find the site → Clear data). Use **Settings → Export data** first if you want a backup.

---

## Option 2 – Download the files / clone the repository and run locally

1. Download the repository as ZIP from GitHub (**Code → Download ZIP**) and unzip it, or clone it:
   ```bash
   git clone https://github.com/YOUR-USER/YOUR-REPO.git
   cd YOUR-REPO
   ```
2. Start a local web server in that folder:
   ```bash
   python3 -m http.server 8000
   ```
3. Open <http://localhost:8000> in Chrome.

> Do **not** open `index.html` by double-clicking (`file://`): speech recognition and the service worker do not work there. `localhost` is treated as secure, so voice works.

## Deploying your own copy (GitHub → Vercel)
1. Put these files in a GitHub repository: `index.html`, `manifest.json`, `sw.js`, `vercel.json`, `icon-192.png`, `icon-512.png`, `icon-maskable-512.png`, `README.md`, `README.pt-BR.md`.
2. On <https://vercel.com>: **Add New → Project → Import** your repository. Framework preset: **Other**. No build command, no output directory. Click **Deploy**.
3. Every `git push` redeploys automatically. When you change files, bump `CACHE_VERSION` in `sw.js` so installed apps refresh.

---

## Features
- **Free conversation** with corrections (after each message, at the end of the session, or off).
- **Role-play scenarios** (restaurant, airport, hotel, job interview, doctor, shopping, taxi, new friend) with an objectives checklist.
- **Mini-lessons** on any topic: short explanation, 5 audio examples, 3–5 exercises (multiple choice, fill in, translate, word order).
- **Listen & repeat / dictation:** the app speaks a sentence; you type or say it; differences are highlighted.
- **Flashcards** with spaced repetition (1, 3, 7, 14, 30 days; a miss restarts the card).
- **Level test** (A1–C2, with approximate HSK / JLPT / TOPIK equivalents for zh/ja/ko).
- **Progress:** streak, daily goal, minutes per week, words by stage, most frequent mistakes, lesson history, AI-estimated level (labelled as an estimate).
- **Student memory** (max 20 editable items) used by the AI; the AI proposes updates at the end of a session.
- **Voice:** per-language voices, speed 0.5x–2x, "slow" button on each sentence, microphone with target/native language switch, optional hands-free mode.
- Export / import all data as JSON.

## Voice notes
- Voices load asynchronously in Chrome; if a language has no voice, the app shows text only and a tip. On Android install voice data in **Settings → System → Languages → Text-to-speech**.
- The first spoken reply needs a user gesture (a tap) – the app handles this when you press buttons.
- Speech recognition only tells you what the recognizer **understood**. It is **not** a pronunciation score.
- Speech recognition in Chrome sends audio to Google's servers; it needs internet.

## Privacy
- Your API key is stored **only in your browser's localStorage** and sent only to Google's Gemini API. The export file does **not** include it.
- Study data (sessions, vocabulary, mistakes, memory) is stored locally in IndexedDB. There is no backend and no analytics.
- Conversation text is sent to the Gemini API to generate replies. Do not type information you don't want to share with it.

## Requirements
- Google Chrome (recommended; Edge also works). Android for phone use.
- A Gemini API key and an internet connection.
- HTTPS (Vercel) or `localhost` for voice and installation.

## Files
`index.html` (the whole app) · `manifest.json` · `sw.js` (network-first service worker) · `vercel.json` · icons (`icon-192.png`, `icon-512.png`, `icon-maskable-512.png`).
