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
├── projects.qmd         # Projects showcase page
├── styles.css           # Custom CSS styling
├── CNAME                # Custom domain configuration (for GitHub Pages)
├── cv.txt               # CV file
├── world_cloud.ipynb    # Jupyter notebook (unused currently)
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
   - **projects.qmd** — Projects showcase (apps, research, etc.)

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

- Commented-out sections in _quarto.yml (Publications, CV) are ready to uncomment when needed
- The `world_cloud.ipynb` notebook isn't currently linked—consider adding it to Projects if you want to showcase it
- Clean up commented content in `index.qmd` for a cleaner codebase

---

**Resources:**
- Quarto Documentation: https://quarto.org
- GitHub Pages: https://pages.github.com
- Quarto Website Guide: https://quarto.org/docs/websites/
