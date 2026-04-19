# studio-bayu — Design System

Deze file is de single source of truth voor visuele en technische keuzes. Raadpleeg hem vóór elke UI-wijziging.

---

## Project

- **Naam:** studio-bayu
- **Type:** Portfolio
- **Framework:** Astro
- **Max breedte:** 1440px (pas aan indien gewenst)

---

## Kleuren

*Wordt ingevuld in Fase 4 van /website-quicklaunch.*

```css
:root {
  --bg: #;
  --fg: #;
  --card: #;
  --accent: #;
  --muted: #;
  --border: #;
}

[data-theme="dark"] {
  --bg: #;
  --fg: #;
  --card: #;
  --accent: #;
  --muted: #;
  --border: #;
}
```

---

## Typografie

*Wordt ingevuld in Fase 4 van /website-quicklaunch.*

```css
:root {
  --font-display: system-ui, sans-serif;
  --font-body: system-ui, sans-serif;
}

h1 { font-size: clamp(2rem, 5vw, 4rem); line-height: 1.1; font-weight: 700; }
h2 { font-size: clamp(1.5rem, 3.5vw, 2.5rem); line-height: 1.2; font-weight: 600; }
h3 { font-size: clamp(1.25rem, 2.5vw, 1.75rem); line-height: 1.3; font-weight: 600; }
p { font-size: 1rem; line-height: 1.6; }
small { font-size: 0.875rem; }
```

---

## Spacing

```css
:root {
  --space-xs: 0.5rem;
  --space-sm: 1rem;
  --space-md: 2rem;
  --space-lg: 4rem;
  --space-xl: 8rem;
}
```

Sectie-padding verticaal: `clamp(4rem, 8vw, 8rem)`.

---

## Radii & shadows

```css
:root {
  --radius-sm: 6px;
  --radius-md: 12px;
  --radius-lg: 24px;

  --shadow-sm: 0 1px 2px rgba(0,0,0,0.05);
  --shadow-md: 0 4px 12px rgba(0,0,0,0.08);
  --shadow-lg: 0 12px 32px rgba(0,0,0,0.12);
}
```

---

## Dark mode

Toggle via `data-theme` attribuut op `<html>`. Persist in `localStorage`:

```js
const saved = localStorage.getItem('theme');
if (saved) document.documentElement.setAttribute('data-theme', saved);
```

---

## Animaties

Default duration: `180ms`. Easing: `cubic-bezier(0.22, 1, 0.36, 1)`.

Standaard-patronen:
- **Fade-up on scroll** voor content-secties (IntersectionObserver + `translateY(20px) → 0`).
- **Hover-lift** op interactieve cards: `transform: translateY(-2px)` + grotere shadow.
- **Marquee** voor logo-tickers: `animation: marquee 30s linear infinite`.

---

## Responsive breakpoints

```css
/* Tablet */
@media (max-width: 960px) { }

/* Mobile */
@media (max-width: 640px) { }
```

---

## Visual direction

*Wordt ingevuld in Fase 5 van /website-quicklaunch.*

**Sleuteltermen**:

**Layout**:

**Animatie-taal**:

**Moodboard-refs**:

---

## Pagina-secties (kern)

1. Hero
2. Propositie
3. Features / diensten
4. Social proof
5. CTA
6. Footer

Portfolio-specifiek:
- case-grid (overzicht)
- case-detail (per project)
