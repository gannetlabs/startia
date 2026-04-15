# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

Startia v2 is a standalone landing page for a modular AI tools ecosystem targeting non-technical entrepreneurs. The entire frontend lives in a single `index.html` file — no build tooling, no framework, no package.json. It uses Tailwind CSS via CDN and vanilla JavaScript.

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
