# Santiago Schnell: personal website

Source for [santiago-schnell.github.io](https://santiago-schnell.github.io/), built with
[Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) and published with GitHub Pages.

## Preview locally

```bash
pip install -r requirements.txt
mkdocs serve          # open http://127.0.0.1:8000; the page reloads as you edit
```

## Publish

Every push to `main` builds the site and publishes it (`.github/workflows/deploy.yml`).

One-time setup on GitHub:

1. Create a repository named **`santiago-schnell.github.io`** and push this folder to its `main` branch.
   A repository with that exact name is served at the root address above. Any other name works too,
   but the site is then served at `https://santiago-schnell.github.io/<repository-name>/`, and
   `site_url` in `mkdocs.yml` should be changed to match.
2. In the repository, go to **Settings → Pages → Build and deployment** and set **Source** to **GitHub Actions**.
3. Optional custom domain: add it under **Settings → Pages**, put a file `docs/CNAME` containing the
   domain, and update `site_url` in `mkdocs.yml`.

## Where things live

```
mkdocs.yml                      site settings, navigation, footer content (tagline, affiliations, links)
docs/
  index.md                      home page (hero, projects, team, covers, latest publications)
  about.md                      biography and contact
  research.md                   research programme
  team/index.md, team/joining.md
  publications/index.md, publications/covers.md
  assets/files/                 CV, short biography, mathematical genealogy (PDF)
  assets/images/brand/          logo, favicon, touch icon
  assets/fonts/                 Newsreader and Inter (SIL Open Font License; see OFL.txt in each folder)
  stylesheets/extra.css         the theme
  stylesheets/fonts.css         font declarations
  javascripts/mathjax.js        equation rendering
overrides/
  main.html                     extra <head> tags
  partials/footer.html          footer layout (its content comes from mkdocs.yml)
.github/workflows/deploy.yml    build and publish
```

## Common edits

- **Change an appointment or a footer link.** Edit `extra.affiliations` or `extra.social` in `mkdocs.yml`.
  The footer updates on every page. Also update the opening lines of `docs/about.md`.
- **Add a publication.** Add it at the top of `docs/publications/index.md`, and add it to the
  "Latest Publications" list on `docs/index.md` if it should appear on the home page.
- **Add a team member.** Copy an existing block in `docs/team/index.md`, and add a card on `docs/index.md`.
- **Add a cover.** Put the image in `docs/assets/images/covers/` and copy a `cover-item` block in
  `docs/publications/covers.md`.

## Design

The identity is deliberately independent of any institution.

| Role                     | Colour  | Hex       |
|--------------------------|---------|-----------|
| Structure, headings      | Navy    | `#14213D` |
| Accent, active states    | Gold    | `#C9A227` |
| Links (light mode)       | Oxblood | `#8A3B2E` |
| Page background (light)  | Paper   | `#FBF8F2` |

Headings and the wordmark use **Newsreader**; text and interface use **Inter**. The logo is a
Michaelis–Menten saturation curve with its asymptote, drawn in gold.

All colours are defined once, as tokens at the top of `docs/stylesheets/extra.css`, with a light and a
dark value. To adjust the palette, edit those two blocks only.

### Page components

The stylesheet provides a few HTML patterns for use inside Markdown pages:

- `card-grid` > `card` > `card-img` + `card-body` (`card-label`, `card-title`, `p`): image cards.
- `card research-card`, `card news-card`: text-only cards.
- `cover-gallery-wrapper` > `cover-gallery` > `cover-item` (with `journal-name`): cover grid.
- `project-section` with `figure.project-figure.float-right` / `.float-left`: research sections with a figure.
- `!!! project-summary`: a one-sentence statement at the head of a research section.
- `hero`: the home-page introduction (see `docs/index.md`).

## Licence

Site code and theme: MIT. Fonts: SIL Open Font License 1.1. Text, photographs, and journal covers
remain the property of their respective owners.
