# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Mission for Yeshua is a static website for a Christian ministry organization. The site has no build process, bundler, or package manager - it uses vanilla HTML, CSS, and JavaScript served directly.

## Development

**Local Development:** Open any HTML file directly in a browser, or use a local server:
```bash
npx serve .
# or
python -m http.server 8000
```

No build, lint, or test commands exist for this project.

## Architecture

### File Structure
- `index.html` - Homepage (root level)
- `pages/` - Subpages (about, books, community-center, contact, teachings)
- `script/css/` - Stylesheets
  - `styles.css` - Shared base styles and CSS variables
  - `*-style.css` - Page-specific styles (e.g., `books-style.css`)
- `script/js/script.js` - All JavaScript functionality
- `images/` - Static assets (logo, favicon, book covers, hero backgrounds)

### CSS Variables
The design system uses CSS custom properties defined in `styles.css`:

**Colors (Professional Church Palette):**
- `--primary: #1e5a8a` (deep blue - main brand color)
- `--primary-light: #2d7ab8`
- `--primary-dark: #0d3a5c`
- `--secondary: #b8860b` (gold - accent)
- `--secondary-light: #d4a524`
- `--accent: #c9a227` (gold variant)

**Gradients:**
- `--gradient-primary`: Deep blue gradient (main brand)
- `--gradient-secondary`: Gold gradient (accents, highlights)
- `--gradient-hero`: Deep blue overlay for hero sections

**Effects:**
- Glassmorphism: `rgba(255,255,255,0.8)` background + `backdrop-filter: blur(10px)`
- Shadows with blue glows: `rgba(30, 90, 138, 0.x)` values
- Rounded corners: `--radius-sm` (8px), `--radius-md` (12px), `--radius-lg` (20px)
- Hover animations with cubic-bezier easing for smooth card lifts

### JavaScript Features
`script.js` initializes on DOMContentLoaded with these modules:
- `initializeNavigation()` - Mobile menu toggle
- `initializeSearch()` - Generic search with debounce
- `initializeScrollEffects()` - IntersectionObserver animations
- `initializeFormValidation()` - Real-time form validation
- `initializeBookFeatures()` - Book filtering by category/search on books page
- `initializeBookCovers()` - Fallback handling for missing book images

### Path Conventions
- Root pages use `script/css/` and `images/` paths
- Pages in `pages/` use `../script/css/` and `../images/` relative paths
- Each page includes both `styles.css` (base) and its page-specific CSS file

### External Dependencies (CDN)
- Font Awesome 5.15.3 for icons
- Google Fonts (Inter family)
