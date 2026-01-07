<!-- Purpose: guidance to AI coding agents working on this Jekyll site -->
# Copilot instructions — repository-specific guidance

This repository is a Jekyll-based personal website derived from the al-folio theme. The goal of this file is to provide concise, actionable guidance for AI coding agents to be immediately productive.

1) Big picture
- This repo is a static Jekyll site. Source lives in the repository root and typical Jekyll folders: `_layouts/`, `_includes/`, `_posts/`, `_pages/`, `_data/`, `_bibliography/`, `_plugins/`, and `assets/`.
- Build output is `_site/` (do not edit directly).
- Content is rendered with a set of Ruby gems (see `Gemfile`) and some repository-specific Ruby plugins under `_plugins/`.

2) Local development & build (concrete commands)
- Preferred (Docker): `docker-compose -f docker-local.yml up --build` or the provided VS Code task `Run local site (Docker)` which runs `docker-compose up`.
  - Note: `docker-local.yml` maps port `8080`, while vanilla `jekyll serve` defaults to `4000`.
- Standard Ruby (when not using Docker):
  - `bundle install`
  - `bundle exec jekyll serve --config _config.yml --lsi` (or `bundle exec jekyll build --lsi` to generate `_site/`).

3) Key project patterns and conventions
- Collections: `_news`, `_activity`, `_projects`, `_research`, `_erc` — permalinks and behavior are configured in `_config.yml`.
- Posts: use Jekyll conventions under `_posts/` (filenames `YYYY-MM-DD-title.md`).
- Pages: see `_pages/` and a few files with a leading `~` (for example `_pages/~activity.md` and root `~activity.html`) — treat these as special/draft-like sources; verify before removal.
- Templates: prefer changing small UI/template behavior in `_includes/` first, then `_layouts/` (e.g. `header.html`, `footer.html`, `post.html`).

4) Plugins, bibliography, and external integrations
- Plugins are declared in `Gemfile` and `_config.yml` (`plugins:`). Examples: `jekyll-scholar` for bibliography, `jekyll-imagemagick` for responsive images, `jekyll-jupyter-notebook` for notebooks.
- Bibliography: source lives in `_bibliography/papers.bib` and the `bib` layout is in `_layouts/` (see `_config.yml` scholar config). When editing BibTeX, run a full build to regenerate pages that depend on `jekyll-scholar`.
- Custom Ruby plugins in `_plugins/` (e.g. caching or bib helpers) are not supported by GitHub Pages by default — use Docker/local builds to test plugin changes.

5) Deployment & CI
- The repo follows al-folio defaults: automatic deployment via GitHub Actions (see `.github/workflows/deploy.yml` if present in your fork). The standard flow: edit source -> push -> Actions build -> `gh-pages` branch created/updated.
- For manual builds and non-GitHub hosting: `bundle exec jekyll build --lsi` and copy `_site/` contents.

6) Editing advice & safe-first changes
- When changing layout or CSS, edit `_includes/` or `_sass/` and test locally (docker or `bundle exec jekyll serve`) before committing.
- When changing Ruby gems, update `Gemfile` and run `bundle install` inside the same environment you use for serving (Docker build if you rely on Docker image).
- Image processing requires ImageMagick (see `_config.yml` `imagemagick:`); ensure Docker image or local environment has ImageMagick installed.

7) Useful example files to inspect before making related changes
- Global config: `_config.yml` (site behavior, plugins, collections, scholar settings)
- Theme / layout examples: `_layouts/post.html`, `_includes/header.html`, `_includes/footer.html`
- Bibliography source: `_bibliography/papers.bib` and `_layouts/bib.html`
- Custom plugins: `_plugins/` (e.g. `cache-bust.rb`, `hideCustomBibtex.rb`)

8) Limitations & gotchas
- GitHub Pages will not run arbitrary `_plugins/` — if you rely on them, test with the Docker workflow used here.
- Some files with a `~` prefix exist; they appear to be alternate/draft sources. Avoid deleting unless you confirm their role in navigation.

If anything above is unclear or you want more detail (for example, contents of `Dockerfile` or how `jekyll-imagemagick` is used in templates), tell me which area to expand and I will update this file.
