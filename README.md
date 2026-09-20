# Wooseok Daniel Shin — Research Website

- URL: https://wsshinskku.github.io
- Stack: GitHub Pages + Minimal Mistakes (remote_theme)
- Content: Research frameworks, publications, projects, teaching(Algorithms, Science Fair(Research and Education))

## Editing the site
This site is built and deployed by `.github/workflows/pages.yml` when `main` is updated.

- Root Markdown files (`index.md`, `research.md`, `publications.md`, etc.) define the main pages.
- `_data/publications.yml` is the source for publication titles, venues, years, and review status.
- `_data/research.yml` groups the five research frameworks and stores summaries, topics, detail URLs, and repository access. Each `publication_title` must exactly match a title in `publications.yml` so metadata stays synchronized.
- `_research/*.md` contains the English descriptions, Korean summaries, method overviews, and artifact links. Preserve the explicit permalinks when renaming files.
- `_includes/research-*.html` renders shared cards, links, metadata, and manuscript records.
- `assets/css/research.css` is loaded only for Research pages through `_includes/head/custom.html`.

The Research catalog includes FedVar, FedGCD, FedHyDRA, TFL-CORAN, and Pandora. All five repositories are public. Keep each project's `access` value synchronized with its actual GitHub visibility. A manuscript's target venue and review status do not imply acceptance.

The public code in FedVar and FedGCD is presented as research prototypes. TFL-CORAN and Pandora describe their runnable reference environments and distinguish them from the original external simulator setups.

## Licensing

- **Code** (HTML/CSS/JS, configuration, build scripts)  
  Licensed under the [MIT License](./LICENSE).

- **Content** (texts, images, diagrams, markdown posts)  
  Licensed under the [Creative Commons Attribution 4.0 International License](./LICENSE-CONTENT).

You are free to share, modify, and reuse the code and content with proper attribution.
