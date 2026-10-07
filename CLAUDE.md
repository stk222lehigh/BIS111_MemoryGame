# CLAUDE.md

## Project Overview

This is a **classroom demonstration project**. Its main purpose is to show students, live, how a piece of software goes from an idea to a working product with Claude Code.

- **What the software is and what it does is still open.** The class will decide in open discussion. Until that's settled, don't assume a domain, feature set, or audience.
- Once the class decides, record the decision in the **Project Decision** section below before writing any code.

## Project Decision

> _Decided by the class on 2026-10-06._

- **Software type:** Memory Match, a browser card game (single `index.html`)
- **Purpose / problem it solves:** A quick, casual brain-teaser that exercises short-term memory. Flip cards two at a time to find matching pairs.
- **Target user:** Anyone, any age, casual play. Simple rules, big tappable cards.
- **Card theme:** Emoji, drawn as text, so the game needs no asset files
- **Core features (MVP):**
  1. Flip & match pairs: click two cards. Matches stay face up and mismatches flip back.
  2. Move counter + timer
  3. Win screen + "New Game" restart (reshuffles)
  4. Difficulty levels: Easy 4×3 (6 pairs), Medium 4×4 (8 pairs), Hard 6×4 (12 pairs)
- **Version 2 (`index_v2.html`):** changes chosen from the student feedback survey. See `PATCH-NOTES.md` for what was and wasn't changed, and why. `index.html` stays as version 1.
- **Version 3 (`index_v3.html`), a just-for-fun spinoff of v2:** always played on Hard. There are 24 mildly unsettling, harmless oddities, and one happens every 3–4 moves all game long (e.g. a blinking eye on a card, the title glitching, the lights dimming), then the win screen turns into a goofy "surprise party" in space, with a collection of every oddity spotted while the page is open (hover or tap one for a fun note).
- **Stretch features (only if time allows):** none chosen yet. Candidates: 3D flip animation; best score saved in `localStorage` labeled "You"; Web Audio sound effects; two-player mode ("Player 1" / "Player 2").

## Hard Constraints (Non-Negotiable)

These apply whatever the class chooses to build. If a proposed feature conflicts with any of them, flag the conflict and suggest an alternative that complies. Don't quietly work around it.

### 1. Standalone HTML file (plus an optional asset package)
- The final deliverable is **one `.html` file** that runs by double-clicking it (opened via `file://`) in any modern browser.
- All CSS goes inline in `<style>` tags and all JavaScript in `<script>` tags.
- No build step, bundler, package manager, transpiler, or server is needed to run it.
- The file must work offline with no internet connection.
- **Prefer embedding small media inline** (inline SVG, CSS drawings, or small `data:` URIs) so the HTML stays fully self-contained.
- **An asset package is allowed when needed**, for example for larger images, sounds, or a sample data file that would make the HTML unwieldy if inlined. Rules for the package:
  - All assets go in a single `assets/` folder next to the HTML file. The HTML and `assets/` are shared together, e.g. zipped as one `.zip`.
  - Reference assets only by **relative paths** (`assets/click.mp3`), never absolute paths or URLs.
  - Load assets only through elements that work from `file://`: `<img>`, `<audio>`, `<video>`, CSS `url()`, `@font-face`. **Don't `fetch()` local files.** Browsers block it under `file://`. Put data in a `.js` file loaded with `<script src="assets/data.js">` (e.g. `const SAMPLE_DATA = [...]`) instead of `.json`.
  - If an asset is missing, the app should degrade gracefully (e.g. show a placeholder or skip the sound), not crash.
  - Assets must be created for this project or carry a license that allows redistribution (e.g. CC0). Record the source and license of each asset in `assets/CREDITS.txt`.
  - The privacy rules below apply to assets too: no photos of real people, no real names in data files, and no files with embedded personal metadata (strip EXIF/GPS data from images).
  - Keep the whole package small enough to email or share easily (aim for under ~10 MB; under ~1 MB for the HTML alone).

### 2. No external APIs or resources
- **No network requests of any kind:** no `fetch`, `XMLHttpRequest`, WebSockets, `navigator.sendBeacon`, or similar.
- **No external scripts, stylesheets, or fonts:** no CDNs, Google Fonts, or analytics tags. Use system font stacks (e.g. `system-ui, sans-serif`), or a font file bundled in `assets/` with a license that allows it.
- **No third-party libraries** unless the class explicitly agrees to one. If it does, the library's source must be inlined in full or bundled in `assets/`, and its license must allow redistribution.
- No embedded iframes, maps, or media from other sites.
- No AI/LLM API calls from the app.

### 3. No privacy-sensitive information
- The app must **not collect, ask for, store, or show** personal or sensitive data. This includes:
  - names, email addresses, phone numbers, physical addresses
  - student IDs, grades, or any education records (FERPA-relevant)
  - health, financial, or government-ID information
  - passwords, accounts, logins, or authentication of any kind
  - location, camera, microphone, contacts, or other device permissions
- No tracking, fingerprinting, cookies, or analytics.
- **Sample and demo data must be clearly fictional** (e.g. "Player 1", "Sample Item A"). Never use real student or staff names, even as placeholders.
- If the app needs to save state between sessions, `localStorage` may be used **only for non-personal data** (e.g. settings, a high score labeled "You", or app content the user created). Wrap storage access in `try/catch` so the app still works when storage is unavailable.
- Any text the user enters should stay inside the browser and must never leave it.

## Classroom-Friendly Code Guidelines

The code will be read and discussed in front of a class, so it should be easy to read, not clever.

- **Readable over compact.** Use descriptive names and short functions with one clear job each.
- **Plain, modern JavaScript** (ES2020+) with no frameworks. Use `const`/`let`, never `var`.
- **Organize the file in clearly labeled sections**, in this order:
  1. `<head>`: metadata, title, `<style>`
  2. `<body>`: semantic HTML markup
  3. `<script>` at the end, split into commented sections such as `// ===== State =====`, `// ===== Rendering =====`, `// ===== Event Handlers =====`, `// ===== Initialization =====`
- **Comment the "why," not the "what."** Write a short comment wherever a student might reasonably ask "why is this here?"
- Keep the whole file small enough to scroll through during a lecture. Prefer fewer, well-made features over many half-done ones.
- Avoid `eval`, `innerHTML` with user-provided text (use `textContent`), and inline `on*=` attributes. Attach event listeners in the script.

## UI / UX Requirements

- Works on a **projector**: large default font size (≥ 18px body), high contrast, and controls that are easy to see from the back of the room.
- Responsive layout that works from phone width (~375px) up to a wide screen, with no horizontal scrolling.
- Accessible basics: semantic elements (`<button>`, `<label>`, `<main>`, headings in order), keyboard-operable controls, visible focus styles, `alt`/`aria-label` where needed, and color never used as the only signal.
- A meaningful `<title>` and a short on-screen explanation of what the app does.
- Optional: light/dark theme via `prefers-color-scheme`.

## Development Workflow

1. **Discuss and decide:** the class picks the software type and purpose, and the result is recorded in *Project Decision*.
2. **Plan:** break the MVP into small, demo-able steps. Each step should give a visible change in the browser.
3. **Build step by step:** after each step, the file must still open and work. Explain each change briefly so it can be narrated to the class.
4. **Review:** check the deliverable against the Hard Constraints checklist below.
5. **Share:** hand out the `.html` file, or a `.zip` of it with `assets/` if the project uses one.

### Version control
- The project uses git on the `main` branch. There's no remote; it stays local unless the class decides otherwise.
- **Commit after each working step** with a short message in plain English (e.g. "Add flip animation to cards"), so the class can see the history and roll back a live demo if needed.
- Every commit should leave `index.html` in a working state.
- Never commit personal information, and don't commit `.zip` packages (they're built from the source when shared).

### File layout
```
teaching_sandbox2/
├── CLAUDE.md        # this file: project specs and rules
├── index.html       # the deliverable (rename once the project is chosen)
└── assets/          # optional: only if the project needs it
    ├── CREDITS.txt  # source + license for every asset
    └── ...          # images, sounds, fonts, data.js
```
To share: send `index.html` by itself, or zip `index.html` + `assets/` together (don't include `CLAUDE.md`).
Keep scratch experiments out of the project folder, or delete them before sharing.

## Pre-Share Checklist

Before calling the project done, confirm each item:

- [ ] Exactly one `.html` file, plus at most one `assets/` folder
- [ ] Opens and works from `file://` with Wi-Fi **turned off**, after unzipping the package into a fresh folder
- [ ] Searching the file finds no `http://`, `https://`, `//cdn`, `fetch(`, `XMLHttpRequest`, or `WebSocket`, and every `src=`/`href=`/`url()` points to a relative path inside `assets/`
- [ ] Every file in `assets/` is actually used and listed in `CREDITS.txt` with its license
- [ ] No asset contains personal information or metadata
- [ ] No input fields or stored data involving personal information
- [ ] All sample data is obviously fictional
- [ ] No console errors in the browser's developer tools
- [ ] Readable on a projector and usable on a phone-sized screen
- [ ] Usable with the keyboard alone

## Notes for Claude

- When a feature request is ambiguous, ask a short clarifying question. The discussion is part of the lesson.
- When a requested feature would break a Hard Constraint (e.g. "pull live weather data," "let students log in"), say so plainly and offer a compliant alternative (e.g. bundled sample data, or a local-only profile with no personal fields).
- Favor changes that are easy to demonstrate and explain live.
