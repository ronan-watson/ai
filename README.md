# AI Notes

A small static site of personal notes on practical AI use, written for three specific friends. Source is plain markdown so this repo can grow into a longer-lived AI knowledge base.

## Layout

```
docs/                    All published content. One .md per page.
  _jargon-allowlist.md   Working contract (excluded from the build).
overrides/               Material theme overrides (noindex + footer).
.github/workflows/       GitHub Actions: build & deploy to Pages.
mkdocs.yml               Site config.
requirements.txt         Pinned: mkdocs + mkdocs-material.
```

## Local preview

```sh
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
mkdocs serve
```

Then open <http://127.0.0.1:8000>. Changes to files under `docs/` reload automatically.

To produce a one-shot build (fails on broken links / unknown extensions):

```sh
mkdocs build --strict
```

The output lands in `site/` (git-ignored).

## Deployment

Push to `main` and the GitHub Actions workflow at `.github/workflows/deploy.yml` builds the site and publishes it to GitHub Pages via the modern `actions/deploy-pages` flow (no `gh-pages` branch).

### One-time GitHub Pages setup

Pages **must be enabled with Actions as the source** before the first deploy works. Do this once after the repo is created:

1. Open the repo on GitHub.
2. Go to **Settings → Pages**.
3. Under **Build and deployment → Source**, select **GitHub Actions**.

That's it. Subsequent pushes to `main` will publish automatically.

## Authoring rules

- Vanilla CommonMark + GFM only. No admonitions, no `pymdownx.*`, no MDX, no shortcodes. Files must read well in plain markdown viewers.
- Any AI-domain term not on `docs/_jargon-allowlist.md` must be glossed in plain language on first use, or removed.
- Aggregate word count across the six published pages should sit between 4,500 and 7,500 words (≈18&ndash;30 min at 250 wpm).
