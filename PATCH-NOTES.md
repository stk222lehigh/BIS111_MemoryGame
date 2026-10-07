# Memory Match: Patch Notes

## Version 2 (`index_v2.html`), 2026-10-06

Version 2 responds to the class feedback survey on the first prototype (`index.html`, which
is kept unchanged as version 1). There were **29 responses**. Each suggestion was:

1. grouped with similar suggestions,
2. checked against the Hard Constraints in `CLAUDE.md`, and
3. reviewed by the instructor, who chose which changes to build.

**Summary:** 10 changes were made. 4 workable suggestions were not chosen for this version.
2 ways of reading the feedback could not be built because they break our rules, and
3 comments could not be acted on.

---

## ✅ Changes made

### 1. The whole board fits on one screen (no scrolling)
- **Feedback:** 5 students had to scroll to see all the cards, especially in Hard mode.
- **Change:** The page is now exactly one screen tall. The cards resize to fill the space left
  under the controls, so every row and column is always visible.
- **Tested:** All three levels fit with no scrolling on a 1280×720 projector screen, a laptop,
  and a 375-px-wide phone. On extremely short windows the board stops shrinking at a minimum
  size and the page scrolls instead, so cards never become too small to use.

### 2. Bigger pictures
- **Feedback:** 1 student asked for bigger images.
- **Change:** The picture now fills about half of each card's width and grows with the card.
  On large screens cards can be up to 180 px wide (version 1 capped them at about 130 px).

### 3. Faster flip-back after a wrong pair
- **Feedback:** 4 students found the wait after a wrong pair too long. One asked for a click to
  flip the cards back instantly.
- **Change:**
  - The wait is shorter: **0.7 seconds**, down from 1 second.
  - **Clicking any card during the wait** flips the wrong pair back immediately and turns over
    the card you clicked, so fast players never have to wait.
- **Note:** one student thought the delay lasted several seconds. It was actually 1 second, so the
  wait *felt* longer than it was. That's useful to know when designing game timing.

### 4. Flip animation
- **Feedback:** 4 students asked for animations, transitions, or effects when flipping.
- **Change:** Cards now turn over with a 3D flip, made with CSS only (no images or libraries).
- **Accessibility:** if a device has "reduce motion" turned on, cards flip instantly instead.
  Some people get dizzy or sick from on-screen motion.

### 5. Sound effects, with a mute button
- **Feedback:** 2 students asked for sound effects.
- **Change:** Short beeps play for a flip, a match, a miss, and a win. A **🔊 Sound on /
  🔇 Sound off** button turns them off, which matters in a quiet classroom. The game remembers
  the choice.
- **How it fits our rules:** the sounds are generated in code by the browser's built-in audio
  feature, so there are **no sound files** to download or credit.

### 6. Best-scores table (saved on this device only)
- **Feedback:** 3 students asked for a high-score or score table.
- **Change:** The win screen shows your **top 5 scores for that difficulty**: moves, time,
  points, and theme. A new score is highlighted, shown in bold, and labeled "new!".
- **Ranking:** fewest moves first. Time only breaks ties, because moves are the goal (see #7).
- **How it fits our rules:**
  - Scores are saved **only in this browser on this device**. Nothing is sent anywhere.
  - **No names are asked for or stored.** The table is simply "Your best scores".
  - If the browser blocks saving (e.g. private browsing), the game still works. It shows a note
    that scores will reset when the page is closed.

### 7. Moves are the main goal, with a star rating
- **Feedback:** 1 student asked to make moves (not time) the main objective, and 1 asked for a
  reward for playing.
- **Change:**
  - **Moves** is now the largest number on screen. Time is shown smaller.
  - The win screen awards **1 to 3 stars** based on moves per pair:
    - ★★★ for 1.75 moves per pair or fewer
    - ★★ for 2.5 or fewer
    - ★ otherwise

    Even perfect memory needs about 1.6 moves per pair on average, because the first flips are
    blind guesses, so three stars is hard but possible.

  - The intro line now says: "Fewer moves earn more stars!"
  - The stars are also written out in words ("2 of 3 stars") for screen readers.

### 8. Points with a streak bonus
- **Feedback:** 2 students suggested a point system, including points for matches in a row.
- **Change:** Each match earns **10 points × your current streak**: 10 for the first match in a
  row, 20 for the second, 30 for the third, and so on. A wrong pair resets the streak.
  A message under the stats announces each result, e.g. "Match! +30 points (3 in a row 🔥)".

### 9. Pictures that are easier to tell apart
- **Feedback:** 3 students found some animals too similar (e.g. the fox, tiger, and lion faces).
- **Change:** The animal set was replaced. Version 1 used 12 similar-looking *faces*. Version 2
  uses 12 animals with very different shapes and colors: 🐘 🦒 🐢 🐙 🦋 🐝 🦀 🐌 🦉 🐧 🐳 🦩.

### 10. Name labels on cards
- **Feedback:** 1 student suggested a number in the corner of each card, to tell look-alike
  pictures apart.
- **Change:** Each face-up card shows its **name** under the picture (e.g. "Owl"). A name says
  more than a number would, and screen readers now announce "Owl" instead of reading out the
  emoji.
- **Small screens:** labels hide themselves on very small cards (Hard mode on a phone), where
  they would be too small to read.

### 11. Theme picker: Animals, Fruit, or Numbers
- **Feedback:** 5 students wanted customizable card pictures, and 1 suggested numbers instead of
  pictures to make the game harder.
- **Change:** A **Theme** menu offers three built-in sets: **Animals**, **Fruit**, and
  **Numbers** (1–12). Changing the theme deals a new game. The best-scores table records which
  theme each score was played with.
- **How it fits our rules:** every set is built into the file, so nothing is uploaded or
  downloaded. (See "Not possible under our rules" for why uploading your own pictures isn't
  offered.)

> Changes 1 and 2 (fit to screen + bigger pictures) were chosen as one item, so these
> 11 sections cover the 10 changes the instructor selected.

---

## ⏸️ Workable, but not chosen for version 2

These suggestions fit our rules, but the instructor did not pick them for this version. They
remain candidates for a future version.

| Suggestion | Students | Notes for a future version |
|---|---|---|
| **Two-player mode** (take turns; a match earns another turn) | 2 | Would be local only: "Player 1" and "Player 2" on one screen. Medium effort. |
| **Type your own card pairs** | part of the 5 asking for custom content | Text would stay in the browser. Students would need a reminder not to type personal details. Larger effort. |
| **"How to play" instructions** before the first game | 1 | Small effort. The one-line intro and the new on-screen messages partly cover this. |
| **Custom-drawn artwork** instead of emoji | 4 | Hand-drawn pictures built into the file. Large effort, and would add a lot to the file's length. The more distinct animals and the theme picker address part of this request. |

---

## ❌ Not possible under our rules

Some feedback could be read in a way that breaks a Hard Constraint in `CLAUDE.md`. In each case
we built the version that fits the rules instead.

| Suggestion (as it could be read) | Why not | What we did instead |
|---|---|---|
| **Upload your own images or photos** for the cards | **Rule 3 (privacy):** students could upload photos of real people, and photos often carry hidden personal data such as GPS location. | Built-in **theme picker** (#11) |
| **Online multiplayer, or a class-wide leaderboard** | **Rule 2 (no internet)** and **Rule 3 (privacy):** this needs a server and players' names. | Private **best-scores table** on each device (#6). A local two-player mode remains a future option. |

---

## 💬 Feedback that could not be acted on

| Comment | Reason |
|---|---|
| A comment about choosing indicators for a stock analysis | About a different assignment, not this game. |
| A two-word comment mentioning "issues" with no details | Too vague to identify a problem. |
| A request to make the game fit when played through the course website | Not a code change: uploading the file to the course site is a sharing decision. Change #1 (fit to screen) should help the game display well inside a course-site window. |

---

## How version 2 was checked

- **Gameplay:**
  - Matches, mismatches, and the streak bonus (10 → 20, then back to 10 after a miss).
  - Click-to-skip during a wrong pair.
  - Switching difficulty and theme.
  - The win screen.
- **Layout:** no scrolling on any level at projector, laptop, and phone sizes. Dark mode checked.
- **Saving:**
  - Scores were saved and still there after reopening the file from `file://`.
  - With saving blocked, the game still worked and showed its warning note.
- **Rules scan:** no web addresses, no code that contacts the internet, no outside files.
  Only non-personal data is saved.
- **Browser console:** no errors.
- **Bug found and fixed during testing:** on phones, the best-scores table was too wide and cut
  off its last column. It now fits a 375-px screen.

## Known limitations

- **Emoji look different on each device** (Apple, Windows, Android, and so on). That's why the
  name labels help.
- **Best scores belong to one browser on one device.** They don't move between computers, and
  clearing the browser's data erases them.
- **Sound starts only after the first click.** Browsers block sound until the user interacts with
  the page.
- **The file is about twice as long as version 1** (about 910 lines vs. 440). It still follows the
  same labeled sections, but it takes longer to scroll through in a lecture.
