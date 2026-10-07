# Memory Match: The Design Rules in Plain English

This guide explains the rules in `CLAUDE.md` for readers who don't write code.
`CLAUDE.md` is the instruction sheet that Claude (the AI assistant) follows while building
this project. Think of it as the **project brief** you would give to a builder: what to
build, what materials are allowed, and what is off-limits.

---

## 1. What we're building, and why

This is a **classroom demonstration**. The goal is to show students, live, how software goes
from an idea to a working product.

The class chose to build **Memory Match**, the classic card game:

- A grid of cards is laid face down. Each picture appears on exactly two cards.
- You turn over two cards at a time. If they match, they stay face up.
  If not, they flip back after one second.
- You win when every pair has been found.

**Who it's for:** anyone, of any age, playing casually.

**What the finished game includes:**

| Feature | What it means for the player |
|---|---|
| Flip & match | The core game described above |
| Moves and timer | Shows how many tries you've taken and how long you've played |
| Win message and restart | A "You won!" box, plus a button to shuffle a new game |
| Difficulty levels | Easy (12 cards), Medium (16 cards), Hard (24 cards) |

The pictures on the cards are **animal emoji** (🐶 🐱 🦊 🐼 …). Emoji are built into every
device, so we don't need to supply any image files.

---

## 2. The three non-negotiable rules

These rules apply to the project whatever it turns out to be. If an idea breaks one of them,
the idea changes, not the rule.

### Rule 1: Everything lives in a single file

The whole game is **one file** (`index.html`). You open it by double-clicking it, like a
document, and it opens in your web browser.

- **No installing anything.** There's no app store, no setup program, and no account.
- **No internet needed.** It works on a plane, or in a classroom with bad Wi-Fi.
- **Easy to share.** You can email it, put it on a USB stick, or post it to a class page.

> 🧳 **Analogy:** a self-contained board game in one box, with nothing sold separately.

The rules allow one exception. If a future project needs larger pictures or sounds, they may
go in a single `assets` folder next to the file, and the two are shared together as one zip.
Each of those files must be **ours, or free to share**, and its source must be written down in
a credits list. Memory Match didn't need this: it really is just one file.

### Rule 2: The game never talks to the internet

The game never sends or receives anything online.

- It doesn't load fonts, pictures, or code from other websites.
- It has no ads, no analytics, and no "phone home".
- It has no AI features calling out to online services.

**Why it matters:**
- **Reliability.** A website that changes or goes down elsewhere can't break the game.
- **Privacy.** If nothing leaves the computer, nothing can leak.
- **Teaching.** Everything the game does is visible in the one file, so the class can read all of it.

> 🏝️ **Analogy:** the game is an island with no bridges. Nothing comes in and nothing goes out.

### Rule 3: No personal information, ever

The game must never **ask for, store, or display** personal details. That includes:

- names, email addresses, phone numbers, or home addresses
- student ID numbers or grades (school records are protected by law; in the U.S. that law is called FERPA)
- health, money, or government-ID details
- passwords or logins of any kind
- access to the camera, microphone, location, or contacts

There is also no tracking and no cookies. Any example data must be **obviously made up**
(e.g. "Player 1"), never a real student's or teacher's name, even as a placeholder.

The rules do allow the game to remember **harmless things**, like a preferred setting or a
best score labeled "You", on the player's own computer. Memory Match currently remembers
nothing at all: close the tab and it's a fresh start.

> 🔒 **Why so strict?** This project is shown in a classroom and shared with students.
> The safest personal data is the data we never collect.

---

## 3. Built to be read aloud

Students will watch the project being built and read along, so `CLAUDE.md` asks for
instructions that are easy to follow:

- **Clear over clever.** Names describe what things are (`moves`, `startTimer`), not cryptic abbreviations.
- **Labeled sections.** The file is organized like a textbook chapter: appearance first, then
  the page layout, then the game's behavior, each under its own heading.
- **Notes explain *why*.** Short notes in the file answer the questions a student might ask,
  like "why is this here?"
- **Fewer, finished features.** It's better to have four features that work well than ten half-done ones.

---

## 4. Designed for a projector and for everyone

The game has to work on a classroom projector, on a phone, and for people who use their
computers in different ways.

| Requirement | Why | How Memory Match does it |
|---|---|---|
| **Big text, strong contrast** | It must be readable from the back of the room | Large fonts, dark text on a light background |
| **Works on any screen size** | Some students play on phones | The card grid shrinks to fit, with no sideways scrolling |
| **Works without a mouse** | Some people use only a keyboard | Tab moves between cards, Enter flips them, and a bright outline shows where you are |
| **Works with screen readers** | Blind and low-vision players use software that reads the screen aloud | Each card announces itself, e.g. "Card 3, face down" |
| **Color is never the only clue** | Some people are color-blind | Matched cards turn green **and** show a ✓ mark |
| **Explains itself** | A first-time player shouldn't need instructions | A one-line description sits under the title |
| **Dark mode** (optional) | Easier on the eyes in a dark room | It switches automatically when the device is set to dark mode |

---

## 5. How the project gets built

`CLAUDE.md` sets out five stages. This is the path the class followed:

1. **Discuss & decide.** The class chose the game, the audience, and the features.
   The decisions were written into `CLAUDE.md` *before* any building started.
2. **Plan.** The work was split into small steps, and each step produced something
   visible in the browser.
3. **Build step by step.** After every step the game had to open and work.
   Each step was explained as it happened.
4. **Review.** The finished file is checked against a checklist (see below).
5. **Share.** The file is handed out.

### Saving checkpoints ("version control")

After each working step, the project is saved as a **checkpoint** with a short plain-English
note, like *"Add move counter and timer"*. This works like save points in a video game:

- The class can look back and see how the game grew, one step at a time.
- If something breaks during a live demo, we can return to the last good checkpoint.
- Every checkpoint is a working game. We never save a broken one.

The checkpoints stay on the teacher's computer. Nothing is uploaded online.

---

## 6. The pre-share checklist, in plain words

Before the game is handed out, someone confirms each of these:

- ☐ It's **one file**, plus at most one `assets` folder.
- ☐ It **works with Wi-Fi turned off**.
- ☐ The file contains **no web addresses** and **no code that reaches the internet**.
- ☐ Every extra file (if any) is **actually used** and **credited**.
- ☐ No extra file contains **hidden personal details**, such as the location data some photos carry.
- ☐ The game **never asks for personal information**.
- ☐ All sample names and data are **clearly made up**.
- ☐ The browser reports **no errors**.
- ☐ It's **readable on a projector** and **usable on a phone**.
- ☐ It can be **played with the keyboard alone**.

---

## 7. When someone asks for something that breaks a rule

The rules also say what to do when an idea conflicts with them: **say so plainly, and offer
an alternative that fits the rules.** For example:

| Request | Problem | Alternative that follows the rules |
|---|---|---|
| "Show the live weather on the cards" | Needs the internet (Rule 2) | Use a built-in set of weather emoji ☀️🌧️❄️ |
| "Let students log in to save their scores" | Logins are personal data (Rule 3) | Save one best score on this computer, labeled "You" |
| "Put our class photos on the cards" | Photos of real people (Rule 3) | Use drawings, emoji, or free-to-use images |
| "Add a leaderboard with everyone's names" | Names plus online sharing (Rules 2 and 3) | A local "Player 1 vs Player 2" mode on one screen |

---

*This guide summarizes `CLAUDE.md`. If the two ever disagree, `CLAUDE.md` is the
official version.*
