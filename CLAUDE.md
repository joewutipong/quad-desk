# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Architecture

Single-file application. Everything lives in `index.html` — HTML structure, embedded `<style>`, and embedded `<script>`. No build system, no framework, no dependencies beyond Google Fonts.

### Data Model

```js
tasks = [{ id, text, q, done }]
// q: "do" | "schedule" | "delegate" | "eliminate"
// persisted to localStorage key: "eisenhower.tasks.v1"
```

### State Flow

1. Load from `localStorage` on startup
2. User actions mutate `tasks` array
3. `save()` — persists to localStorage + triggers render
4. `renderQuad(qid)` — rebuilds DOM for one quadrant
5. `renderStats()` — updates footer counters

### Key Patterns

- **Portal dropdown** — export menu appended to `document.body` to escape stacking context (this was a deliberate fix, don't revert)
- **Theme** — toggled via `data-theme="dark"` on `<html>`, persisted to `localStorage`
- **Drag-and-drop** — native HTML5 drag events; `dragId` tracks in-flight card
- **Inline edit** — double-click spawns auto-growing `<textarea>` in place

### Responsive Breakpoints

| Breakpoint | Layout |
|---|---|
| ≥1500px | Ultrawide padding |
| ≤960px | Tighter spacing |
| ≤720px | Single-column stack |
| ≤560px | Horizontal toolbar scroll |
| height ≤500px | Landscape compact mode |

## Development

No build step. Edit `index.html`, refresh browser.

```sh
# Open locally
start index.html        # Windows
open index.html         # macOS
```

For live-reload during development, use any static server (e.g., `npx serve .` or VS Code Live Server).

## Language

UI is Thai-primary with English sublabels. Quadrant names: ทำเลย (DO), วางแผน (SCHEDULE), มอบหมาย (DELEGATE), ตัดทิ้ง (ELIMINATE).
