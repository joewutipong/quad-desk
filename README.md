# QuadDesk

Task prioritization board based on the **Eisenhower Matrix** — sort tasks by urgency and importance to focus on what actually matters.

Live demo: https://joewutipong.github.io/quad-desk *(if deployed)*

---

## Features

- **4-quadrant board** — Do, Schedule, Delegate, Eliminate
- **Drag-and-drop** — move tasks between quadrants
- **Inline editing** — double-click any task to edit
- **Dark / light theme** — persisted across sessions
- **Export** — Markdown or JSON
- **Import** — restore from JSON backup
- **Responsive** — works on desktop, tablet, and mobile
- **Offline-ready** — pure client-side, localStorage persistence
- **Thai UI** — bilingual labels (Thai + English)

---

## Usage

No install. No build. Just open:

```
index.html
```

Or serve locally:

```sh
npx serve .
```

---

## Quadrants

| Quadrant | Thai | Meaning |
|---|---|---|
| **DO** | ทำเลย | Urgent + Important → do it now |
| **SCHEDULE** | วางแผน | Important + Not Urgent → plan it |
| **DELEGATE** | มอบหมาย | Urgent + Not Important → hand it off |
| **ELIMINATE** | ตัดทิ้ง | Neither → cut it |

---

## Keyboard Shortcuts

| Key | Action |
|---|---|
| `Enter` | Add task |
| Double-click task | Edit task |
| `Enter` / `Blur` | Save edit |

---

## Changelog

### Fixes

- **fix(dropdown): portal menu to body to fix portrait stacking** — export dropdown now renders outside quadrant containers, fixing z-index issues in portrait orientation
- **fix(dropdown): escape overflow clip on mobile** — dropdown no longer gets clipped by overflow hidden on mobile viewports
- **fix(css): unlock mobile scroll and restore quad overflow** — mobile layout scroll restored; quadrant overflow handling corrected

---

## Tech

Vanilla HTML + CSS + JavaScript. No framework, no build step, no dependencies.

Data stored in `localStorage` under key `eisenhower.tasks.v1`.
