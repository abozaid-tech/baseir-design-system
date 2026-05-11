# Baseir Typography Specimens

Visual specimens of how each font + size combination should render. Use this as the reference when designing any text in Claude Design.

---

## Font Stack Overview

| Role | Font | Weights Used | Where |
|------|------|--------------|-------|
| English Headings | **Plus Jakarta Sans** | 400, 600, 700, 800 | All English headings |
| Arabic Headings + Body | **IBM Plex Sans Arabic** | 400, 500, 600, 700 | All Arabic text (headings + body unified for cleaner pairing) |
| English Body | **Inter** | 400, 500, 600 | English body text only |
| Numerals / Data / IDs | **JetBrains Mono** | 400, 500, 600 | ALL numbers (prices, dates, percentages, IDs) — even in Arabic UI |

**Self-hosted in `/public/fonts/`.** All four are free + open source.

---

## Headings — Rendered Specimens

### `sp-h1` — 36px / 40px line / -0.02em / weight 800

**English:**
> # Investment Analysis

**Arabic:**
> # تحليل الاستثمار

Used for: Page hero (Dashboard, Project Detail header, Comparison header)
Frequency: ONE per page, max.

---

### `sp-h2` — 24px / 32px line / -0.01em / weight 700

**English:**
> ## Compare 4 Units Side-by-Side

**Arabic:**
> ## مقارنة 4 وحدات جنباً إلى جنب

Used for: Major section headings (Filters, Comparison sections, Pipeline columns)

---

### `sp-h3` — 20px / 28px line / -0.01em / weight 700

**English:**
> ### Investment Metrics

**Arabic:**
> ### مقاييس الاستثمار

Used for: Subsection headings, card cluster titles

---

### `sp-h4` — 16px / 24px line / 0 / weight 600

**English:**
> #### Maintenance Fees

**Arabic:**
> #### رسوم الصيانة

Used for: Card titles, modal section headings, form group titles

---

### `sp-h5` — 14px / 20px line / 0.01em / weight 600

**English:**
> ##### Property Type

**Arabic:**
> ##### نوع العقار

Used for: Caption-level headings, table column headers, sidebar item labels

---

## Body Text — Rendered Specimens

### `sp-body-lg` — 16px / 24px / weight 400

**English (Inter):**
> Welcome to Baseir. Your daily companion for analyzing Egypt's off-plan real estate market with confidence.

**Arabic (IBM Plex Sans Arabic):**
> أهلاً بك في بصير. رفيقك اليومي لتحليل سوق العقارات تحت الإنشاء في مصر بثقة.

Used for: Onboarding copy, marketing copy, empty state explanations

---

### `sp-body` — 14px / 20px / weight 400

**English:**
> The project is located 2.5km from Cairo Festival City Mall. The developer has delivered 8 projects on time over the past 5 years.

**Arabic:**
> المشروع يقع على بعد 2.5 كم من مول كايرو فستيفال سيتي. المطور سلم 8 مشاريع في الوقت المحدد خلال 5 سنوات.

Used for: Default body text everywhere. The workhorse style.

---

### `sp-body-medium` — 14px / 20px / weight 500

**English:**
> **Reminder:** Trial expires in 7 days.

**Arabic:**
> **تذكير:** التجربة تنتهي خلال 7 أيام.

Used for: Slight emphasis inline, banner copy, alert messages.

---

### `sp-body-semibold` — 14px / 20px / weight 600

**English:**
> **Premium feature** — upgrade to unlock.

**Arabic:**
> **ميزة احترافية** — رقّ اشتراكك لفتحها.

Used for: Stronger inline emphasis. Use sparingly.

---

## KPIs / Data — JetBrains Mono (English Numerals V1)

### `sp-kpi-hero` — 48px / 48px line

```
8.4
```

Used for: **ONE** KPI per Comparison page — the Investment Score HERO. This is the AHA moment.

---

### `sp-kpi-lg` — 32px / 36px line

```
5,000,000 ج.م
```

Used for: Dashboard primary KPIs (Total Portfolio Value, Top Comparison Result, Saved Searches Total)

---

### `sp-kpi-md` — 24px / 28px line

```
+12.4%
```

Used for: Card-level KPIs (ROI, IRR, Capital Appreciation per scenario)

---

### `sp-kpi-sm` — 20px / 24px line

```
3,250,000
```

Used for: Inline metrics within cards (e.g., variant price in a comparison row)

---

### `sp-data` — 14px / 20px line

```
4Q 2027 | 25% DP | 84 months
```

Used for: Table cells (Comparison Matrix rows), payment plan details, factor configurator values

---

### `sp-data-sm` — 12px / 16px line

```
Updated 14:32 today
```

Used for: Live ticker bar, timestamps, last-modified labels

---

### `sp-order-id` — 13px / 20px line

```
P-2026-1234
```

Used for: Project IDs, Client Portal slugs, Order/Subscription IDs

---

## Labels & Captions

### `sp-label` — 12px / 16px / 0.02em / weight 500

**English:**
> Email Address

**Arabic:**
> البريد الإلكتروني

Used for: Form field labels (above inputs)

---

### `sp-label-uppercase` — 11px / 16px / 0.05em UPPER / weight 600

**English:**
> AVAILABLE UNITS

**Arabic:**
> الوحدات المتاحة

(Note: Arabic doesn't have case; renders as bold + tracking)

Used for: Section dividers, sidebar group headings (Tarek's Pipeline → ACTIVE LEADS)

---

### `sp-caption` — 12px / 16px / 0.01em / weight 400

**English:**
> Updated 2 hours ago by Ahmed

**Arabic:**
> تم التحديث منذ ساعتين بواسطة أحمد

Used for: Metadata, hint text, "powered by" text

---

### `sp-overline` — 10px / 12px / 0.08em UPPER / weight 600

**English:**
> NEW

**Arabic:**
> جديد

Used for: Badge text, tag micro-labels

---

## Mixed-Direction Text (Critical Spec)

Arabic UI often contains Latin tokens. ALL of the following are CORRECT:

| Mixed text | Direction handling |
|-----------|---------------------|
| `أحمد - P-2026-1234` | `dir="auto"` on container; Latin ID stays LTR |
| `5,000,000 ج.م` | `<bdi>` wrapper around `5,000,000`; `ج.م` reads right-to-left |
| `+20 10 1234 5678` | Phone always renders LTR even in Arabic UI; use `dir="ltr"` |
| `الجمعة 28 أبريل 2026` | Date — day name AR, number EN, month name AR — `dir="auto"` |
| `Cairo Festival City Mall` | English landmark name kept LTR inside Arabic paragraph |

**Designs MUST visually demonstrate these mixed-direction cases.** A monolingual Arabic mockup hides this critical UX risk.

---

## Numeral Rendering Examples

JetBrains Mono numerals in JSON-like tabular use:

| Field | Value |
|-------|-------|
| Price | `5,000,000` |
| Price per sqm | `25,000` |
| Down Payment % | `25%` |
| Delivery | `Q4 2027` |
| Years to Sell | `5` |
| ROI | `+12.4%` |
| Maintenance Fee | `0 ج.م` (Free) — semantic green color |
| Discount | `-3.2%` (Off-Plan) — semantic green color |

**Critical rule:** Negative deltas use semantic `--destructive` (red), positive deltas use semantic `--success` (green). NEVER use yellow/orange for negative — that's "warning," not "loss."

---

## Don't-Do List

| Pattern | Why not |
|---------|---------|
| Arabic numerals (`٥،٠٠٠،٠٠٠`) anywhere in V1 | English locked V1; revisit post-launch |
| Numbers in IBM Plex Sans Arabic | Use JetBrains Mono — tabular alignment matters |
| Italic Arabic text | Arabic doesn't italicize naturally; renders as forced italic = ugly |
| Underlined links | Use color (`--primary`) + on-hover underline only |
| ALL-CAPS Arabic | Arabic doesn't have case — looks weird as forced bolder |
| `text-left` / `text-right` | Use `text-start` / `text-end` — RTL-safe |
| Tabular figures via CSS only without JetBrains Mono | Inter/IBM Plex tabular variants exist but JetBrains Mono is the locked decision |
