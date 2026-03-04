# KB Forge — Kettlebell Workout Generator

A mobile-friendly, single-page web app that generates balanced kettlebell workouts from a curated library of 30 exercises across 6 movement categories. Built for strength and hypertrophy training with configurable session durations.

**[Live Demo →](https://yourusername.github.io/kb-forge/)** *(update this link after deploying)*

---

## Features

### Workout Generation
- **30 exercises** across 6 categories: Posterior Chain, Quad Dominant, Upper Push, Upper Pull, Core, and Full Body
- **3 training goals** — Strength (heavy/low rep), Hypertrophy (moderate/high rep), or Mixed — each with tailored sets, reps, and rest timing
- **3 session types** — Balanced, Lower Focus, or Upper Focus — adjusting which movement categories are included
- **2 durations** — ~25 min (5 exercises) or ~45 min (7 exercises with scaled volume)
- **Optimal exercise ordering** — most demanding compound movements are placed first while you're freshest (full body → posterior → quad → push → pull → core)
- **No duplicate exercises** — the generator won't pick the same exercise twice, even when a category appears multiple times in longer sessions
- **Per-side indicators** — unilateral exercises display an "EACH SIDE" badge

### Spinning Wheel
- Roulette-style category wheel spins for 2 seconds during workout generation

### Preview & Customize
- Review the generated workout before committing
- **Swap individual exercises** within their category (↻ button)
- **Reforge** to generate an entirely new workout
- **Accept** to lock in and start

### Active Workout Tracking
- **3-2-1 countdown** (full-screen overlay, tap anywhere to skip)
- **Per-set checkboxes** — tap to mark each set complete; card fades when all sets are done
- **45-second rest timer** — automatically starts when you check a set; circular ring depletes with color changes at 5 seconds; skip anytime
- **Complete Workout** button available at any time; confirms if sets remain incomplete
- **Cancel Workout** button to abandon without logging

### Workout Log
- **Persistent history** saved to localStorage across browser sessions
- **Exercise × Session matrix** — all 30 exercises as rows, sessions as columns, with ✕ marks showing which exercises appeared in each workout
- **Color-coded category dots** for quick visual scanning
- **Clear log** option to reset all history

### Duration & Goal Scaling

| Setting | ~25 Min | ~45 Min |
|---------|---------|---------|
| **Strength** | 5 exercises, 2 sets each | 7 exercises, 2 sets each (volume from extra exercises) |
| **Hypertrophy** | 5 exercises, 3 sets each | 7 exercises, 4 sets each (+1 set bump) |
| **Mixed** | 5 exercises, 2–3 sets each | 7 exercises, 3–4 sets each (+1 set bump) |

Time estimates account for goal-specific rest periods: strength uses longer rest (90–120s per set), hypertrophy uses shorter rest (45–60s per set).

---

## Deploy to GitHub Pages

1. **Create a new repository** on GitHub (e.g., `kb-forge`)
2. **Upload both files** — `index.html` and `README.md` — to the root of the repository
3. Go to **Settings → Pages**
4. Under **Source**, select **Deploy from a branch**
5. Choose the **main** branch and **/ (root)** folder
6. Click **Save**
7. Your app will be live at `https://yourusername.github.io/kb-forge/` within a few minutes
8. Update the demo link at the top of this README with your actual URL

### Alternative Hosting

This is a single static HTML file with no dependencies, so it works on any static host:

- **Netlify** — drag and drop the file at [app.netlify.com/drop](https://app.netlify.com/drop)
- **Vercel** — deploy from a GitHub repo or CLI
- **Cloudflare Pages** — connect a repo or direct upload
- **Local** — just open `index.html` in any browser

---

## Exercise Categories

| Category | Focus | Example Exercises |
|----------|-------|-------------------|
| Posterior Chain | Glutes, hamstrings, erectors | Double KB Deadlift, Single-Leg RDL, Heavy Swing |
| Quad Dominant | Quads, glutes, adductors | Double Front Squat, Goblet Squat, Bulgarian Split Squat |
| Upper Push | Shoulders, chest, triceps | Military Press, Push Press, Floor Press |
| Upper Pull | Lats, upper back, traps | Gorilla Row, Renegade Row, High Pull |
| Core | Obliques, deep stabilizers | Turkish Get-Up, Suitcase Carry, Windmill |
| Full Body | Total body compound | Clean and Press, Snatch, Heavy Swing, Armor Building Complex |

The Heavy Two-Hand Swing appears in both Posterior Chain and Full Body pools, increasing its selection probability.

---

## Customization

All exercise data lives in the `exercises` object at the top of the `<script>` block in `index.html`. To add or modify exercises:

```javascript
posterior: [
  {
    name: "Your Exercise",
    muscles: "Target muscles",
    note: "Coaching cue or tip.",
    sets: { s: 2, h: 3, m: 2 },     // sets per goal (s=strength, h=hypertrophy, m=mixed)
    reps: { s: 5, h: 10, m: 8 },    // reps per goal
    unit: "reps",                     // optional: "reps", "30m", or "complex"
    unilateral: true                  // shows "EACH SIDE" badge if true
  },
]
```

Other configurable values:

- **Rest timer duration** — change `REST_DURATION` constant (default: 45 seconds)
- **Exercise ordering** — modify `catOrder` object to change which categories are performed first
- **Session composition** — edit `getCats()` to change how many and which categories appear per session type and duration
- **Colors and fonts** — CSS variables at the top of the `<style>` block

---

## Tech Stack

- **Pure HTML/CSS/JS** — no frameworks, no build tools, no server
- **Google Fonts** — Bebas Neue, Space Mono, Outfit
- **localStorage** — persistent workout logging
- **CSS/SVG animations** — wheel spin, countdown pulse, rest timer ring, card stagger

---

## License

MIT — use it, fork it, modify it however you like.
