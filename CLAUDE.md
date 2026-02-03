# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Single-page Hebrew (RTL) landing page for a Non-Violent Communication (NVC) workshop taught by Sharon Carmel in Pardes Hanna. Everything lives in one self-contained `index.html` file with inline CSS and vanilla JavaScript — no build tools, frameworks, or package manager.

## Development

Open `index.html` directly in a browser or serve via any static HTTP server (e.g. `python3 -m http.server`). No build step required.

## Architecture

**`index.html`** — the entire site in one file:
- **CSS custom properties** (`:root` block) define the design system: color palette (beige/peach/cream/teal), fluid typography via `clamp()`, spacing scale, shadows, and transitions
- **9 content sections**: Hero → What is NVC → Quote → Course Content → Testimonials → About Instructor → Dates → CTA → Footer
- **JavaScript** (~60 lines): Two `IntersectionObserver` instances handle scroll-triggered `.fade-up` and staggered child animations. Respects `prefers-reduced-motion`.
- **Floating WhatsApp FAB**: fixed-position button with pulse animation, links to `wa.me/972XXXXXXXXX` (placeholder)

**Assets:**
- `שרון כרמל.png` — instructor photo, referenced directly from HTML
- `תוכן דף נחיתה.docx` — source content document (Hebrew), not used at runtime

## Key Conventions

- **Language**: All content is Hebrew. Document uses `lang="he" dir="rtl"`. English terms (NVC, Non-Violent Communication) are wrapped in `<span dir="ltr">`.
- **Font**: Rubik from Google Fonts (loaded via `<link>` with `display=swap`)
- **Responsive breakpoints**: mobile (<768px), tablet (768–1023px), desktop (≥1024px)
- **Accessibility**: skip link, `aria-labelledby` on sections, semantic HTML, visible `:focus-visible` outlines, reduced-motion support
- **Color palette**: soft beiges/peaches/creams for backgrounds, dark teal (#2C4A4C, #3D5A5C) for text — maintains AAA contrast ratio
