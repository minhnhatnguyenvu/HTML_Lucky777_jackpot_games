# 🎰 Lucky 777 – Casino Royale

A fully browser-based slot machine jackpot game built with pure HTML, CSS, and vanilla JavaScript. No frameworks, no dependencies, no installs — just open and play.

![Lucky 777 Casino](https://img.shields.io/badge/built%20with-HTML%20%2F%20CSS%20%2F%20JS-gold?style=for-the-badge&logo=javascript&logoColor=black)
![License](https://img.shields.io/badge/license-MIT-green?style=for-the-badge)
![Zero Dependencies](https://img.shields.io/badge/dependencies-none-brightgreen?style=for-the-badge)

---

## 🎮 Demo

Open `jackpot-casino.html` directly in any modern browser — no server required.

---

## ✨ Features

### 🎰 Slot Machine
- **3 spinning reels** displaying numbers 1–7
- Smooth reel spin animation with deceleration easing and a satisfying snap-to-number at the end
- **Red payline** across the center of the reels
- Reel tick sounds on every revolution cycle

### 🕹️ Lever
- Fully animated side lever — **click or drag to pull**
- Ball + rod slides **down** with a quick snap, then **springs back up** with a bounce overshoot
- Glows red on hover

### 🏆 Jackpot (3 matching numbers)
- Multi-burst **fireworks** explosion across the full screen with trailing particles
- **60 gold coins** rain down from the top of the screen
- Fullscreen **JACKPOT! banner** animates in with a golden glow
- Reel borders flash gold and amber
- Screen strobes with a flash effect

### 🔊 Web Audio (no audio files needed)
All sounds are generated live using the **Web Audio API**:

| Event | Sound |
|---|---|
| Reel spinning | Subtle square-wave tick |
| Jackpot triggered | Ascending piano chime (C–E–G–C–E) |
| Firework burst | Low noise boom + high-frequency crackle sparks |
| Coin rain | Metallic triangle-wave pings |

### ⚡ Automatic Pulls
- Input **1–30 pulls** and let the machine run automatically
- Every pull plays the **full lever animation + reel spin** — nothing is skipped
- Gold **progress bar** tracks current pull in real time
- Waits for the jackpot celebration to finish before continuing
- After all pulls complete, a **results table** appears with:
  - Pull number
  - All 3 reel results shown as styled badges
  - Outcome: **Miss** or **🏆 JACKPOT!**
  - Summary row: Total pulls / Misses / Jackpots count
  - Jackpot rows highlighted in amber glow
  - Rows animate in with a staggered fade

### 🎨 Casino Aesthetic
- Dark velvet background with gold grid texture
- Animated marquee bulbs across the machine top
- Chrome-styled lever with a polished rod and metal base
- Gold gradient title with neon glow animation
- Pull history tracker (last 3 spins)
- Pay table display

---

## 🚀 Getting Started

### 1. Clone the repo

```bash
git clone https://github.com/yourusername/lucky-777-casino.git
cd lucky-777-casino
```

### 2. Open the game

Simply open the HTML file in your browser:

```bash
open jackpot-casino.html        # macOS
start jackpot-casino.html       # Windows
xdg-open jackpot-casino.html    # Linux
```

Or drag the file into any browser window. That's it — no build step, no npm install.

---

## 🕹️ How to Play

| Action | Control |
|---|---|
| Single spin | Click the **red lever** on the right side of the machine |
| Single spin (keyboard) | `Space` or `Enter` |
| Auto pull | Enter a number (1–30) in the **Automatic Pulls** section and click **Start Auto Pull** |
| Jackpot condition | All 3 reels show the **same number** |

**Odds of hitting a jackpot:** 1 in 49 (7 × 7 = 49 combinations)

---

## 📁 Project Structure

```
lucky-777-casino/
└── jackpot-casino.html     # The entire game — single self-contained file
└── README.md               # This file
```

Everything lives in one file:
- **CSS** — all styles, animations, and responsive layout
- **HTML** — machine cabinet, reels, lever, controls, auto-pull section, results table
- **JavaScript** — game logic, Web Audio engine, fireworks particle system, auto-pull runner

---

## 🛠️ Technical Details

### Reel Animation
Each reel runs an `requestAnimationFrame` loop with a custom easing curve:
- Full speed for the first 60% of the spin duration
- Gradual deceleration from 60% → 100%
- Final snap using a CSS `cubic-bezier` transition to the target number

### Web Audio Engine
All sounds are synthesized at runtime with no external files:
- **Firework boom** — white noise buffer shaped with an exponential gain envelope, filtered through a low-pass filter that sweeps down, plus 7 randomized bandpass crackle bursts
- **Coin tink** — triangle oscillators at random frequencies with pitch drop envelopes
- **Jackpot chime** — 5 sine oscillators tuned to a C major arpeggio, staggered 130ms apart
- **Reel tick** — brief square-wave oscillator burst at randomized low frequency

### Fireworks Particle System
Canvas-based particle engine:
- Each burst spawns 60–100 particles in a circular spread
- Particles have individual gravity, velocity drag, and alpha decay
- 6-frame position trail drawn behind each particle
- 8 bursts fire with randomized delays across the 4-second jackpot window

### Auto Pull Runner
An `async/await` loop that:
1. Plays the lever animation
2. Awaits `doSpin()` which itself returns a Promise resolving after all 3 reels settle
3. Waits 4.3 seconds after a jackpot (to let the celebration play out)
4. Waits 380ms between normal pulls
5. Renders the results table with staggered row animations after all pulls complete

---

## 🌐 Browser Support

| Browser | Support |
|---|---|
| Chrome / Edge | ✅ Full |
| Firefox | ✅ Full |
| Safari | ✅ Full |
| Mobile (iOS / Android) | ✅ Full |

Requires a browser with support for:
- `Web Audio API`
- `Canvas 2D`
- `CSS custom properties`
- `requestAnimationFrame`
- `async/await`

All of these are supported in every major browser since 2018.

---

## 📄 License

MIT License — free to use, modify, and distribute.

---

## 🙏 Acknowledgements

- Fonts: [Cinzel Decorative](https://fonts.google.com/specimen/Cinzel+Decorative) & [Oswald](https://fonts.google.com/specimen/Oswald) via Google Fonts
- Sound design: Web Audio API (no external assets)
- Inspired by classic casino slot machines and pachinko parlor aesthetics
