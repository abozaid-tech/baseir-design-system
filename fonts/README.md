# Baseir Brand Fonts

18 `.woff2` files covering Baseir's 4-font stack at all required weights, subset-pruned to Latin (+ Arabic for IBM Plex Sans Arabic).

**Total payload:** ~583 KB across all files.
**Source:** Google Fonts (downloaded via `fonts.googleapis.com/css2` API on 2026-05-11).
**License:** SIL Open Font License (OFL-1.1) — free for commercial use.

---

## File Inventory

### Plus Jakarta Sans — English headings (Tokotype)
- `plus-jakarta-sans-400-latin.woff2` — Regular (26 KB)
- `plus-jakarta-sans-600-latin.woff2` — SemiBold (26 KB)
- `plus-jakarta-sans-700-latin.woff2` — Bold (26 KB)
- `plus-jakarta-sans-800-latin.woff2` — ExtraBold (26 KB)

### Inter — English body text (Rasmus Andersson)
- `inter-400-latin.woff2` — Regular (47 KB)
- `inter-500-latin.woff2` — Medium (47 KB)
- `inter-600-latin.woff2` — SemiBold (47 KB)

### JetBrains Mono — Numerals / data / IDs (JetBrains s.r.o.)
- `jetbrains-mono-400-latin.woff2` — Regular (30 KB)
- `jetbrains-mono-500-latin.woff2` — Medium (30 KB)
- `jetbrains-mono-600-latin.woff2` — SemiBold (30 KB)

### IBM Plex Sans Arabic — Arabic headings + body (IBM)
**Two subsets per weight** — browsers auto-pick based on character:
- `ibm-plex-sans-arabic-400-arabic.woff2` (41 KB) + `ibm-plex-sans-arabic-400-latin.woff2` (18 KB) — Regular
- `ibm-plex-sans-arabic-500-arabic.woff2` (44 KB) + `ibm-plex-sans-arabic-500-latin.woff2` (19 KB) — Medium
- `ibm-plex-sans-arabic-600-arabic.woff2` (44 KB) + `ibm-plex-sans-arabic-600-latin.woff2` (20 KB) — SemiBold
- `ibm-plex-sans-arabic-700-arabic.woff2` (43 KB) + `ibm-plex-sans-arabic-700-latin.woff2` (19 KB) — Bold

---

## Usage

### In production (Next.js / Tailwind 4)

Copy this entire `fonts/` directory into `apps/web/public/fonts/`. The `fonts.css` file has `@font-face` declarations with relative `./*.woff2` paths — just link it from your root `<head>` (or import in your global CSS):

```html
<link rel="stylesheet" href="/fonts/fonts.css" />
```

Or in Tailwind 4 global CSS:

```css
@import url('/fonts/fonts.css');
```

`tokens.css` already references these font families by name — no changes needed.

### In Claude Design (Upload fonts button)

Open [the Baseir design system](https://claude.ai/design/p/019e1771-2754-7cf0-a62a-b3625a285015) and click the **"Upload fonts"** button in the top alert. Either:

1. **Drag all 18 `.woff2` files** in one go (preferred — single upload), OR
2. **Drag the `baseir-fonts.zip`** if the upload dialog accepts archives, OR
3. Upload one family at a time if there's a per-family limit

Claude Design parses the `@font-face` data embedded in each `.woff2` and registers them under their respective family names automatically.

---

## Why Latin-only for 3 of 4 fonts

Plus Jakarta Sans, Inter, and JetBrains Mono are only used for **English content** in Baseir (headings, body text, numerals). The Arabic UI is rendered entirely in IBM Plex Sans Arabic. Stripping non-Latin subsets cuts ~40 KB per font weight.

IBM Plex Sans Arabic includes both Arabic and Latin subsets because mixed-direction text (e.g., Arabic sentences with English brand names or numbers) requires it to fall back gracefully to Latin glyphs.

---

## Subset Coverage

The `unicode-range` declarations in `fonts.css` ensure browsers fetch only the file matching each character. So an Arabic-heavy page on slow Egyptian mobile networks fetches just the Arabic subset of IBM Plex Sans Arabic, not the Latin one.

Approximate fetch sizes per page locale:
- **Mostly Arabic UI:** IBM Plex Sans Arabic-arabic.woff2 (4 weights × ~43 KB ≈ 170 KB) + JetBrains Mono Latin (numbers) (~30 KB) = ~200 KB
- **Mostly English UI:** Plus Jakarta Sans + Inter Latin (~150 KB) + JetBrains Mono Latin (~30 KB) = ~180 KB
- **Mixed:** Browser fetches only what each character needs
