# Baseir Design System — Brand & Foundation Brief

> **Product:** Baseir — Egyptian PropTech B2B SaaS for real estate brokers
> **Stack:** Next.js 16.2 · Tailwind 4 · shadcn/ui · TypeScript
> **Locale:** Bilingual AR (primary) + EN, RTL-first, mobile-first
> **This document tells Claude Design WHO Baseir is visually, so it can design with discipline.**

---

## 1. Brand Identity (Locked)

### 1.1 Aesthetic name — "Tech-Native Discipline"

The aesthetic positioning is **"Now You Don't Have To Argue."** Baseir is the analytical advisor that ends broker-client arguments with numbers. The visual language must feel:

- **Calm, not loud** — restraint over decoration. No gradients, no glassmorphism overuse, no neon.
- **Modern but not flashy** — Linear / Notion / Stripe vibe, NOT Apple-keynote vibe.
- **Numerate first** — numbers are the protagonists. Typography emphasizes data legibility (mono numerals + tight letter-spacing on headings).
- **Confident without being aggressive** — authority through composition discipline, not through bold colors.

Anti-vibes to AVOID:
- ❌ Dated "Egyptian PropTech competitor" look (heavy shadows, default Bootstrap, beige/brown)
- ❌ Crypto/Web3 aesthetic (neon, glitch, dark with cyan accents)
- ❌ Generic SaaS dashboard (white + blue + emoji icons)
- ❌ Government-portal blandness (gray + black + Arial Helvetica)

### 1.2 Tonal direction — Dark uniform across 5 portals

Baseir has 5 user-facing portals — all share the same dark theme:

| Portal | Audience | Theme |
|--------|----------|-------|
| **Broker Portal** | Pro brokers (daily users, ~70% of flows) | Dark uniform, Violet 600 primary |
| **Public Marketplace** | Visitors, lead-gen funnel | Dark uniform, Violet 600 primary |
| **Client Portal** | End-buyers (read-only, broker-curated) | Dark uniform BUT **zero Baseir branding** — uses broker's logo + name + phone |
| **Developer Portal** | Real-estate developers | Dark uniform, Violet 600 primary, **first-class polish** (developers are first-class users) |
| **Admin Portal** | Internal Baseir team | Dark uniform, Violet 600 primary, utilitarian density |

### 1.3 Three forced-light exceptions (auto-applied)

These contexts override the dark theme automatically. Never design them dark:

- **PDF Exports** — printable on paper (saves ink, professional convention)
- **Email Templates** — adaptive `prefers-color-scheme`; default light
- **Open Graph Cards** — WhatsApp/Twitter render OG previews light

All three are server-side rendered with a separate `.light-forced` class scope. The broker has no choice.

---

## 2. Color System Philosophy

### 2.1 Primary color choice — Violet 600 (`#7c3aed`)

Decision rationale (locked, not subject to redesign):
- Egyptian urban professionals associate violet with **modern tech tools** (Linear, Notion, Stripe, Figma)
- Egyptian mourning color is BLACK, not purple — no cultural conflict
- Violet 600 + dark `#0c0c10` background gives WCAG AA contrast (4.5:1+) for all text sizes
- Hover state: Violet 700 `#6d28d9` (slightly darker, NOT a lighter tint)

**Where violet appears:** Only in BROKER-FACING surfaces (Broker, Public, Developer, Admin portals). NOT in Client Portal — Client Portal uses the broker's brand color instead.

### 2.2 Background color — `#0c0c10` (cool near-black)

NOT pure black (`#000`). The slight cool tint:
- Reduces OLED screen burn-in on phones
- Reads as "sophisticated" rather than "default"
- Mirrors Linear's dark mode, which is the closest reference

### 2.3 Semantic tokens, not color names

Every color used in components is a **semantic token**, never a raw color value. This means designs MUST reference tokens, not hex values:

| Semantic intent | Token |
|-----------------|-------|
| Default button | `--primary` |
| Button hover | `--primary-hover` |
| Page background | `--background` |
| Primary text | `--foreground` |
| Secondary text | `--foreground-subtle` |
| Card background | `--card` |
| Inset card | `--card-subtle` |
| Border default | `--border` |
| Border emphasis | `--border-strong` |
| Focus ring | `--ring` / `--ring-brand` / `--ring-error` / etc. |
| Success | `--success` (green) |
| Warning | `--warning` (amber) |
| Error/destructive | `--destructive` (red) |
| Info/emphasis | `--emphasis` (blue) |

### 2.4 Chart palette (6 tokens, ordered)

Charts use a fixed ordering — NEVER pick chart colors ad-hoc:

| Token | Color | Semantic use |
|-------|-------|--------------|
| `--chart-1` | Violet 500 | Primary metric, brand-aligned series |
| `--chart-2` | Emerald 500 | Positive delta, growth, success |
| `--chart-3` | Rose 500 | Negative delta, loss, decline |
| `--chart-4` | Amber 500 | Caution, projected, warning |
| `--chart-5` | Blue 500 | Reference baseline, "actual" |
| `--chart-6` | Teal 500 | Secondary metric |

---

## 3. Typography Philosophy

### 3.1 Why FOUR fonts (not one)

Most B2B SaaS uses 1-2 fonts. Baseir uses 4 deliberately:

| Role | Font | Why this font |
|------|------|---------------|
| English headings | **Plus Jakarta Sans** (400/600/700/800) | Geometric sans with personality; matches modern dashboard aesthetic |
| Arabic headings + body | **IBM Plex Sans Arabic** (400/500/600/700) | Best free Arabic font; pairs visually with Plus Jakarta Sans; handles Arabic + Latin glyphs in mixed text |
| English body | **Inter** (400/500/600) | Workhorse body font; designed for screen legibility |
| Numerals / data / IDs | **JetBrains Mono** (400/500/600) | Monospace ensures column alignment in tables/comparisons; tabular figures by default |

### 3.2 Numerals — English V1 (locked)

Baseir uses **English numerals** (`1234567890`) in V1, even in Arabic UI. Rationale:
- JetBrains Mono has NO Arabic numerals (Latin only)
- Egyptian brokers READ both AR/EN numerals but WRITE in English daily (WhatsApp, Excel, calculator)
- No suitable Arabic monospace font exists (no Cairo Mono, no Tajawal Mono)
- Conditional re-evaluation post-launch IF 3+ of 5 brokers strongly prefer Arabic numerals

**Designs MUST use English numerals for ALL data:** prices, dates, percentages, IDs, calculator output, KPIs. Even in fully Arabic screens.

### 3.3 Type scale (15 sizes total)

Headings (Plus Jakarta Sans / IBM Plex Sans Arabic):

| Token | Size | Line | Tracking | Weight | Use |
|-------|------|------|----------|--------|-----|
| `sp-h1` | 36px | 40px | -0.02em | 800 | Page hero (Dashboard, Project Detail header) |
| `sp-h2` | 24px | 32px | -0.01em | 700 | Section heading (Filters, Comparison) |
| `sp-h3` | 20px | 28px | -0.01em | 700 | Subsection (Card cluster title) |
| `sp-h4` | 16px | 24px | 0 | 600 | Card title |
| `sp-h5` | 14px | 20px | 0.01em | 600 | Caption heading, table column |

Body (Inter / IBM Plex Sans Arabic):

| Token | Size | Line | Weight | Use |
|-------|------|------|--------|-----|
| `sp-body-lg` | 16px | 24px | 400 | Onboarding, marketing copy |
| `sp-body` | 14px | 20px | 400 | Default body |
| `sp-body-medium` | 14px | 20px | 500 | Emphasized inline |
| `sp-body-semibold` | 14px | 20px | 600 | Stronger inline emphasis |

KPI / Data (JetBrains Mono — English numerals V1):

| Token | Size | Line | Use |
|-------|------|------|-----|
| `sp-kpi-hero` | 48px | 48px | Investment Score HERO on Comparison page |
| `sp-kpi-lg` | 32px | 36px | Dashboard primary KPIs |
| `sp-kpi-md` | 24px | 28px | Card-level KPIs |
| `sp-kpi-sm` | 20px | 24px | Inline metrics |
| `sp-data` | 14px | 20px | Table cells, ROI/IRR rows |
| `sp-data-sm` | 12px | 16px | Live ticker, timestamps |
| `sp-order-id` | 13px | 20px | Project IDs, Client Portal slugs |

Labels & Captions:

| Token | Size | Line | Tracking | Weight |
|-------|------|------|----------|--------|
| `sp-label` | 12px | 16px | 0.02em | 500 |
| `sp-label-uppercase` | 11px | 16px | 0.05em UPPER | 600 |
| `sp-caption` | 12px | 16px | 0.01em | 400 |
| `sp-overline` | 10px | 12px | 0.08em UPPER | 600 |

---

## 4. Spacing & Geometry

### 4.1 Spacing scale — 15-step (ShopPulse-derived)

```
0  · 2 · 4 · 6 · 8 · 12 · 16 · 20 · 24 · 32 · 40 · 48 · 56 · 64
   4xs  3xs  2xs  xs  sm   md   lg   xl   2xl  3xl  4xl  5xl  6xl
```

All padding, margin, gap MUST use these tokens. No arbitrary pixel values.

### 4.2 Border radius scale — 10-step

```
0 · 2 · 4 · 6 · 8 · 10 · 12 · 16 · 24 · 9999
   xs  sm  md  lg  10   xl   2xl  3xl  full
```

**Defaults:**
- Buttons: `10px` (between Tailwind `md` 6px and `lg` 8px — slightly more rounded for tactility)
- Cards: `12px` (`xl`)
- Modals / Sheets: `16px` (`2xl`)
- Badges / Pills: `full`
- Inputs: `10px`

### 4.3 Shadows — 7 levels

`shadow-2xs` → `shadow-2xl`. Use shadows sparingly. Dark mode shadows are weaker (darker bg + darker shadow = invisible). Use `border-strong` + subtle inner highlight on dark surfaces instead.

### 4.4 Glass blur — 3 levels

| Class | Backdrop |
|-------|----------|
| `backdrop-blur-md` | 12px |
| `backdrop-blur-lg` | 16px |
| `backdrop-blur-xl` | 24px |

Use only on overlay surfaces (modals, dropdowns, sticky headers). Performance budget: max ONE backdrop-blur per visible frame on mid-tier Android.

### 4.5 Focus rings — 6 contextual

`ring`, `ring-error`, `ring-brand`, `ring-success`, `ring-warning`, `ring-emphasis`. Every interactive element MUST show a visible focus ring on `:focus-visible`. Contrast ≥3:1 against background.

---

## 5. Motion Philosophy

### 5.1 Base animations — 8

`fade-up`, `slide-up`, `scale-in`, `page-in`, `accordion-down`, `accordion-up`, `caret-blink`, `number-transition` (0.3s ease-out, for Investment Score "ripple")

### 5.2 Stagger timing — 25ms

For lists/grids, stagger reveal animations at 25ms intervals (NOT 50ms — 50ms × 4 items = 200ms which feels slow).

### 5.3 Reduced motion — MANDATORY

ALL animations MUST respect `prefers-reduced-motion: reduce`. Replace transitions with instant state changes. No exceptions.

### 5.4 Direction-aware animation (RTL)

Animations that move horizontally MUST flip in RTL. Use logical directions:

| Physical (avoid) | Logical (use) |
|------------------|---------------|
| `slide-in-from-right` | `slide-in-from-end` |
| `slide-in-from-left` | `slide-in-from-start` |
| Sheet `side="right"` | Sheet `side="end"` |
| Toast `bottom-right` | Toast `bottom-end` |

---

## 6. RTL Strategy

### 6.1 Logical properties, never physical

All spacing/layout uses logical Tailwind properties:
- `ms-4` / `me-4` (margin-start, margin-end) — NOT `ml-4` / `mr-4`
- `ps-4` / `pe-4` (padding-start, padding-end) — NOT `pl-4` / `pr-4`
- `inset-inline-start` — NOT `left`
- `text-start` / `text-end` — NOT `text-left` / `text-right`

### 6.2 Mixed-direction text

Arabic UI often contains Latin tokens (broker slugs, project IDs, hashtags, English numerals). Use:
- `dir="auto"` on bidirectional text containers
- `<bdi>` element to wrap currency, IDs, numerals
- Test in BOTH RTL (Arabic) AND LTR (English) modes on every screen

### 6.3 Designs MUST show both modes

Every design Claude Design produces MUST show the screen in:
1. RTL Arabic (the default — broker primary language)
2. LTR English (the secondary mode)

NOT just one. Both. Side-by-side preferred.

---

## 7. Component Strategy — 3-Tier Architecture

### Tier 1 — Foundation tokens (this file)
CSS variables in `tokens.css`. Single source of truth.

### Tier 2 — Generic components (~40, themed shadcn/ui)

Standard primitives, themed with Baseir tokens. Examples:
- **Form:** Button, Input, Select, Checkbox, Radio, Switch, Slider, Textarea, Label, FormField
- **Data Display:** Card, Table, Badge, Avatar, Separator, Skeleton, Tooltip
- **Feedback:** Alert, AlertDialog, Toast (Sonner), Progress, Spinner
- **Navigation:** Tabs, Breadcrumb, Pagination, NavigationMenu, Command (cmdk)
- **Overlay:** Dialog, Drawer (Vaul on mobile), Sheet, Popover, DropdownMenu, ContextMenu, HoverCard
- **Layout:** AppLayout (shell), ResizablePanel, ScrollArea, AspectRatio

ALL Tier 2 components MUST have:
- Default state design
- Hover state design
- Focus state design
- Disabled state design
- Loading state (skeleton variant)
- Error state (where applicable)

### Tier 3 — Baseir-specific patterns (~20-30, custom)

Components with Baseir business logic baked in:
- **FactorForm** — 34-factor investment input with tooltip dictionary
- **ComparisonMatrix** — 4-variant side-by-side with color-coded diff
- **ConfidenceGauge** — InstaPay verification confidence (per-check breakdown)
- **KanbanPipeline** — CRM drag-drop client stages
- **PriceHistoryChart** — sold-out unit price history with scrubber
- **ClientPortalLayout** — broker-only branding, zero Baseir attribution
- **FrancoArabSearchInput** — trilingual search (AR + EN + Franco-Arab)
- **SavingsCounter** — quarterly brag card (single designed exception)
- **LiveTickerBar** — real-time data updates, horizontal scroll
- **BragCard, StreakCounter, DeliveryScoreBadge** — likely Tier 2 (styled, no logic)

See `component-inventory.md` for full list.

---

## 8. Egyptian-Native Component Library

Baseir-specific typed wrappers for Egyptian-locale primitives. Designs MUST visually account for these:

```tsx
<EgyptianCurrency amount={5000000} numeralLanguage="en" />
// Renders: "5,000,000 ج.م" — JetBrains Mono number, IBM Plex Sans Arabic currency symbol, Bidi-safe

<EgyptianPhone number="01012345678" />
// Renders: "+20 10 1234 5678" — JetBrains Mono, with country code

<EgyptianDate date={d} format="long" />
// Renders: "الجمعة 28 أبريل 2026" — IBM Plex Sans Arabic, Friday-Saturday weekend respected

<MonoNumber value={1234.56} precision={2} thousandsSeparator="," />
// JetBrains Mono, tabular figures, Bidi-safe

<PercentDelta value={-3.2} colorCoded showSign />
// "-3.2%" colored via semantic token (red/green/foreground-subtle)

<ProjectId id="P-2026-1234" />
// JetBrains Mono, non-breaking

<AreaSize sqm={250} unit="sqm" />
// "250 م²" — number + Arabic unit symbol, Bidi-safe
```

**Designs MUST use these visual conventions consistently.** Currency always has `ج.م` after the number. Phone always shows `+20` country code. Dates always include the Arabic day name in Arabic locale.

---

## 9. Design Principles — 8 Locks

When Claude Design generates any screen, it MUST satisfy:

1. **Glanceable** — primary information visible within 3 seconds. No buried KPIs.
2. **Baseir Invisible in Service of Broker's Brand** — Client Portal shows broker logo + name + phone, ZERO Baseir attribution.
3. **Numbers Always Look Serious** — KPIs use JetBrains Mono, tabular figures, never decorative fonts.
4. **Skeleton Before Spinner** — loading states are skeleton placeholders, not spinners. (Spinner only for <1s waits.)
5. **Smart Defaults That Run Untouched** — most user flows complete without changing any default value.
6. **Tiered Recalc Budget** — instant <100ms for primitive inputs, <300ms for derived metrics, <800ms for full recalculation.
7. **Bilingual Without Compromise** — every screen feels native in both AR and EN. Not "AR is a translation of EN".
8. **The Promise Lives in the Product** — "Now You Don't Have To Argue" must be felt, not just said. Show the broker winning the argument with numbers.

---

## 10. Anti-Patterns — DO NOT design

| Pattern | Why |
|---------|-----|
| White cards on dark background with no border | Looks like default Tailwind — lazy |
| Neon glow on every button | Mid-tier Android at 25% brightness can't see it; loses brand discipline |
| Decorative gradients in backgrounds | Date themselves; harder to maintain RTL parity |
| Emoji icons | Inconsistent across OS/browsers; use Lucide icons only |
| Pure black `#000` background | Causes OLED smearing; use `#0c0c10` |
| Dropdown arrows pointing inward | Direction-confusion in RTL; use chevrons that visually match (down for collapse, end for expand) |
| Toasts in top-right corner | In RTL, top-right is the START position (busy area); use `bottom-end` |
| Date pickers showing Sunday as first day | Egyptian weeks start Saturday; weekend = Friday-Saturday |
| Phone inputs without `+20` country prefix | Brokers WhatsApp internationally; missing prefix = confusion |
| Currency without `<bdi>` wrapper | RTL Bidi causes `5,000,000 ج.م` to render mangled |

---

## 11. References

- `tokens.css` — actual CSS variable definitions (Tailwind v4 format)
- `typography-specimens.md` — type scale with rendered specimens
- `component-inventory.md` — full Tier 2 + Tier 3 component list

This document is the canonical Baseir design system brief. If Claude Design needs to make a design decision not covered here, defer to this document's principles or ask for clarification.
