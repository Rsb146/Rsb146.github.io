## Quick context

- This repository is a single-page static personal site served from `index.html` (root). It uses local Bootstrap CSS/JS (`css/bootstrap.min.css`, `js/bootstrap.min.js`) and Bootstrap Icons (`icons/bootstrap-icons.css`). Custom styles live in `css/style.css` and site behavior in `js/main.js`.
- Assets (images, video) are in `images/` and referenced with relative paths from `index.html`.
- It is intended for GitHub Pages (repository root `index.html` will be published as the site).

## Big-picture architecture

- Static client-only website. No backend or build pipeline. Edits are HTML/CSS/JS only.
- Key files:
  - `index.html` — single-page layout and navigation; primary integration point for CSS/JS and assets.
  - `css/style.css` — project-specific overrides and layout tweaks.
  - `js/main.js` — small client scripts (behavior hooks, optional). Review before changing UI behaviour.
  - `icons/` — local Bootstrap Icons stylesheet and fonts.

## Developer workflows (how to preview & test)

- Preview locally with a simple static server to ensure video and module features work (browsers often block autoplay from file://). Example commands (PowerShell):

```powershell
# Python
python -m http.server 8000
# or (Node)
## Quick context

- This repository is a single-page static personal site served from `index.html` (root). It uses local Bootstrap CSS/JS (`css/bootstrap.min.css`, `js/bootstrap.min.js`) and Bootstrap Icons (`icons/bootstrap-icons.css`). Custom styles live in `css/style.css` and site behavior in `js/main.js`.
- Assets (images, video) are in `images/` and referenced with relative paths from `index.html`.
- It is intended for GitHub Pages (repository root `index.html` will be published as the site).

## Big-picture architecture

- Static client-only website. No backend or build pipeline. Edits are HTML/CSS/JS only.
- Key files:
  - `index.html` — single-page layout and navigation; primary integration point for CSS/JS and assets.
  - `css/style.css` — project-specific overrides and layout tweaks.
  - `js/main.js` — small client scripts (behavior hooks, optional). Review before changing UI behaviour.
  - `icons/` — local Bootstrap Icons stylesheet and fonts.

## Developer workflows (how to preview & test)

- Preview locally with a simple static server to ensure video and module features work (browsers often block autoplay from file://). Example commands (PowerShell):

```powershell
# Python
python -m http.server 8000
# or (Node)
npx http-server -p 8000
```

- Open `http://localhost:8000/` in a browser. For GitHub Pages behavior, ensure paths remain relative (they already are).

## Project-specific patterns & gotchas

- Spanish content and comments are used in many places — preserve text unless asked to translate.
- The project uses Bootstrap utility classes heavily. When modifying layout, prefer editing `css/style.css` rather than changing many Bootstrap classes in `index.html`.
- Several repeated typos exist in class names (e.g. `aling-items-center` instead of `align-items-center`). Fixing these globally is common; search for `aling-` to find occurrences.
- Video autoplay: `index.html` uses `<video src="./images/pipboy.mp4" autoplay loop>`; browsers will block autoplay unless the video is muted. When adding autoplay, also add `muted playsinline`.
 - Navigation collapse: the toggler button targets the element with id "navbar-toggler" — when changing IDs, ensure the corresponding `data-bs-target` matches to keep mobile menu working.

## Safe edit rules for AI agents

- Do not change the project's offline Bootstrap or icons references to external CDNs unless the user asks. The repo intentionally includes offline copies in `css/`, `js/`, and `icons/`.
- Keep all asset paths relative. Avoid absolute or environment-specific paths.
- Preserve the `<meta charset>`, `<meta name="viewport">` and author/description metadata unless user requests an update.
- When changing layout or styles, add small CSS rules to `css/style.css` rather than making many inline edits in `index.html`.

## Concrete examples

- Fixing autoplay video: replace `autoplay loop` with `autoplay loop muted playsinline` in `index.html` at the section containing `pipboy.mp4`.
- Correcting class typos: search `aling-items-center` and change to `align-items-center` in `index.html` and in any other files.
- To add a new section, follow the existing pattern: a `<section>` with a descriptive id (used by navbar links), a container div, and classes like `seccion-titulo` / `seccion-texto` for headings and paragraphs.

## Tests & verification

 - Manual verification is sufficient: run local server and open the site. Check responsive behavior (shrink window), navbar collapse, carousel controls for the element with id "recomendaciones", and video playback.

## When to ask the user for clarification

- If a requested change affects the tone/language (Spanish text) or the site publishing target (GitHub Pages vs other host).
- If a change requires adding npm tooling or a build step (none currently present) — propose adding a small toolchain and ask before adding.

If anything above is unclear or you'd like me to merge these changes into `index.html` (fix typos, make video muted, or similar), tell me which one to apply and I'll implement it now.
