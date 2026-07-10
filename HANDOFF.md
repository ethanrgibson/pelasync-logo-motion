# Handoff — PelaSync logo motion study

_Written to bring a fresh chat up to speed. This folder is a standalone static site; it is
**not** part of the PatientNotes/PelaSync app codebase (that lives at `~/Downloads/PatientNotes`)._

## What this is

A single-page motion study for the **PelaSync logo**. The static mark is a clay dot inside
two sage rings (concentric, "in sync"). This page animates the rings three different ways,
lets you compare them side by side, adjust tempo, pause, and copy the drop-in code. The goal
was to make the logo feel "active" — rings that pulse outward from the center dot. It's meant
to be shared with a business partner for feedback.

## Files in this folder

- `index.html` — the whole site. Self-contained: inline CSS + vanilla JS, no dependencies,
  no build step, no external assets (favicon is an inline data-URI of the mark).
- `README.md` — public-facing readme + GitHub Pages publish steps.
- `.nojekyll` — tells GitHub Pages to serve the HTML as-is.
- `HANDOFF.md` — this file.

## The mark (geometry + palette)

Pulled straight from the original `pelasync-icon.svg`, on a 64×64 viewBox, all centered at (32,32):

- Outer ring: `r=24`, stroke `#5F9D87` (sage), `stroke-width=4`, opacity `0.35`
- Mid ring: `r=16`, stroke `#5F9D87`, `stroke-width=4`, opacity `0.70`
- Center dot: `r=7`, fill `#C68360` (clay)

Full palette / dark "studio" theme is in the `:root` block of `index.html`.

## The three motions (all pure CSS keyframes)

1. **Sonar** (`mode-ripple`) — thin rings born at the core, ripple outward + fade. Crisp/alert.
2. **Breathe** (`mode-breathe`) — the whole mark gently expands and settles in place. Calm/soft.
3. **Swell** (`mode-swell`) — **the current favorite.** The two real rings stay parked at their
   home positions (logo always legible) while a matching pair sheds outward and dissolves.
   Half-cycle stagger so a ring is always traveling; dot stays anchored. This is "breathe's
   outward swell, but it never pulls back in."

The three share one SVG structure (3 `.ripple` circles + static rings + dot); a mode class on
the `<svg>` decides which animation runs. Swell repurposes the ripple circles by overriding
their radius via the CSS `r` property (to 16 and 24) so the shed rings start exactly on the
static ones.

## Decisions already made (don't re-litigate unless asked)

- Heartbeat was an earlier 3rd option; it was **replaced** by Swell at the user's request.
- Colors must come straight from the icon — no palette changes.
- Motion must honor `prefers-reduced-motion` (reduce → clean static logo, no pulse). Keep this.
- This folder is deliberately separate from the PatientNotes repo.

## Preview locally

Just open `index.html`, or:

```bash
python3 -m http.server 8000   # then open http://localhost:8000
```

## Likely next steps (pick up here)

- **Publish to GitHub Pages** to get a shareable link (steps in `README.md`). User prefers to
  run `git`/`gh` commands themselves — do the file work, hand off the commands.
- **Partner-facing variant** — optionally strip the "Drop-in code" section, add the user's/
  partner's names or a short intro, tune copy for a non-engineer audience.
- **Wire the favorite (Swell) into the actual app** — that work belongs in
  `~/Downloads/PatientNotes` (Vue 3 frontend), likely as the header mark and/or a "syncing"
  indicator. Open question the user flagged: pulse constantly vs. only fire on activity
  (new entry / sync complete).

## Working-style notes for this user

- The user commits code themselves — do the edits, but don't run `git commit`/push; hand off
  the commands.
- Surface non-obvious tradeoffs and let them choose rather than deciding silently.
