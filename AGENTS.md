# AGENTS.md

Guidance for Codex and other agentic coding tools working in this repository.

## Project Overview

Startia v2 is a standalone landing page for a modular AI tools ecosystem targeting non-technical entrepreneurs. The frontend lives in a single `index.html` file. There is no build tooling, framework, or `package.json`.

## Previewing

Open the page directly in a browser:

```bash
open index.html
```

If browser opening is unavailable, serve the current directory with any static file server and load `index.html`.

## Repository Shape

- `index.html` contains all HTML, CSS, and vanilla JavaScript.
- `CLAUDE.md` contains Claude Code guidance.
- `.agents/skills/` contains Codex-compatible local design skills.
- `.claude/` contains Claude-specific local settings.

## Current Landing Structure

- Hero with split content and a right-side visual based on the "El Rompecabezas" concept.
- Floating module pieces in the hero should keep a puzzle-piece silhouette with tabs and sockets, implemented in CSS rather than bitmap assets.
- The hero visual includes compact satellite pieces connected by animated dotted SVG lines: `Agente IA` above `Landing Page`, `Ideas` to the right of `Contenido`, and `Recordatorios` below `Turnos`.
- In the hero visual, `Agente IA`, `Landing Page`, `Turnos`, and `Recordatorios` should stay left-aligned on the same vertical axis.
- Main sections: `#problema`, `#solucion`, `#como-funciona`, `#modulos`, `#testimonios`, `#para-vos`, `#empezar`, free-trial CTA, `#formulario-startia`, and footer.
- The header and footer navigation should point to real section anchors. The header CTA should point to `#formulario-startia`.
- `#solucion` uses a before/after composition: noisy chips on the left, a dotted connector, and a clear first-piece panel on the right.
- `#como-funciona` uses puzzle-shaped step cards. The third step is animated with GSAP ScrollTrigger on desktop so it starts separated above the step row and docks into the second piece while scrolling.
- `#para-vos` has a GSAP ScrollTrigger parallax on the left text column on desktop.
- `#empezar` is the pricing section. It includes a module-price carousel that scrolls only inside the card viewport, not with the page scroll.
- The free-trial CTA appears after pricing and before the form. Its CTA should point to `#formulario-startia`.
- `#formulario-startia` is the lead form section and should remain the final commercial section before the footer.
- Primary CTAs should point to `#formulario-startia` when the user intent is to start or request guidance.
- The lead form is static: it validates required fields and email in vanilla JavaScript, then shows an inline success message. It does not submit to a backend yet.

## Design Skills

Use the installed `.agents/skills/` instructions when the task matches their scope:

| Skill | When to use |
| --- | --- |
| `design-taste-frontend` | General frontend work, typography, color, layout, and motion discipline. |
| `high-end-visual-design` | Premium visual polish and agency-level landing page refinement. |
| `redesign-existing-projects` | Auditing and upgrading the existing UI without breaking behavior. |
| `full-output-enforcement` | Tasks that require complete, unabridged generated output. |
| `minimalist-ui` | Clean editorial or Linear/Notion-inspired UI direction. |
| `industrial-brutalist-ui` | Mechanical, Swiss, blueprint-like experimental UI direction. |
| `stitch-design-taste` | Google Stitch-compatible semantic design rules. |

## Design Constraints

- Font: `Outfit` from Google Fonts. Do not switch to Inter, Roboto, or Arial.
- Accent: warm amber `#D97706`.
- Background: warm cream `#FDFBF7`.
- Text: off-black `#18160F`; avoid pure black.
- Avoid AI-purple or blue-purple gradient themes.
- Icons should be inline SVG with `stroke-width="1.5"`.
- Prefer `min-height: 100dvh` for full-height sections.
- Keep the hero split and asymmetric: text left, visual right.
- Use `IntersectionObserver` for scroll reveals.
- Avoid `window.addEventListener('scroll')` for reveal effects.
- Use GSAP ScrollTrigger for complex scroll-linked assembly effects; keep those effects disabled or static for reduced-motion users and small screens.
- Do not use ScrollTrigger for the pricing carousel; it should move only when the user scrolls inside the carousel viewport.
- Use `cubic-bezier(0.32, 0.72, 0, 1)` for transitions.
- Use `picsum.photos/seed/{descriptive-seed}/width/height` for placeholder images.

## Brand Context

Concept: "El Rompecabezas". Startia sells independent modules that fit together:

- Landing Page
  - Agente IA
- Content Generator
  - Ideas
- Appointments Agent
  - Recordatorios
- Dashboard

The copy should stay friendly, human, and approachable. Avoid technical language.

## Module Identity Colors

- Landing Page: amber `#D97706`
- Content Generator: green `#16a34a`
- Appointments Agent: blue `#3b82f6`
- Dashboard: purple `#9333ea`

## Editing Notes

- Keep edits scoped to `index.html` unless adding agent or documentation files.
- Do not add a framework or build step unless explicitly requested.
- Preserve the single-file deployment model.
- Avoid unrelated formatting churn in `index.html`; it is already large and has local modifications.
- When updating the form, preserve label-above-input structure, helper text, error text, and the inline success status.
- When updating the hero visual, preserve the puzzle-piece metaphor and avoid replacing it with generic cards.
