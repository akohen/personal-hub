# Build plan (next session)

Read `CLAUDE.md` first; it holds the constraints and design. Delete this file once done.

## Content needed from Alexandre (fill in before or at start of session)

- [ ] Role / company line (e.g. "Software engineer at X · Paris, France")
- [ ] Optional 1-sentence bio
- [ ] LinkedIn URL (GitHub: https://github.com/akohen)
- [ ] Projects — URL + 1–2 sentence description each:
  - [ ] AeroTrips — https://aerotrips.fr — …
  - [ ] Songline — … — …
  - [ ] Citation Needed — … — …
  - [ ] Advent of Code contributions — … — …
  - [ ] (optional 5th) — … — …

## Steps

1. **Scaffold**: `index.html`, `style.css`, `CNAME` (`alexandre.kohen.fr`), empty `.nojekyll`,
   `assets/`.
2. **Avatar**: download `https://github.com/akohen.png?size=256` to `assets/avatar.jpg`
   (check the actual format; rename to `.png` if needed and update references).
3. **Favicon**: simple `favicon.svg` (e.g. "AK" monogram in `--accent`), or reuse the avatar.
4. **HTML**: head (meta, OG, canonical, favicon), header, projects list, footer, with the
   content above.
5. **CSS**: tokens + dark-mode override, typography, layout, link/focus styles, per CLAUDE.md.
6. **Check**:
   - local preview via `python3 -m http.server`, light and dark mode
   - 320px / mobile width, no horizontal scroll
   - W3C HTML validator, keyboard navigation and focus visibility, contrast of `--muted`
7. **Commit & push** to `main` (ask first).
8. **Go live** (Alexandre, outside the repo):
   - DNS: `CNAME alexandre → akohen.github.io` at the kohen.fr registrar
   - repo Settings → Pages: deploy from `main` / root, custom domain `alexandre.kohen.fr`,
     enable "Enforce HTTPS" once the certificate is issued
   - verify https://alexandre.kohen.fr loads with the avatar and correct OG preview
