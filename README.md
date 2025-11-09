# ŊOB Universe Hub (Static Site)

A GitHub‑ready hub that collects all available **NOB Universe** HTML modules from our conversation context
and wires **40 projects** as launchpads. It’s 100% static (HTML/CSS/JS) so you can host it on GitHub Pages.

## Folders
- `index.html` — main hub UI (sidebar + search + iframe preview)
- `modules/` — all context HTML modules copied in (open directly in the preview)
- `projects/` — 40 project folders, each with an `index.html` placeholder wired to the hub
- `projects.json` — list of projects (title, slug, path)
- `modules.json` — list of modules (title, file path)
- `styles/` — minimal CSS

## Local Dev
Just open `index.html` in a browser. For strict browsers, use a local server:
```bash
python3 -m http.server 8080
# then visit http://localhost:8080/
```

## Publish to GitHub Pages
1. Create a repo, e.g., `NOB-Universe-Hub`.
2. Commit all files and push to `main`.
3. Enable GitHub Pages (Settings → Pages → Deploy from branch: `main` / root).
4. Your hub will be live at `https://<you>.github.io/NOB-Universe-Hub/`.

## Wiring New Modules
- Drop any new `.html` into `modules/` and append an entry to `modules.json`:
```json
{{ "title": "My Module", "file": "modules/my_module.html" }}
```

## Wiring Projects
- Edit `projects.json`. Each project points to `projects/<slug>/index.html`. You can embed modules by query:
`projects/urft-simulator/index.html?modules=modules/kaleidoscope_optics.html,modules/tps_ripple_animation.html`

---

> Note: One file in context (`apex-crm-demo.tsx`) is TypeScript/React and not directly embeddable as HTML.
You can build it separately (Vite/Next) and link the deployed URL from `projects.json`.
