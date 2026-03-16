# MathQuest

A single-file MathQuest game (Index.html) featuring engaging UX and gameplay enhancements.

## Key Features & Upgrades (v4.1.1)

### 🧮 Inequalities Game (Ungleichungen knacken)
The game now focuses on linear inequalities with a two-phase gameplay loop:

- **Phase 1 – Identify the Equation:** Given a verbal German-language description of a linear inequality (e.g. "Das Dreifache einer Zahl vermindert um 5 ist kleiner als …"), the player selects the correct algebraic form(s) from the options.
- **Phase 2 – Find the Solution:** Given the algebraic inequality identified in Phase 1, the player selects the correct solution(s) (e.g. `x < 3`).
- **Progress Indicator:** A two-step visual indicator (① → ②) shows where the player is within each task.

### 🗣 Natural-Language Math Generator (MathGen)
A built-in generator (`MathGen`) produces varied German-language verbal descriptions of linear inequalities:
- Coefficients `a`, `c` are randomly chosen from ±[2, 9] (never 0, 1, or −1), ensuring the inequality direction may or may not flip when solved.
- Constants `b`, `d` are chosen so the solution `x_limit` is always a whole number in [−10, 10].
- Multiple phrasing templates per term structure (e.g. "Subtrahiert man … vom …", "Das … einer Zahl verringert um …", "Die Summe aus … und dem …") ensure variety.

### 🛠 Wrong-Answer Review
- **In-place Feedback:** No disruptive modals.
- **Visual Cues:** Option buttons are locked and color-coded immediately upon submission. Correct answers are marked green (✓), and wrongly-selected answers are marked red (✗).
- **Flow:** The check button transforms into "Verstanden! Weiter 💪" to allow the player to review before starting a fresh task.

### 💾 LocalStorage Persistence
- **Auto-Save:** Score, streak, and recent-answer history are written to `localStorage` key `mathquest_v4_1_1` after every action.
- **Session Recovery:** The `loadState()` function restores previous sessions transparently on page load.

### 🏆 Level-up Ceremony
Features 9 levels at regular 50-point intervals with a celebratory overlay:

| Points | Level | Badge |
| :--- | :--- | :--- |
| 0 | Anfänger | 🌱 |
| 50 | Entdecker | ⭐ |
| 100 | Rechenkünstler | 🏅 |
| 150 | Profi | 🥈 |
| 200 | Experte | 🥇 |
| 250 | Meister | 🏆 |
| 300 | Mathe-Ninja | 🥷 |
| 350 | Legende | 👑 |
| 400 | Mathe-Gott | ✨ |

- **Celebration:** Reaching a threshold triggers a full-screen overlay with a bounce-in icon, shimmer-gold level name, German congratulatory message, 90-piece confetti rain, and a pulsing "🚀 Weiter geht's!" button.

### 📈 Adaptive Difficulty
Three tiers offset from score thresholds to manage progression:

| Score | Options | Correct |
| :--- | :--- | :--- |
| 0–29 | 2 | 1 |
| 30–69 | 4 | 1–2 |
| 70+ | 5 | 1–2 |

- **Anti-Frustration Mechanic:** If a player gets ≥3 wrong in the last 5 answers, the difficulty tier drops by 1 temporarily.
- **Duplicate-Free Options:** `generateEqOptions` and `generateSolOptions` deduplicate generated options using a `Set` of display texts before presenting them to the player (bug fix from v4.1.0).