# studio-bayu — Design System

Deze file is de single source of truth voor visuele en technische keuzes. Raadpleeg hem vóór elke UI-wijziging. Alle tokens leven in `src/styles/globals.css`.

---

## Project

- **Naam:** studio-bayu
- **Type:** Portfolio
- **Framework:** Astro
- **Max breedte:** 1200px

---

## Context & intake

- **Vibe:** editorial, verfijnd, warm-natuurlijk (luxe-minimalisme, beauty/wellness-achtig)
- **Merkwaarden:** verfijnd, sereen, natuurlijk
- **Theme:** light only (dark mode bewust niet meegenomen — past bij editorial-vibe)
- **Density:** luchtig/spacious — veel whitespace, generous section-padding
- **Motion:** subtiel (fade-up on scroll, zachte hover-states)
- **Referentielayout:** alternerende cream + deep-taupe "banden" met portrait-fotografie (zie `brand/`-moodboard)

---

## Kleuren

Palette "Studio Bayu" — warm-aards, editorial.

| Token | Hex | Naam | Gebruik |
|---|---|---|---|
| `--bg` | `#F1EADA` | Vanilla | Primaire achtergrond |
| `--bg-alt` | `#CEC1A8` | Sand | Sectie-contrast, subtiele cards |
| `--bg-deep` | `#AAA396` | Mountain | Donkere contrast-band |
| `--fg` | `#584738` | Mahogany | Body + headings op light |
| `--fg-inverse` | `#F1EADA` | — | Tekst op `--bg-deep` |
| `--accent` | `#B59E7D` | Tobacco | CTA's, links, highlights |
| `--muted` | `#8A7F6F` | — | Secundaire tekst |
| `--border` | `#D9CFB8` | — | Subtiele lijnen |

### Semantic (harmonieus met palet)

| Token | Hex | Gebruik |
|---|---|---|
| `--success` | `#8A9B7F` | Sage-groen |
| `--danger` | `#B85C44` | Warme terracotta |
| `--warning` | `#C79B5A` | Honing-amber |

### Sectie-patronen

- `.section` — default: Vanilla bg + Mahogany fg
- `.section--alt` — Sand bg (zachte contrast-band)
- `.section--deep` — Mountain bg + Vanilla fg (donkere showcase-band, zoals SEREIN in ref)

---

## Typografie

### Families

- `--font-display`: `'TAN Nimbus', 'Playfair Display', Georgia, serif`
  - Self-hosted (`public/fonts/TAN-Nimbus.woff2` + `.woff` fallback)
  - Gelicenseerd — niet publiek delen of doorgeven
- `--font-body`: `'Quicksand', -apple-system, BlinkMacSystemFont, sans-serif`
  - Self-hosted, 5 weights (300/400/500/600/700) als `.ttf` in `public/fonts/`

### Scale

| Element | Size | Line-height | Family |
|---|---|---|---|
| `h1` | `clamp(2.5rem, 6vw, 5rem)` | 1.05 | display |
| `h2` | `clamp(2rem, 4.5vw, 3.5rem)` | 1.1 | display |
| `h3` | `clamp(1.5rem, 3vw, 2.25rem)` | 1.2 | display |
| `h4` | `clamp(1.25rem, 2.25vw, 1.75rem)` | 1.3 | display |
| `body` | `1.05rem` | 1.7 | body 400 |
| `.eyebrow` | `0.8rem` | — | body 500, `letter-spacing: 0.2em`, uppercase |

Letter-spacing op headings: `-0.01em` (subtiele tightening voor display-serif).

---

## Spacing & layout

Base-unit: **8px**. Schaal:

| Token | Waarde |
|---|---|
| `--space-xs` | 4px |
| `--space-sm` | 8px |
| `--space-md` | 16px |
| `--space-lg` | 32px |
| `--space-xl` | 64px |
| `--space-2xl` | 128px |
| `--space-3xl` | 192px |

- `--max-width`: `1200px` (container max-width)
- `--section-padding`: `clamp(6rem, 12vw, 12rem)` (verticaal — luchtig)
- Container padding-inline: `clamp(1.5rem, 4vw, 3rem)`

---

## Radii & shadows

### Radii (minimaal — architectural)

```css
--radius-sm: 2px;
--radius-md: 4px;
--radius-lg: 8px;
```

### Shadows (warm-getint via Mahogany)

```css
--shadow-sm: 0 1px 2px rgba(88, 71, 56, 0.06);
--shadow-md: 0 4px 16px rgba(88, 71, 56, 0.08);
--shadow-lg: 0 16px 48px rgba(88, 71, 56, 0.12);
```

---

## Motion

- **Duration:** `400ms` (default, subtiel/statig)
- **Easing:** `cubic-bezier(0.22, 1, 0.36, 1)`
- **Standaard-patronen:**
  - `.fade-up` — opacity 0→1, `translateY(24px)` → `0`, via IntersectionObserver-class `.is-visible`
  - Link hover → `color: var(--accent)`
- **Reduced motion:** `prefers-reduced-motion: reduce` zet alle transitions uit en toont `.fade-up` elementen direct

---

## Responsive breakpoints

```css
/* Tablet */  @media (max-width: 960px) { }
/* Mobile */  @media (max-width: 640px) { }
```

---

## Fonts — technische notes

- `TAN-Nimbus.woff2` + `.woff` in `public/fonts/` — display-only (headings)
- `Quicksand-*.ttf` in `public/fonts/` — body, 5 weights
- `<link rel="preload">` op TAN Nimbus + Quicksand Regular in `<head>` voor no-FOUT
- `font-display: swap` overal — voorkomt invisible text tijdens load

---

## Pagina-secties (kern)

1. Hero — Tan Nimbus h1 + Quicksand body, Vanilla bg
2. Propositie / Our Story — alternating Vanilla / Sand
3. Portfolio-grid / cases — 3-col op desktop, 1-col mobile
4. Contrast-band — Mountain bg (zoals SEREIN-ref)
5. Our Philosophy — Sand bg, asymmetrische layout
6. Footer — category-labels in eyebrow-style, kleine navigatie

---

## Brand mark (logo)

Bestand: `public/assets/logo.png` (1500×1500 transparant PNG, stacked "Studio Bayu" in display-serif).

**Kleuring**: het logo wordt in HTML gerenderd via een `.logo-mark`-span die `mask-image` gebruikt — zo kan de kleur via tokens worden ingesteld:

```html
<span class="logo-mark logo-mark--md" role="img" aria-label="Studio Bayu"></span>
```

| Variant | Size | Gebruik |
|---|---|---|
| `.logo-mark--sm` | 48px | Header |
| `.logo-mark--md` | 96–140px (clamp) | Hero, footer |
| `.logo-mark--lg` | 160–240px (clamp) | Grote brand-momenten |

**Kleur**: default `var(--fg)` (Mahogany) op light backgrounds; binnen `.band--deep` wordt automatisch `var(--fg-inverse)` (Vanilla) toegepast. Override met `.logo-mark--accent` voor Tobacco.

---

## Implementatie-import

Elke pagina (of shared layout) moet beginnen met:

```astro
---
import '../styles/globals.css';
---
```

Alle tokens zijn daarna beschikbaar als `var(--token-name)`.
