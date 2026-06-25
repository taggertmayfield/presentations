[README (1).md](https://github.com/user-attachments/files/29340241/README.1.md)
# presentations

**Taggert Mayfield — Interactive Presentations**

A catalog of self-contained, interactive technical presentations. Each one takes a
subject worth understanding and turns it into something you can poke at, scrub through,
and explore — no slideshows, no frameworks, just a page that runs in any browser.

**Repository:** `presentations` &nbsp;·&nbsp; **Live site:** https://taggertmayfield.github.io/presentations/

---

## Presentations

| # | Presentation | Topic | Built with | Link |
|------|--------------|-------|------------|------|
| TM-001 | Crumb Rubber Molding | Materials · Process | HTML5, SVG, video | [`/crumb-rubber-molding/`](./crumb-rubber-molding/) |

The home page (`index.html`) is the hub: it indexes every presentation in the top
menu and lays them out as a catalog, newest first.

---

## Repository structure

```
presentations/
├── index.html                  # Site hub — catalog + menu (start here)
├── README.md                   # This file
├── .nojekyll                   # Tell GitHub Pages to serve files as-is
└── crumb-rubber-molding/       # TM-001
    ├── index.html              # The presentation (images embedded as base64)
    ├── process-cycle.mp4       # Short clip: full mix → press → demold cycle
    └── plant-tour.mp4          # Plant tour: every production station
```

---

## Adding a new presentation

The hub is built to grow. To index a new build:

1. **Drop the project in a folder** at the repo root, e.g. `my-new-project/`, with its
   own `index.html` and any assets. Keep each project self-contained in its folder.
2. **Add a menu entry** in `index.html` inside `<nav class="menu">`:
   ```html
   <a href="#my-new-project"><span class="ix">02</span>My New Project</a>
   ```
3. **Add a catalog card** in the `.grid` block. Copy the existing `<article class="card">`,
   then update the `id`, index code (`TM-002`), title, description, tags, and both the
   `href` links (the `.card-media` link and the `.stretch` link at the bottom). Use a
   16:9 image for `.card-media img`, or an inline `<svg>` motif if you don't have a shot.
4. **Bump the counts** — the hero `statline` and the `.count` label in the section header.
5. **Restore the two-column grid.** With one presentation the grid CSS is
   `grid-template-columns:minmax(0,560px)`; for two or more cards change it back to
   `grid-template-columns:repeat(2,1fr)`.

Newest entries go at the top of the grid; the `TM-00x` index code preserves build order.

---

## Conventions

- **Self-contained pages.** Images are embedded as base64 data URIs so a presentation
  renders even if moved. Large media (video) is kept as sibling files in the project
  folder — keep those files next to the `index.html` that references them.
- **No build step, no dependencies.** Plain HTML, CSS, and vanilla JS. Web fonts load
  from Google Fonts; everything else is local.
- **Accessible by default.** Responsive down to mobile, visible keyboard focus, and
  `prefers-reduced-motion` respected on every animation.
- **House style.** Display type *Space Grotesk*, body *Archivo*, data/labels in
  *Spline Sans Mono*. Individual presentations may use their own palette to suit the
  subject (the crumb-rubber page runs a warmer, industrial theme).

---

## Local preview

No server required — open `index.html` in a browser. To click through to the local
presentation and have the videos load, serve the folder so relative paths resolve:

```bash
# from the repo root
python3 -m http.server 8000
# then visit http://localhost:8000
```

---

## Deploy to GitHub Pages

This is a **project repository**, so GitHub Pages serves it from a subpath named after
the repo:

```
https://taggertmayfield.github.io/presentations/
```

All internal links are **relative** (e.g. `./crumb-rubber-molding/`), so they resolve
correctly under that subpath — no hard-coded root paths to break. To publish:

```bash
git init
git add .
git commit -m "Initial commit: presentations hub + crumb rubber molding"
git branch -M main
git remote add origin https://github.com/taggertmayfield/presentations.git
git push -u origin main
```

Then in the repo's **Settings → Pages**, set the source to the `main` branch (root).

---

*Built by hand. No trackers, no frameworks.*
