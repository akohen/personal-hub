# personal-hub

Personal landing page for Alexandre Kohen, served by GitHub Pages at
**https://alexandre.kohen.fr** (custom domain, root path `/`).
One page listing projects, socials and a short bio.

## Hard constraints

- Pure static HTML + CSS. **No build step, no framework, no package.json, no JavaScript.**
- No external requests at runtime: no web fonts, no CDNs, no icon libraries, no analytics,
  no hotlinked images. Everything the page needs lives in this repo.
- Single language: **English** (`<html lang="en">`).
- Keep it small: the whole site should stay a handful of files and well under 200 KB.

## File layout

```
index.html        the page (all content lives here)
style.css         all styles
assets/avatar.jpg profile picture (copy of the GitHub avatar, ~256px)
favicon.svg       favicon (+ assets/apple-touch-icon.png if added)
CNAME             contains exactly: alexandre.kohen.fr
.nojekyll         empty; disables Jekyll processing on Pages
```

Use root-relative-free, plain relative paths (`style.css`, `assets/avatar.jpg`) so the page
also works when opened locally.

## Design

Text-first, "well-written README" feel. Left-aligned, single narrow column, lots of whitespace.

Layout, top to bottom:
1. Header: small round avatar (≈64px) inline next to the name (`h1`), then one line with
   role/company · Paris, France, then social links as plain text: `github · linkedin`.
2. `## projects` section: a list; each item is the project name as a link, followed by an
   em dash and a 1–2 sentence description.
3. Footer: a thin rule and `alexandre.kohen.fr`.

Design tokens (define as CSS custom properties on `:root`, never hard-code colors elsewhere):

| token        | light     | dark      |
|--------------|-----------|-----------|
| `--bg`       | `#fdfdfc` | `#16171a` |
| `--fg`       | `#1d1f23` | `#e6e6e3` |
| `--muted`    | `#62666d` | `#9a9ea6` |
| `--accent`   | `#2456c7` | `#7aa2ff` |
| `--rule`     | `#e3e3df` | `#2c2e33` |

- Theme: light by default; dark via `@media (prefers-color-scheme: dark)` overriding the
  tokens. Set `color-scheme: light dark` on `:root`. No manual toggle.
- Font: system sans stack
  `system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif`.
  Monospace stack (`ui-monospace, SFMono-Regular, Menlo, Consolas, monospace`) is allowed
  only for small README-style accents such as section headings (`## projects`).
- Measure: `max-width: 40rem`, side padding `1.25rem`, base font size `1.0625rem`,
  line-height `1.6`.
- Links: `--accent` color, underline on hover/focus; visible `:focus-visible` outline.
  External links get `rel="noopener"`; no `target="_blank"`.
- No shadows, gradients, cards or animations. Fine at 320px width with no horizontal scroll.

## HTML conventions

- Semantic markup: `<header>`, `<main>`, `<section>`, `<ul>`, `<footer>`.
- `<head>` must include: charset, viewport, `<title>Alexandre Kohen</title>`,
  meta description, canonical `https://alexandre.kohen.fr/`, favicon, and Open Graph tags
  (`og:title`, `og:description`, `og:url`, `og:image` → absolute URL of the avatar).
- Avatar `<img>` has `alt="Alexandre Kohen"`, explicit `width`/`height`.
- Indent with 2 spaces. Keep HTML valid (W3C validator clean).

## Adding or editing content

- New project: add one `<li>` in the projects list in `index.html`, following the existing
  pattern (link name — description). Keep descriptions to 1–2 sentences.
- New social: append to the social line, separated by ` · `.
- Don't add new pages or sections without asking.

## Local preview & deploy

- Preview: `python3 -m http.server 8000` then open http://localhost:8000.
- Deploy: GitHub Pages → "Deploy from a branch", branch `main`, folder `/ (root)`.
  Pushing to `main` publishes. No GitHub Actions.
- DNS (at the kohen.fr registrar): `CNAME alexandre → akohen.github.io`.
  Then set the custom domain in repo Settings → Pages and enable "Enforce HTTPS".
