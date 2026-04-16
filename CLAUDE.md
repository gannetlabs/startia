# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

Startia v2 is a standalone landing page for a modular AI tools ecosystem targeting non-technical entrepreneurs. The entire frontend lives in a single `index.html` file — no build tooling, no framework, no package.json. It uses plain CSS and vanilla JavaScript inside `index.html`.

## Previewing the page

```bash
open index.html
```

## Installed design skills

Seven design skills from `Leonxlnx/taste-skill` are installed in `.claude/skills/`. Use them via slash commands when generating or redesigning UI:

| Skill | Command | When to use |
|-------|---------|-------------|
| `design-taste-frontend` | `/taste` | General frontend work — enforces typography, color, and layout rules |
| `high-end-visual-design` | `/soft` | Agency-level polish: Double-Bezel cards, spring animations, cinematic motion |
| `redesign-existing-projects` | `/redesign` | Auditing and fixing existing UI problems |
| `full-output-enforcement` | `/output` | Ensures no incomplete code or placeholder comments |
| `minimalist-ui` | `/minimalist` | Editorial style (Notion/Linear-inspired) |
| `industrial-brutalist-ui` | `/brutalist` | Experimental mechanical aesthetic |
| `stitch-design-taste` | `/stitch` | Google Stitch-compatible semantic design rules |

To add new skills: `npx skills add <github-url> --yes`

## Design constraints enforced by the active skills

These rules apply whenever generating or modifying UI in this project:

- **Font:** `Outfit` (via Google Fonts). `Inter`, `Roboto`, `Arial` are banned.
- **Accent color:** Warm amber `#D97706`. AI purple/blue gradients are banned.
- **Background:** Warm cream `#FDFBF7`. Off-black text `#18160F` (never pure `#000000`).
- **Icons:** Inline SVG with `stroke-width="1.5"`. No Lucide, FontAwesome, or emoji.
- **Full-height sections:** Always `min-h-[100dvh]`, never `h-screen` (iOS Safari bug).
- **Hero layout:** Split asymmetric (text left, visual right). Centered hero is banned.
- **Hero puzzle visual:** Preserve the CSS puzzle-piece silhouettes and animated dotted SVG connector lines. The compact satellite pieces are `Agente IA` above `Landing Page`, `Ideas` to the right of `Contenido`, and `Recordatorios` below `Turnos`.
- **Hero alignment:** Keep `Agente IA`, `Landing Page`, `Turnos`, and `Recordatorios` left-aligned on the same vertical axis.
- **Cards:** Use elevation only when hierarchy requires it. Avoid 3-column equal card grids.
- **Animations:** `cubic-bezier(0.32, 0.72, 0, 1)` for all transitions. Never `linear` or `ease-in-out`.
- **Scroll reveals:** Use `IntersectionObserver`. Never `window.addEventListener('scroll')`.
- **Scroll-linked effects:** Use GSAP ScrollTrigger only for complex desktop effects, and keep them disabled/static for reduced-motion users and small screens.
- **Pricing carousel:** Do not tie pricing cards to page scroll. The module-price cards should move only when the user scrolls inside the carousel viewport.
- **Images:** `picsum.photos/seed/{descriptive-seed}/width/height` for placeholders. No Unsplash.

## Brand context

**Concept:** "El Rompecabezas" — four independent modules (Landing Page, Content Generator, Appointments Agent, Dashboard) that snap together. Clients buy only what they need; new pieces auto-integrate with existing ones. The hero can also show smaller connected pieces such as Agente IA, Ideas, and Recordatorios to suggest optional pieces that live inside or around the main modules.

**Tone:** Zero technical language. Friendly, human, approachable — not "cyborg" or cold.

**Module identity colors:**
- Landing Page → amber `#D97706`
- Agente IA → amber `#D97706`
- Content Generator → green `#16a34a`
- Ideas → green `#16a34a`
- Appointments Agent → blue `#3b82f6`
- Recordatorios → blue `#3b82f6`
- Dashboard → purple `#9333ea`

## Page sections structure

The landing page follows a narrative arc of **Problem → Solution → Process → Modules → Proof → Pricing → Trial → Form**:

1. **Hero** — Puzzle visual with 4 main modules + satellites. CTA buttons. Social proof avatars.
2. **Proof bar** — 4 stat metrics (emprendedores, rating, setup time, no-code guarantee).
3. **Problem** — `#problema`, `abrumada.png` image (left) + 3 pain points: task overload, lost clients, complex tools.
4. **Solution** — `#solucion`, before/after composition: noisy chips on the left, dotted connector, and a clear first-piece panel on the right.
5. **How it works** — `#como-funciona`, puzzle-shaped 4-step journey. Step 3 docks with GSAP ScrollTrigger on desktop.
6. **Modules** — `#modulos`, modular offering cards.
7. **Testimonials** — `#testimonios`, 3 cards: 1 featured (dark), 2 standard.
8. **Persona** — `#para-vos`, `nutri.png` image (center) + copy/quote/stats. Left copy column has desktop GSAP parallax.
9. **Pricing** — `#empezar`, pricing copy plus a module-price carousel. The carousel scrolls only inside its own viewport.
10. **Trial CTA** — Free-trial CTA: "Elegí tu módulo y obtené tu primer mes gratis." Button points to `#formulario-startia`.
11. **Form** — `#formulario-startia`, final commercial section before the footer. Keep fields, helpers, errors, Netlify attributes, and inline success status intact.
12. **Footer** — Includes primary section navigation plus secondary links.

## Navigation

- Header links should stay compact and point to real anchors: `#problema`, `#solucion`, `#como-funciona`, `#modulos`, `#testimonios`, `#empezar`.
- Header CTA should point to `#formulario-startia`.
- Footer should include the fuller menu: Problem, Solution, How it works, Modules, Stories, Pricing, Contact, plus secondary links.

## Key images

- `abrumada.png` — Overwhelm section (image left)
- `nutri.png` — Persona section (image center)
- Module images use `picsum.photos/seed/` placeholders

## Component patterns

**Section headers:** tag (small caps gray) → h2 headline → optional subtext
**Cards:** white bg, 28px border-radius, 1px border, subtle shadow, hover lift (+3px)
**Icons:** 52px circles with tinted backgrounds + 24px inline SVG at 1.5 stroke-width
**Lists:** flex column, gap 10–18px, no bullets, use colored checkmarks or dots
**Bento layouts:** Use grid for asymmetric featured cards; responsive to single column on tablets
