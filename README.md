# raidsmithz.github.io

Personal profile & portfolio website for **Nanda Fitri Tsalatsa** — Embedded & Industrial IoT Engineer. Built as a static site and deployed via **GitHub Pages**.

Live site: https://raidsmithz.github.io/

## Overview

- Single-page profile (About, Skills, Resume, Portfolio) served from `index.html`
- 20 project detail pages (`project-detail-1.html` … `project-detail-20.html`) with image galleries
- Static, no build step — plain HTML/CSS/JS (Bootstrap 5 + BootstrapMade "Personal" template base)

## Project Structure

```
.
├── index.html              # main profile page (About / Skills / Resume / Portfolio)
├── project-detail-*.html   # 20 individual project pages
├── assets/
│   ├── css/style.css       # all styling + shimmer/image effects
│   ├── js/main.js          # nav, sliders, lazy-load + shimmer init
│   ├── img/                # WebP images (portfolio, profile, background)
│   │   └── portfolio/<n>-<project>/{1..N}.webp
│   └── vendor/             # Bootstrap, Swiper, GLightbox, Isotope, etc.
├── robots.txt              # crawler rules + sitemap pointer
├── sitemap.xml             # 21 URLs (root + 20 projects)
├── .nojekyll               # disables Jekyll processing on GitHub Pages
└── README.md
```

## Features

- **WebP images** — all photos converted to WebP (quality 80, downscaled to 1600px for galleries / 800px for profile). Total `assets/img` ≈ 23 MB (was ~70 MB). Favicon & Apple-touch-icon kept as PNG.
- **Lazy loading + shimmer** — every `<img>` gets `loading="lazy"` and a CSS shimmer placeholder that fades in on load (handled globally in `main.js` + `style.css`; no per-image markup required). Respects `prefers-reduced-motion`.
- **SEO** — meta description/keywords, Open Graph + Twitter Card tags, `robots.txt`, and `sitemap.xml`.
- **UI polish** — smooth scrolling, visible keyboard focus states, portfolio/icon-box hover lift.

## Local Development

No build tooling required. Serve the folder with any static server:

```bash
# Python
python3 -m http.server 8000
# then open http://localhost:8000
```

Edit `index.html` / `project-detail-*.html` for content and `assets/css/style.css` for styling.

## Deploy

Changes are deployed automatically by GitHub Pages on push to the `main` branch. Verify the build status:

```bash
gh api repos/raidsmithz/raidsmithz.github.io/pages/builds/latest
```

## Notes

- Images are stored as WebP. When adding new photos, convert them (e.g. `ffmpeg -i in.jpg -vf "scale='min(1600,iw)':-2" -quality 80 out.webp`) and reference the `.webp` path.
- Keep `favicon.png` and `apple-touch-icon.png` as PNG (required icon formats).
