# Memory Match (BIS111 classroom demo)

A browser memory card game, built live in class to show how software goes from an idea to a
working product with [Claude Code](https://claude.com/claude-code). The class chose the game,
its features, and later its improvements, step by step.

Flip two cards at a time to find matching pairs, and clear the board in as few moves as you can.

## How to play

1. Download one of the `.html` files below. (On GitHub, open the file and use **Download raw file**.)
2. Double-click it. It opens in your web browser.

That's it. There's nothing to install, no account, and no internet needed. Each version is a
single self-contained file.

## Versions

| File | What it is |
|---|---|
| [`index.html`](index.html) | **Version 1:** the original prototype. Animal emoji, a move counter and timer, a win screen, and Easy / Medium / Hard levels. |
| [`index_v2.html`](index_v2.html) | **Version 2:** improvements chosen from student feedback. It fits on one screen, adds a flip animation, sound (with mute), a best-scores table, star ratings, streak points, and a theme picker. |
| [`index_v3.html`](index_v3.html) | **Version 3:** a just-for-fun spinoff, always on Hard. Something is a little... off. Then it ends in a surprise space party. |

## Documents

- [`DESIGN-GUIDE.md`](DESIGN-GUIDE.md) ([PDF](DESIGN-GUIDE.pdf)): the project's design rules, explained for non-programmers.
- [`PATCH-NOTES.md`](PATCH-NOTES.md) ([PDF](PATCH-NOTES.pdf)): what changed in version 2, what didn't, and why.
- [`CLAUDE.md`](CLAUDE.md): the instructions Claude Code followed while building the project.

## Design rules

The game follows three rules, described in full in the design guide:

1. **One file.** Everything is in a single HTML file that works offline.
2. **No internet.** The game never sends or loads anything online.
3. **No personal information.** The game never asks for, stores, or shows personal details. The
   only thing saved, on your own device, is your best scores and the mute setting.
