# Santiago Schnell: personal website

Source for [santiago-schnell.github.io](https://santiago-schnell.github.io/), built with
[Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) and published with GitHub Pages.

## Updating the site (everyday use)

1. Edit the files in this folder (see *Where things live* and *Common edits* below).
2. Open **GitHub Desktop**. Your changes appear in the left panel.
3. Type a short summary in the box at the bottom left (for example *Add new publication*),
   click **Commit to main**, then **Push origin** in the top bar.
4. GitHub rebuilds and publishes the site automatically. The change is live at
   <https://santiago-schnell.github.io> within about two minutes. Press **Ctrl+F5** if your browser
   still shows the old page.

To replace a PDF (CV, short biography), copy the new file into `docs/assets/files/` under the
**same file name**, so the existing links keep working, then commit and push.

## First-time setup (Windows and GitHub Desktop)

You only need to do this once.

### 1. Check the folder

The folder should be named `santiago-schnell.github.io`, and these items should sit directly
inside it, not inside another folder:

```
.github\    docs\    overrides\    .gitignore    mkdocs.yml    README.md    requirements.txt
```

### 2. Create the repository

1. In GitHub Desktop, choose **File → Add local repository** and select the folder.
2. When it says the folder is not a Git repository, click **create a repository**.
3. Keep the name `santiago-schnell.github.io`, set **Git ignore** to *None* and **License** to *None*
   (the folder already has a `.gitignore`), and click **Create repository**.

### 3. Publish it to GitHub

1. Click **Publish repository** in the top bar.
2. Keep the name exactly `santiago-schnell.github.io`. It must match the GitHub username for the
   site to appear at that address.
3. **Untick** *Keep this code private*: GitHub Pages on a free account needs a public repository.
4. Click **Publish repository**.

### 4. Switch on GitHub Pages

1. In GitHub Desktop, choose **Repository → View on GitHub**.
2. On github.com, open **Settings → Pages**. Under *Build and deployment*, set **Source** to
   **GitHub Actions**.
3. GitHub then suggests workflows such as *Jekyll* or *Static HTML*. **Ignore them and leave the page.**
   This repository already has its own workflow (`.github/workflows/deploy.yml`, named
   *Deploy site*), and adding a second one would conflict with it.

### 5. Run the first deployment

1. Click the **Actions** tab in the row along the top of the repository page (next to *Code* and
   *Pull requests*). This is not the *Actions* entry in the Settings sidebar, which shows
   *General, Runners, Policies* and needs no changes.
2. Click **Deploy site** on the left.
3. If the first run has a red ✗ (it usually does, because Pages was not switched on yet), open it
   and click **Re-run all jobs**. If there is no run, click **Run workflow → Run workflow**.
4. Wait for the green tick (about a minute), then visit <https://santiago-schnell.github.io>.

## Previewing changes on your own computer (optional)

This lets you see a change before publishing it.

**One-time installation**

1. Install Python from <https://www.python.org/downloads/>. On the first installer screen, tick
   **Add python.exe to PATH**.
2. Open this folder in File Explorer, click in the address bar, type `cmd` and press Enter.
   A Command Prompt window opens in the folder.
3. Run:

   ```
   py -m pip install -r requirements.txt
   ```

**Each time you want a preview**

1. Open a Command Prompt in the folder as above and run:

   ```
   py -m mkdocs serve
   ```

2. Open <http://127.0.0.1:8000> in your browser. The page reloads each time you save a file.
3. Press **Ctrl+C** in the Command Prompt window to stop.

Addresses starting with `127.0.0.1` exist only on your own computer. Never paste them into a page
as a link.

To check for broken links before pushing, run `py -m mkdocs build --strict`. It is the same check
GitHub runs, so anything it reports would also stop the site from publishing.

## Troubleshooting

| What you see | What to do |
|---|---|
| A red ✗ next to *Deploy site* | Open the run and click the failed step to read the log. It usually names a file and a broken link or image path. Fix it, then commit and push again. |
| *Deploy site* is not listed under Actions | The `.github` folder is not at the top of the repository. Check the layout in step 1, then commit and push. |
| The address shows "404" | Check that the repository is public, is named exactly after the GitHub username, and that **Settings → Pages → Source** is *GitHub Actions*. |
| The site shows an old version | Wait until the Actions run has a green tick, then press **Ctrl+F5**. |
| `py` is not recognised in Command Prompt | Python is not on the PATH. Re-run the Python installer, choose *Modify*, and tick *Add Python to environment variables*. |

## Custom domain (optional)

To use your own domain instead of `santiago-schnell.github.io`:

1. Add the domain under **Settings → Pages → Custom domain** and follow GitHub's instructions for
   your domain registrar's DNS settings.
2. Add a file `docs/CNAME` containing only the domain name (for example `www.example.org`).
3. Change `site_url` in `mkdocs.yml` to the new address, then commit and push.

## Where things live

```
mkdocs.yml                      site settings, navigation, footer content (tagline, affiliations, links)
docs/
  index.md                      home page (hero, projects, team, covers, latest publications)
  about.md                      biography and contact
  research.md                   research program
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
