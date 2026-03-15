# MathQuest

A single-file MathQuest game (Index.html) featuring engaging UX and gameplay enhancements.

## Key Features & Upgrades (v1.1.0)

### 🛠 Wrong-Answer Review
- **In-place Feedback:** No disruptive modals.
- **Visual Cues:** Option buttons are locked and color-coded immediately upon submission. Correct answers are marked green (✓), and wrongly-selected answers are marked red (✗).
- **Flow:** The check button transforms into "Verstanden! Weiter 💪" to allow the player to review before starting a fresh task.

### 💾 LocalStorage Persistence
- **Auto-Save:** Score, streak, and recent-answer history are written to `localStorage` key `mathquest_v1_1_0` after every action.
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
Three tiers offset from level thresholds to manage progression:

| Score | Options | Correct |
| :--- | :--- | :--- |
| 0–29 | 2 | 1 |
| 30–69 | 4 | 1–2 |
| 70+ | 5 | 1–2 |

- **Anti-Frustration Mechanic:** If a player gets ≥3 wrong in the last 5 answers, the difficulty tier drops by 1 temporarily.
- **Dynamic Options:** `generateEqOptions` and `generateSolOptions` now support explicit parameters for correct and wrong counts.