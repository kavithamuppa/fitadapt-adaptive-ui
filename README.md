# FitAdapt – AI-Based Adaptive Fitness Tracker

> **University of the Cumberlands**
> Course Project | AI-Based Human-Computer Interaction

---

## What is FitAdapt?

FitAdapt is a browser-based **Adaptive User Interface (AUI)** that automatically changes its entire visual appearance and layout based on how you interact with it — in real time, with no manual configuration required.

This project was built as a demonstration of **AI-Based Adaptive Human-Computer Interaction (HCI)** — where a system observes user behavior and mutates its own interface to better serve that specific user.

---

## Live Demo

Simply open `src/index.html` in any modern browser. No build step. No server. No dependencies.

---

## What Adapts and Why

| User Behavior Detected | Visual + Layout Adaptation |
|---|---|
| Completing workouts consistently | Green energetic theme · Denser layout · Bold typography · 4-column stats |
| High activity streak (7+ days) | Dark intense orange theme · Sidebar collapses to icons · Max density · Performance panel unlocked |
| Skipping 3+ workouts | Warm amber recovery theme · Spacious layout · Larger gentle font · Recovery plan shown |
| Injury mode toggled | Instantly switches entire UI to recovery layout |
| Beginner score (0–34) | Soft blue calm theme · Simple 2-column stats · Expanded sidebar with labels |

### The 6 Things That Change Every Level Transition

1. **Color theme** — entire palette swaps (blue → green → dark orange → amber)
2. **Font size** — scales from 17px (recovery) down to 13px (advanced)
3. **Font weight** — from light 500 (recovery) up to heavy 900 (advanced)
4. **Layout density** — card padding, spacing, stat grid columns all change
5. **Sidebar width** — expands in recovery (220px), collapses to icons in advanced (56px)
6. **Visible sections** — Performance Metrics panel appears only in advanced; Recovery Plan appears only in recovery mode

---

## How to Test It

### Quick Test (30 seconds)
1. Open `src/index.html` in your browser
2. Go to **Settings** tab
3. Click **"7-day streak"** → watch the entire UI go dark and intense (Advanced mode)
4. Click **"3 skips"** → UI switches to warm Recovery mode
5. Check **Adapt Log** to see every change with timestamps and reasons

### Real Interaction Test
1. Go to **Dashboard**
2. Click **"Complete All"** workouts each day
3. Watch your level score climb and the UI adapt progressively

---

## File Structure

```
fitadapt-adaptive-ui/
├── src/
│   └── index.html        # Full application (single-file, no dependencies)
├── README.md             # This file
└── APA_Report.docx       # Academic report (APA format, 5-7 pages)
```

---

## Technical Architecture

FitAdapt is built with **pure HTML, CSS, and JavaScript** — no frameworks, no libraries.

### Adaptive Engine
The core engine is a JavaScript state object (`ST`) that tracks:
- Workouts completed
- Days skipped
- Current streak
- Calories burned
- Session score (weighted formula)

Every interaction recalculates a **level score** using:
```
score = (completions × 8) + (streak × 12) + (calories ÷ 50) − (skips × 10)
```

### Level Thresholds
| Score | Level | UI Mode |
|---|---|---|
| 0–34 | Beginner | Soft blue, spacious |
| 35–74 | Intermediate | Green, balanced |
| 75–100 | Advanced | Dark orange, dense |
| Skips ≥ 3 OR injury flag | Recovery | Warm amber, gentle |

### CSS Variable System
All adaptations are driven by CSS custom properties that change when a class is applied to `<body>`:
```css
body.advanced {
  --font-size:  13px;
  --wt-title:   800;
  --bg:         #0d0f14;
  --primary:    #f97316;
  --spacing:    0.7rem;
  ...
}
```
This means a single `document.body.className = level` line triggers the entire visual transformation.

---

## Key Concepts Demonstrated

### Adaptive User Interface (AUI)
A system that modifies its own layout, content, and visual properties based on user behavior — without manual reconfiguration.

### Intelligent User Interface (IUI)
AUIs powered by AI or AI-informed heuristics. FitAdapt uses a weighted behavioral scoring model to determine adaptation triggers.

### AI-Based HCI
The application of computational intelligence to personalize the human-computer interaction experience in real time.

---

## Adaptation Log
Every change FitAdapt makes is recorded in the **Adapt Log** panel with:
- What changed
- Why it changed
- Timestamp
- Whether it was AUTO (AI-triggered) or USER (manual)

This ensures full **transparency** — a core principle of ethical adaptive design.

---

## Challenges Solved

| Challenge | Solution |
|---|---|
| Adapting too fast felt jarring | Added score thresholds — level only changes after sufficient behavioral evidence |
| Users felt they lost control | Manual override and injury toggle give users full control at any time |
| Too many changes at once felt overwhelming | Changes cascade from CSS variables — smooth 0.4s transitions throughout |

---

## Technologies Used

- **HTML5** — Structure and semantic markup
- **CSS3 Custom Properties** — Theme engine (all visual adaptation)
- **Vanilla JavaScript** — Behavioral tracking and adaptive logic
- **No external libraries** — Fully portable, runs anywhere

---

## AI Tool Disclosure

Claude (Anthropic, claude.ai) assisted with:
- Reviewing the CSS variable architecture
- Suggesting the weighted scoring formula
- APA report formatting guidance

All code, design decisions, and analysis are the author's original work.

---

## Academic References

- Brusilovsky, P., & Millán, E. (2007). User models for adaptive hypermedia. Springer.
- Findlater, L., & McGrenere, J. (2004). A comparison of static, adaptive, and adaptable menus. *CHI '04*.
- Gajos, K. Z., et al. (2010). Automatically generating personalized user interfaces. *Artificial Intelligence, 174*(12–13).
- Lavie, T., & Meyer, J. (2010). Benefits and costs of adaptive user interfaces. *IJHCS, 68*(8).
- Shneiderman, B., et al. (2016). *Designing the user interface* (6th ed.). Pearson.

---

## Author

**[Your Name]**
School of Computer Science and Information Technology
University of the Cumberlands
