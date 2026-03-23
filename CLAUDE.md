# Portfolio Site — Project Instructions

## About

- Personal portfolio for Lucas Sam (GitHub: Lucas-sam93), a data analyst
- GitHub Pages site at `lucas-sam93.github.io`
- Inspired by mason-wong.com — cinematic, minimal, editorial design language

## Architecture

- **Single-file architecture**: entire site lives in `index.html` (embedded CSS + JS)
- No build step, no framework — static HTML served via GitHub Pages
- Assets: project screenshots (`*-screenshot.png`), headshot, resume PDF

## Design System

### Typography
- **Koulen** (Google Fonts): display headings, nav logo. Always `font-weight: 400`, `text-transform: uppercase`, tight `line-height: 0.83–0.9`
- **Inter**: body text, paragraphs. Weights 300–800
- **Roboto Mono**: labels, tags, nav links, monospace UI elements. Weights 400–600

### Color Themes
- Dual theme (dark/light) via CSS custom properties on `[data-theme]`
- Auto-detected from `prefers-color-scheme`, no manual toggle
- Accent warm: `#ccbb87` (dark) / `#8a7a4a` (light) — gold tone for emphasis
- Navigation uses `mix-blend-mode: difference` with `#fff` text

### Spacing & Layout
- Desktop sections: `padding: 8rem 3rem`, `max-width: 1100px`
- Mobile sections: `padding: 5rem 1.5rem`
- Primary mobile breakpoint: `768px`
- Small phone breakpoint: `480px`

## Libraries & Dependencies

- **GSAP 3 + ScrollTrigger**: sticky pinning, parallax, scroll-driven animations
- **Lenis**: smooth scroll (with `prevent` for modal native scroll)
- No other dependencies — vanilla JS only

## Key Patterns

### CSS
- Class naming: `kebab-case` (e.g., `project-showcase-inner`, `footer-cta-heading`)
- Use CSS custom properties for all theme-dependent values
- Responsive: `clamp()` for fluid typography, `@media` for layout shifts
- Transitions: `cubic-bezier(0.23, 1, 0.32, 1)` for spring-like easing
- Touch devices: `@media (hover: none) and (pointer: coarse)` to remove hover-dependent styles

### JavaScript
- `camelCase` for variables and functions, `const` preferred over `let`
- `gsap.matchMedia()` to split desktop (pinning + parallax) vs mobile (simple fade-in)
- Project data stored in `data-*` attributes on HTML elements
- Case study content stored in a `projectDetails` JS object keyed by project title
- Custom cursor disabled on touch via `ontouchstart` check

### HTML
- Semantic structure: `<nav>`, `<section>`, `<aside>` (modal), `<footer>`
- `data-cursor-hover` attribute marks interactive elements for cursor expansion
- Project modals use `clip-path` curtain reveal + `history.pushState` for back button

## Required Skills

- **UI/UX Pro Max**: Always use this skill when applying visual, aesthetic, or UX improvements. Run the design system analysis and audit before implementing changes.
- **Nano Banana Pro**: Always use this skill for generating or editing images to improve visuals (e.g., hero images, project screenshots, OG images, backgrounds).

## Autonomy & Boundaries

- **NEVER execute changes without explicit user approval** — always suggest first
- Always suggest the best possible improvement based on industry standards
- When suggesting changes, explain the "why" not just the "what"
- If something could be done multiple ways, explain trade-offs
- Destructive actions (deleting files, force-pushing): always confirm first
- Never modify .env files, credentials, or secrets
- Never commit sensitive data

## Git Rules

- NEVER include `Co-Authored-By` trailers in commit messages
- NEVER add Claude or any AI assistant as a contributor or co-author
- Use conventional commit style: `feat:`, `fix:`, `docs:`, `style:`, `refactor:`
- Do not push to remote unless explicitly asked
