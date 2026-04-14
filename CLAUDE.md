# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Static single-file landing page for **WattClever** – a German AI automation agency by Kirill Schäfer targeting local businesses (Handwerk, Arztpraxen, KMU).

**Output file:** `index.html` (all CSS and JS are inline, no build step)

## Viewing the site

```bash
open index.html
```

No build, no server, no dependencies required. Open directly in a browser.

## Assets

| File | Location |
|---|---|
| Logo (SVG) | Embedded inline in `index.html` |
| Portrait photo | `/Users/kirillschafer/Desktop/Logo und Foto/IMG_4826.PNG` |

> For deployment: copy the photo into the project directory and update the `<img>` `src` attributes (currently absolute paths) to a relative path like `./assets/foto.png`.

## Brand

- **Primary:** `#0F385C` (deep navy)
- **Accent:** `#5EA4C2` (sky blue)
- **Fonts:** DM Serif Display (headlines) + DM Sans (body) via Google Fonts
- **Language:** German throughout

## Architecture of `index.html`

All sections in document order:

1. `<nav #navbar>` – sticky, gains shadow + backdrop-blur on scroll via `.scrolled`
2. `<section .hero>` – 2-col grid (text left, photo right), dot-pattern background via `.hero-bg-dots`
3. `<section #leistungen>` – 6 service cards, 3-col grid
4. `<section #anwendungen>` – 3 use-case cards with numbered headings
5. `<section #ueber-mich>` – 2-col (photo left, bio right)
6. `<section #prozess>` – 4-step horizontal process with connecting line (`.process-steps::before`)
7. `<section .contact-section #kontakt>` – navy background, 3 contact cards (tel/WhatsApp/Calendly)
8. `<footer>` – logo, legal links, copyright

**JS behaviour (inline `<script>`):**
- Navbar scroll shadow: `IntersectionObserver`-free, uses `window.scroll` + `.scrolled` class
- Mobile hamburger: toggles `.open` on `#mobile-menu` and `#hamburger`, locks `body` scroll
- Fade-in animations: `IntersectionObserver` on `.fade-up` elements → adds `.visible`
- Smooth scroll: intercepts `a[href^="#"]` clicks

**Contact details:**
- Phone / WhatsApp: `+49 170 823 4778` → `wa.me/491708234778`
- Calendly: `https://calendly.com/wattclever` (placeholder – update when live)
- Impressum / Datenschutz links are currently `href="#"` placeholders

## Installed skills (`.agents/skills/`)

The `ui-ux-pro-max-skill/` directory and `.agents/` folder contain AI design skills (frontend-design, brand, slides, etc.) installed via `npx skills`. They are not part of the website – ignore them when editing the site.
