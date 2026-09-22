# Portfolio

Personal portfolio site for Abdulrahman (Abood) Abusaleh — electrical & computer engineering
student at Northeastern University. Built as a static site with plain HTML, CSS, and JavaScript
(no frameworks, no build step) and deployed to GitHub Pages.

**Live site:** https://aboodyabusaleh.github.io/portfolio/

## Structure

```
.
├── index.html                  # Entire single-page site: markup, inline <style>, inline <script>
├── resume.html                 # Standalone resume viewer (embeds the PDF)
├── .github/workflows/static.yml# GitHub Pages deploy on push to main
└── assets/
    ├── css/style.css           # Legacy stylesheet — not referenced by any page
    ├── docs/resume.pdf         # Resume, embedded by resume.html and the in-page modal
    ├── media/                  # Audio and video (background track, project demo)
    └── img/
        ├── about/              # Hero / profile photos
        ├── cats/               # "Cat vault" easter-egg gallery
        ├── certifications/     # Altium certificate scans
        ├── experience/         # Company and lab photos for the work-history cards
        ├── hobbies/            # Hobby gallery (gym, games, shows, hiking, misc)
        ├── projects/           # One folder per project: ecg, mira, river, spider
        └── ui/                 # Decorative cat GIFs, including light/dark theme variants
```

Both pages are self-contained: CSS lives in an inline `<style>` block and JS in an inline
`<script>` block at the bottom of each file. There is no bundler, package manager, or
dependency install — the only external resource is the Font Awesome CDN.

## Running locally

Any static file server works. From the repo root:

```bash
python -m http.server 8000   # then open http://localhost:8000
```

Opening `index.html` directly via `file://` mostly works, but the embedded PDF and the
video element behave better over HTTP.

## Deploying

Pushing to `main` triggers `.github/workflows/static.yml`, which uploads the whole repo
as a Pages artifact and deploys it. No build step runs, so whatever is committed is what
ships.

## Conventions

- Asset paths are always repo-relative (`assets/img/...`) — never absolute, so the site
  works from the `/portfolio/` subpath on GitHub Pages.
- File names are lowercase kebab-case. Avoid spaces; they force URL encoding.
- New project images go in `assets/img/projects/<project>/`.
