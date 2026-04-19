# studio-bayu — Claude Context & Gedragsregels

## Raadpleeg altijd eerst

- **Design & techniek:** Lees `DESIGN-SYSTEM.md` vóór elke visuele of technische aanpassing.

---

## Over dit project

- **Projectnaam:** studio-bayu
- **Domein:** studiobayu.com
- **Type site:** Portfolio
- **Talen:** Single-language (NL)

---

## Tech Stack

- **Framework:** Astro
- **Deploy:** Vercel via GitHub
- **Node:** ≥20

---

## Copy-regels

- Concrete getallen altijd. Nooit "bespaar tijd" maar "8 uur per week terug".
- Geen buzzwords: "revolutionair", "game-changer", "holistische aanpak", "synergieën".
- Geen em-dashes (—) in copy. Gebruik een punt, komma of nieuwe zin.
- Actieve werkwoorden. Korte zinnen.

---

## Skills — wanneer raadplegen

### `/copywriting`
Voor elke copywriting-taak: nieuwe paginateksten, hero headlines, CTA's, meta-descriptions, blog-artikelen.

### `/frontend-design`
Voor frontend/design: nieuwe secties, visuele verbeteringen, animaties, responsive gedrag.

### `/ui-ux-pro-max`
Voor UX/UI beslissingen: kleuren, fonts, component-keuzes, accessibility-reviews.

### `/page-cro`
Voor conversie-optimalisatie van bestaande pagina's.

---

## SEO — verplicht bij elke nieuwe pagina

```html
<title>[Paginatitel] — studio-bayu</title>
<meta name="description" content="...">
<link rel="canonical" href="https://studiobayu.com/[slug]">

<meta property="og:type" content="website">
<meta property="og:url" content="https://studiobayu.com/[slug]">
<meta property="og:title" content="[Paginatitel] — studio-bayu">
<meta property="og:description" content="...">
<meta property="og:image" content="https://studiobayu.com/og-preview.png">
<meta property="og:image:width" content="1200">
<meta property="og:image:height" content="630">
<meta property="og:site_name" content="studio-bayu">

<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="[Paginatitel] — studio-bayu">
<meta name="twitter:description" content="...">
<meta name="twitter:image" content="https://studiobayu.com/og-preview.png">

<link rel="icon" href="/favicon.png">
```

**BreadcrumbList JSON-LD** (altijd toevoegen, voor `</head>`):
```html
<script type="application/ld+json">
{"@context":"https://schema.org","@type":"BreadcrumbList","itemListElement":[
  {"@type":"ListItem","position":1,"name":"Home","item":"https://studiobayu.com"},
  {"@type":"ListItem","position":2,"name":"[Paginanaam]","item":"https://studiobayu.com/[slug]"}
]}
</script>
```

---

## Sitemap — bijwerken na elke nieuwe pagina

Bestand: `public/sitemap.xml`

- Voeg de nieuwe URL toe met `<lastmod>` (publicatiedatum of vandaag)
- Geen `<lastmod>` weglaten — Google gebruikt dit voor crawlprioriteit
