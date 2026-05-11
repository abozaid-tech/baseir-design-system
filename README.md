# Baseir — Org-Level Design System for Claude Design

This folder contains everything Claude Design needs to extract the Baseir design system at the **organization level** (one-time setup, before per-epic projects start).

## What's in this folder

| File | Purpose | Upload as |
|------|---------|-----------|
| `design-system-brief.md` | Single comprehensive document — brand identity + design philosophy + token philosophy + component strategy | Main attachment |
| `tokens.css` | Canonical Tailwind v4 CSS variables (colors, typography, spacing, radius, shadows, motion, RTL utilities) | Attachment (Claude Design parses CSS variables natively) |
| `typography-specimens.md` | Font stack + type scale with rendered examples | Attachment |
| `component-inventory.md` | List of all Tier 2 + Tier 3 components expected to be designed across the project | Attachment (helps Claude Design plan component reuse) |

## How to use (Claude Design org setup)

1. Sign in to [claude.ai/design](https://claude.ai/design)
2. Create an **organization** named **"Baseir"** (top-left org switcher → New Organization)
3. Open the org's **Design System** section
4. Upload all 4 files in this folder (drag-and-drop or file picker)
5. Claude Design parses them and shows an extracted summary (colors, typography, components)
6. Review the extraction:
   - All 14 color palettes appear with correct hex values
   - 4 fonts (IBM Plex Sans Arabic, Plus Jakarta Sans, Inter, JetBrains Mono) registered
   - Spacing/radius scales appear
7. Toggle **"Published"** so every per-epic project under this org inherits the system

## Why this works without a GitHub repo

Claude Design's `phase-04-claude-design-loop.md` reference recommends either:
- **Best:** linking the GitHub repo containing component library + styles, OR
- **Alternative:** manually uploading color palette + typography specimens + component screenshots

Baseir has no code yet (Story 2.1 hasn't run), so we use the alternative. The `tokens.css` + `design-system-brief.md` together give Claude Design enough context to extract the system as if it had read a real codebase.

## After the org is set up

This setup is **one-time per project**. After it's done, the per-epic loop begins:
1. Create a new Claude Design project for Epic N
2. The project automatically inherits the org's design system
3. Upload epic-specific context (stories, journey notes)
4. Iterate on designs
5. Export → handoff bundle → `bmad-sync-from-design` propagates back to stories

Never touch this `00-design-system/` folder again unless the design system itself changes (token rename, palette swap, new font).
