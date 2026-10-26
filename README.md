# Roberto Licandeo's Professional Website

A personal portfolio website built with **Quarto** and deployed to **GitHub Pages**.

## Setup Overview

This website is built using Quarto, a modern open-source scientific publishing system that renders Markdown files (.qmd) to HTML.

## Key Files & Folder Structure

```
rlicandeo.github.io/
├── _quarto.yml          # Quarto configuration file (site settings, navbar, theme)
├── index.qmd            # Home page
├── about.qmd            # About/contact page
├── projects.qmd         # Projects page (Apps and Dashboards cards)
├── styles.css           # Custom CSS styling
├── CNAME                # Custom domain configuration (for GitHub Pages)
├── cv.txt               # CV file
├── world_cloud.ipynb    # Notebook that generates world_cloud.png (not rendered as a page)
├── images/              # Images folder (logo, photos)
└── docs/                # OUTPUT FOLDER (compiled HTML site)
    ├── index.html
    ├── about.html
    ├── projects.html
    ├── styles.css
    ├── search.json
    └── site_libs/       # Bootstrap and Quarto libraries
```

## Steps to Replicate This Website

### 1. **Install Quarto**
   - Download and install from: https://quarto.org/docs/get-started/
   - Verify installation: `quarto --version`

### 2. **Create Project Structure**
   ```powershell
   mkdir rlicandeo.github.io
   cd rlicandeo.github.io
   mkdir images
   ```

### 3. **Create Configuration File: `_quarto.yml`**
   ```yaml
   project:
     type: website
     output-dir: docs
     resources:
       - CNAME
   
   website:
     title: "Roberto Licandeo, PhD"
     favicon: "images/logo_mini.png"
     google-analytics: "G-X8FBYR6RWS"
     navbar:
       left:
         - href: index.qmd
           text: Home
         - href: projects.qmd
           text: Projects
       right:
         - icon: github
           href: https://github.com/rlicandeo
         - icon: mortarboard-fill
           href: https://scholar.google.com/citations?user=66RSKVsAAAAJ
         - icon: fingerprint
           href: https://orcid.org/0000-0003-4593-183X
         - icon: envelope
           href: mailto:robertolicandeo@gmail.com
   
   format:
     html:
       theme: cosmo
       css: styles.css
       toc: true
       page-layout: full
   ```

### 4. **Create Content Pages**
   - **index.qmd** — Home page with introduction and contact grid
   - **about.qmd** — About section with contact information and photos
   - **projects.qmd** — Projects showcase (Sockeye, SOPS and Delay-Difference apps)

### 5. **Add Custom Styling: `styles.css`**
   - Create custom CSS for your design preferences
   - Link it in each .qmd file under `format: html: css: styles.css`

### 6. **Add Images**
   - Place your logo, photos, and assets in the `images/` folder
   - Reference them in .qmd files as: `![](images/filename.png)`

### 7. **Build the Site**
   ```powershell
   quarto render
   ```
   This generates the `docs/` folder with compiled HTML files.

### 8. **GitHub Pages Setup**
   - Create a GitHub repository: `yourusername.github.io`
   - In repository settings:
     - Go to **Settings → Pages**
     - Set source to: `Deploy from a branch`
     - Select branch: `main` (or `master`)
     - Select folder: `/docs`
   
### 9. **Custom Domain (Optional)**
   - Create a `CNAME` file with your domain: `yourdomain.com`
   - Add to DNS provider's A records pointing to GitHub Pages IP
   - Reference in `_quarto.yml` under `resources: - CNAME`

### 10. **Push to GitHub**
   ```powershell
   git init
   git add .
   git commit -m "Initial commit"
   git remote add origin https://github.com/yourusername/yourusername.github.io
   git branch -M main
   git push -u origin main
   ```

## Workflow for Updates

1. **Edit .qmd files** locally
2. **Run `quarto render`** to compile to HTML in `docs/`
3. **Commit and push** to GitHub
4. GitHub Pages automatically deploys from the `docs/` folder

## Useful Commands

| Command | Purpose |
|---------|---------|
| `quarto render` | Build entire site to docs/ |
| `quarto preview` | Preview site locally in browser |
| `quarto watch` | Watch for changes and auto-render |
| `quarto clean` | Remove docs/ and rebuild |

## Customization

- **Change theme**: Update `theme:` in _quarto.yml (e.g., `cosmo`, `lux`, `slate`, etc.)
- **Modify navbar**: Edit `navbar:` section in _quarto.yml
- **Custom CSS**: Add styles to `styles.css`
- **Analytics**: Update `google-analytics:` ID in _quarto.yml

## Notes

- Only the pages listed under `project: render:` in _quarto.yml are built (index, projects, about)
- Project cards on the Projects page use the `.project-card`, `.card-*` and `.tag` classes in `styles.css`. To add an app, copy one card block in `projects.qmd` and change the title, text, tags and link
- `world_cloud.ipynb` generates `world_cloud.png` for the home page. It is not rendered as a page

---

**Resources:**
- Quarto Documentation: https://quarto.org
- GitHub Pages: https://pages.github.com
- Quarto Website Guide: https://quarto.org/docs/websites/

## Change log

### 2026-10-26
- Added "Dashboards" section to Projects with the Tableau dashboard
  "Indigenous Education and Employment in Canada".
- Added this change log. Added a local CLAUDE.md (git-ignored, not published).

### 2026-10-25
- Added the Delay-Difference Stock Assessment Model app (Hugging Face, Python/JAX/Gradio)
  to Projects and to "My Apps" on the home page, with a note that the Space may take
  about a minute to wake up.
- Merged `projects_new.qmd` into `projects.qmd` (kept the fuller SOPS title and description,
  unified tag colours) and deleted `projects_new.qmd`.
- Moved card styles from inline HTML to CSS classes in `styles.css`
  (`.project-grid`, `.project-card`, `.card-title`, `.card-desc`, `.card-note`,
  `.card-footer`, `.card-tags`, `.tag`, `.card-btn`, `.app-link`).
- Fixed card hover shine effect (it crossed the whole page) and removed duplicate CSS rules.
- Moved "My Apps" into the main column of the home page, with buttons for all apps.
- Removed the old commented-out block at the top of `index.qmd`.
- Updated location from Chilliwack to Prince George, BC (index and about).
- `_quarto.yml` now renders only index, projects and about. Removed commented navbar items.
- Deleted unused files: `docs/projects_new.html`, `docs/world_cloud.html`,
  `docs/world_cloud_files/`, `images/Rho_fly.jpeg`,
  `mohamed_hassan-silhouette-3113255_1280.png`, `.Rhistory`.
- Added `.Rhistory` to `.gitignore`.
