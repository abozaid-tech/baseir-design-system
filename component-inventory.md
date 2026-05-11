# Baseir Component Inventory

Complete list of components that will be designed across all per-epic Claude Design sessions. This list lets Claude Design plan **component reuse** instead of redesigning the same primitive 5 times.

---

## Tier 2 — Generic shadcn/ui primitives (themed with Baseir tokens)

~40 components. All MUST be designed with these state coverages:
- Default
- Hover
- Focus (`:focus-visible` ring)
- Active / pressed
- Disabled
- Loading (skeleton variant)
- Error (where applicable)

### Form (12)

| Component | Notes |
|-----------|-------|
| Button | Variants: `default`, `destructive`, `outline`, `ghost`, `secondary`, `link` · Sizes: `xs`, `sm`, `default`, `lg`, `icon` · Always rounded `radius-10` |
| Input | Email, text, password, number variants · Prefix/suffix slot · Error state with `--ring-error` |
| Textarea | Auto-grow variant · Character counter slot |
| Select | Single-value · With search (cmdk-powered) · Inline-search rule: 10+ options → search visible |
| Combobox | Multi-value variant · Async search support |
| Checkbox | With label + description slot |
| Radio | Group only — never standalone |
| Switch | With label slot · For binary settings |
| Slider | Single-value + range variants · `--chart-1` track fill |
| Label | Above inputs · `sp-label` token |
| FormField | Composed: Label + control + description + error message · Used in React Hook Form |
| FormErrorMessage | `--destructive` semantic color · Inline below input |

### Data Display (8)

| Component | Notes |
|-----------|-------|
| Card | Default radius `xl` · Background `--card` · Hoverable variant for clickable cards |
| Table | Header sticky · Sortable column indicators · TanStack Table-powered |
| Badge | Variants: `default`, `success`, `warning`, `destructive`, `emphasis`, `outline` · Always `rounded-full` |
| Avatar | Sizes: `xs`, `sm`, `md`, `lg`, `xl` · Initial fallback · Group stack variant |
| Separator | Horizontal + vertical · `--border` color |
| Skeleton | Shimmer animation · Per Tier 2 component, MANDATORY |
| Tooltip | Radix-powered · Auto-positioned (avoid viewport edges) · 200ms delay default |
| Empty State | Illustration slot · Title + description + optional CTA |

### Feedback (5)

| Component | Notes |
|-----------|-------|
| Alert | Variants: `default`, `success`, `warning`, `destructive`, `emphasis` · Icon slot · Dismissible variant |
| AlertDialog | Confirmation pattern · Cancel + Action buttons · Async loading on Action |
| Toast (Sonner) | Position: `bottom-end` (NOT bottom-right — RTL-safe) · 4 variants matching Alert |
| Progress | Linear · Determinate + indeterminate · `--primary` fill |
| Spinner | Last resort (use Skeleton instead) · For <1s waits only |

### Navigation (6)

| Component | Notes |
|-----------|-------|
| Tabs | Horizontal · Active tab `--primary` underline · Animated indicator (direction-aware) |
| Breadcrumb | Separator: `›` chevron · Last item non-clickable · RTL-flipping |
| Pagination | Page numbers + prev/next · Compact variant for mobile |
| NavigationMenu | Top header dropdown menus · Hover-open desktop, click-open mobile |
| Command (cmdk) | ⌘K palette · Recent + Search + Groups · Vaul drawer fallback on mobile |
| Stepper | Onboarding wizard · Horizontal desktop, vertical mobile · Active + completed states |

### Overlay (7)

| Component | Notes |
|-----------|-------|
| Dialog | Centered modal · Backdrop blur · Close on Esc · Max-width `2xl` |
| Drawer (Vaul) | Mobile bottom-sheet · Drag-to-dismiss · Snap points |
| Sheet | Side panel · `side="end"` default (NOT `right`) · Direction-aware |
| Popover | Smaller than Dialog · Positioned relative to trigger · Auto-flip on edge |
| DropdownMenu | Right-click + button-triggered · Keyboard navigable · Grouped items |
| ContextMenu | Right-click only · Same items as DropdownMenu typically |
| HoverCard | Desktop-only · Avatar / preview popups · 700ms delay |

### Layout (5)

| Component | Notes |
|-----------|-------|
| **AppLayout** | THE shell · Sidebar + header + main content area · ⚠️ Build FIRST (Phase 4 pre-flight) |
| ResizablePanel | Comparison Matrix variant adjuster |
| ScrollArea | Custom styled scrollbar · For overflowing card content |
| AspectRatio | Property image grids · `16/9` and `4/3` variants |
| Container | Max-width constraint · `max-w-screen-baseir` (1440px) for DashboardLayout |

---

## Tier 3 — Baseir-specific patterns (business logic baked in)

~20-30 patterns. Each has its own dedicated design session in the relevant epic.

### Phase 4 — Epic 2 (Foundation & Auth)

| Pattern | Belongs in Epic | Why Tier 3 |
|---------|-----------------|------------|
| AuthLayout | Epic 2 | Centered card on dark gradient bg · Logo top, form middle, footer bottom · Different from AppLayout |
| OnboardingWizard | Epic 2 / Epic 16 | Step indicator + slide animation + form per step · Validation rules embedded |
| BrandingSetupCard | Epic 2 | Logo upload + color picker preview + name preview · Live preview pane |
| TrialBanner | Epic 2 / Epic 16 | Persistent banner showing "X days left" · Auto-dismiss on conversion |

### Phase 4 — Epic 3 (Projects & Search)

| Pattern | Belongs in Epic | Why Tier 3 |
|---------|-----------------|------------|
| FrancoArabSearchInput | Epic 3 | Single input handling AR + EN + Franco-Arab · Trilingual hint chips · Bidi-safe |
| ProjectCard | Epic 3 | Image + price + delivery + score + actions · Hot-deal variant + sold-out variant |
| FilterPanel | Epic 3 | Collapsible per group · 3-mode maintenance fee filter (Free / % / Amount) · RTL-aware |
| SortDropdown | Epic 3 | Per-attribute · Asc/desc toggle · Multi-sort V1.5 |
| ProjectMap | Epic 3 / Epic 4 | MapLibre clustering · Landmark distance overlay |

### Phase 4 — Epic 4 (Comparison & Investment)

| Pattern | Belongs in Epic | Why Tier 3 |
|---------|-----------------|------------|
| **ComparisonMatrix** | Epic 4 | 4-column side-by-side · Color-coded diff (green/red) · Unified vs Per-Unit toggle · Sticky first column · WOW moment |
| **FactorForm** | Epic 4 | 34-factor form · Default vs optional groups · Tooltip dictionary · Live recalc · Workspace + Present-to-Client modes |
| ScenarioSwitcher | Epic 4 | 4 scenario type tabs · Saved scenarios dropdown · Max 3 named per analysis |
| **InvestmentScoreHero** | Epic 4 | `sp-kpi-hero` 48px number · Number-transition ripple animation · Top 2 sliders highlighted |
| QuickCalculator | Epic 4 | Standalone version of FactorForm · Manual entry mode |

### Phase 4 — Epic 5 (Market Intelligence)

| Pattern | Belongs in Epic | Why Tier 3 |
|---------|-----------------|------------|
| MarketTrendChart | Epic 5 | Recharts line + area · Time scrubber · Multi-series overlay |
| AreaHeatmap | Epic 5 | MapLibre + custom layer · Price/sqm gradient |
| **LiveTickerBar** | Epic 5 | Horizontal scroll · Real-time updates · 25ms stagger reveal |

### Phase 4 — Epic 6 (Satellite & Construction)

| Pattern | Belongs in Epic | Why Tier 3 |
|---------|-----------------|------------|
| **PriceHistoryChart** | Epic 6 | Recharts with scrubber UI · Price aggregation per quarter · Sold-out markers |
| SatelliteImageViewer | Epic 6 | Image comparison slider · Date timeline · Annotation overlay |
| ConstructionScoreBadge | Epic 6 | Color thresholds (red/amber/green) · Tooltip with breakdown |

### Phase 4 — Epic 7 (Notifications)

| Pattern | Belongs in Epic | Why Tier 3 |
|---------|-----------------|------------|
| NotificationCenter | Epic 7 | Bell icon + popover · Read/unread states · Deep-link rows · Empty state |
| ChannelSelectorMatrix | Epic 7 | Admin-configurable matrix · User can reduce, not add · Per-type independent muting |
| DigestEmailPreview | Epic 7 | Email render preview · Forced-light variant |

### Phase 4 — Epic 9 (CRM)

| Pattern | Belongs in Epic | Why Tier 3 |
|---------|-----------------|------------|
| **KanbanPipeline** | Epic 9 | Drag-drop columns (V1.5) · Status dropdown (V1) · Per-stage count · Color-coded client temperature |
| ClientCard | Epic 9 | Hot/Warm/Cold badge · Source tag · Linked projects · Last-contacted timestamp |
| WhatsAppTemplateModal | Epic 9 | Variable substitution preview · Send button · Template gallery |
| ReminderModal | Epic 9 | DatePicker + time · Google Calendar sync toggle · Notes field |

### Phase 4 — Epic 13/14 (Export & Client Portal)

| Pattern | Belongs in Epic | Why Tier 3 |
|---------|-----------------|------------|
| ExportPreviewModal | Epic 13 | PDF/Excel toggle · Full vs Executive Summary toggle · Language toggle (AR/EN) |
| **ClientPortalLayout** | Epic 14 | Broker-only branding · Zero Baseir attribution · Read-only navigation · `.light-forced` if PDF |
| InboundMessageWidget | Epic 14 | Max 3/24h limit · Max 1000 chars · Captcha for unverified · Send confirmation |

### Phase 4 — Epic 20 (Payments)

| Pattern | Belongs in Epic | Why Tier 3 |
|---------|-----------------|------------|
| **ConfidenceGauge** | Epic 20 | InstaPay verification · Per-check breakdown · Threshold colors (red <70%, amber 70-80%, green >80%) |
| InstaPayScreenshotUploader | Epic 20 | Drag-drop + camera capture · OCR preview · Manual override |
| PaymobIframeEmbed | Epic 20 | Themed wrapper · Loading skeleton · Error fallback |
| SubscriptionFSMDiagram | Epic 20 | Internal admin only · Visualized xstate v5 graph |
| **SavingsCounter** | Multiple | Brand anchor counter · "You've saved 2 hours" · Once-in-a-lifetime first-comparison celebration |
| **BragCard** | Multiple | Quarterly brag · Designed exception to "restraint" rule · Strict implementation rules (see UX §7.6) |

### Always-Present (App Shell)

| Pattern | Notes |
|---------|-------|
| **AppLayout** | THE shell — designed in Phase 4 pre-flight, BEFORE per-epic loops start |
| TopHeader | Logo + search + language toggle + numeral toggle (post-launch) + notification bell + user menu |
| Sidebar | Nav items + active highlighting + collapsed/expanded states + tenant switcher (Enterprise) |
| UserMenu | Avatar + dropdown · Profile + Settings + Billing + Logout |
| TenantSwitcher | Enterprise-only · Office name + role badge |

---

## Component Count Summary

| Tier | Component Count | Location |
|------|-----------------|----------|
| Tier 1 | Tokens only | `src/styles/tokens.css` |
| Tier 2 | ~40 generic components | `src/components/ui/` |
| Tier 3 | ~25 Baseir patterns | `src/components/baseir/` |
| Egyptian-Native wrappers | 7 wrappers | `src/lib/egyptian-native/` |

**Total: ~96 components.** Most appear in multiple epics. Phase 4 per-epic sessions MUST reuse components, not redesign them.

---

## Component Reuse Map (per Epic)

Hint to Claude Design — these components appear in MULTIPLE epics; design once, reuse always:

| Component | Used in Epics |
|-----------|---------------|
| AppLayout | ALL epics |
| ProjectCard | 3, 4, 5, 9, 13, 14 |
| FactorForm | 4, 13 |
| ComparisonMatrix | 4, 13 |
| NotificationCenter | ALL epics (header bell) |
| TrialBanner | 2, 16, 20 |
| EmptyState | ALL epics (per page) |
| Skeleton variants | ALL epics (loading states) |
| ConfirmationDialog | ALL epics (destructive actions) |

When designing Epic N, check this map. If a component appears here AND was designed in a previous epic, REUSE the existing design — don't redesign.
