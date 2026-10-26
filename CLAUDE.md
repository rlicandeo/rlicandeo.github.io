# CLAUDE.md - rlicandeo.github.io

Personal website of Roberto Licandeo (Rho). Built with Quarto, published on GitHub Pages
from the `docs/` folder. Custom domain: imfemc.com (see `CNAME`).
Local path: `P:\pCloud Sync\GitHub\rlicandeo.github.io`. Repo: github.com/rlicandeo/rlicandeo.github.io

## Structure

- `_quarto.yml` - site config. Only the pages listed under `project: render:` are built
  (index.qmd, projects.qmd, about.qmd). Add new pages there, or they will not be rendered.
- `index.qmd` - home page. Contact info, About Me, "My Apps" buttons (`.app-link` class),
  word cloud image, photos in the right column.
- `projects.qmd` - Projects page with two sections, "Apps" and "Dashboards". Each item is a card.
- `about.qmd` - contact page (rendered but not in the navbar).
- `styles.css` - all custom styles. Card styles live here, not inline.
- `world_cloud.ipynb` - generates `world_cloud.png`. Not rendered as a page.
- `docs/` - rendered output. Never edit by hand, run `quarto render`.

## Adding an app or dashboard to Projects

Copy one card block in `projects.qmd` and change title, description, tags and link:

```
::::: {.project-card}
::: {.card-title}
Title
:::

::: {.card-desc}
Description.
:::

::: {.card-note}
Optional small italic note (e.g. hosting caveat).
:::

:::: {.card-footer}
::: {.card-tags}
[Python]{.tag} [Dash]{.tag}
:::

<a href="URL" target="_blank" class="btn-primary card-btn">Launch app →</a>
::::
:::::
```

Cards sit inside a `::: {.project-grid}` block. Also add a button in the "My Apps" section
of `index.qmd` if the item should appear on the home page.

## Current items

Apps
- BC Sockeye Stock Analysis - https://dash-sockeye.onrender.com/ (Python, Dash)
- Jack Mackerel HCR with SOPS - https://quant-analytics.shinyapps.io/sops_app/ (R, Shiny)
- Delay-Difference Stock Assessment Model - https://huggingface.co/spaces/RhoL/DD
  (Python, JAX, Gradio). Space sleeps when idle, card has a wake-up note.

Dashboards
- Indigenous Education and Employment in Canada - Tableau Public
  https://public.tableau.com/app/profile/roberto.licandeo/viz/FN_17549778644590/Dashboard1

## Conventions

- Source files use Windows line endings (CRLF). Keep them.
- `index.qmd` has an R chunk (`Sys.Date()`), so rendering needs R + knitr.
- Location shown on the site is Prince George, BC.

## Publish workflow (PowerShell)

```
cd "P:\pCloud Sync\GitHub\rlicandeo.github.io"
quarto render
git add -A
git commit -m "message"
git push
```

Check that `git push` ends with `main -> main` and that `git status` says
"up to date with 'origin/main'". "ahead of 'origin/main'" means the push did not happen.
GitHub Pages takes 1-2 minutes. Reload with Ctrl+F5.

See the Change log in README.md for history.
