# studio-bayu — Claude Context & Gedragsregels

## Raadpleeg altijd eerst

- **Design & techniek:** Lees `DESIGN-SYSTEM.md` vóór elke visuele of technische aanpassing.
- **Homepage context:** `src/pages/index.astro` is de hele site (single-page layout met anchor-navigatie). Alle secties hebben ID's: `#home`, `#introductie`, `#werkwijze`, `#expertise`, `#voor-wie`, `#projecten`, `#ervaringen`, `#contact`.

---

## Over dit project

- **Projectnaam:** studio-bayu
- **Domein:** studiobayu.com (nog niet gekoppeld — momenteel via `studio-bayu.vercel.app`)
- **Eigenaar:** Lize van den Heuvel — project- en operations specialist
- **Type site:** Portfolio (single-page marketing + services)
- **Talen:** Single-language (NL)
- **Live:** https://studio-bayu.vercel.app
- **Edit (alleen Lize):** https://studio-bayu.vercel.app/?edit=1
- **GitHub:** https://github.com/weadapt-robin/studio-bayu

---

## Tech Stack

- **Framework:** Astro 5
- **Deploy:** Vercel via GitHub `main` branch (auto-deploy op push)
- **Node:** ≥20
- **Fonts:** self-hosted TAN Nimbus (`public/fonts/TAN-Nimbus.woff2`) + Quicksand 5 weights (`.ttf`)
- **Texture:** `public/assets/paper-texture.jpg` (384KB JPG, via `.band::before` overlay)
- **Logo:** `public/assets/logo.png` (1500×1500 transparent, via mask-image)

---

## Homepage structuur (alternerende band-kleuren, 3-cyclus Light → Warm → Deep)

1. Hero (`#home`) — `band--light` (Vanilla) — gecentreerde copy + 2 CTAs
2. Introductie (`#introductie`) — `band--alt` (Warm-cream) — Lize's intro + over Studio Bayu
3. Werkwijze (`#werkwijze`) — `band--deep` (Mountain) — 3 pijlers (Heldere structuren / Sterke aansturing / Voorspelbare uitvoering)
4. Expertise (`#expertise`) — `band--light` — 3 service-cards met `<details>` accordions:
   - `#expertise-projectmanagement`
   - `#expertise-operations`
   - `#expertise-events`
5. Voor wie (`#voor-wie`) — `band--alt` — bullet-lijst
6. Projecten (`#projecten`) — `band--deep` — horizontal scroll carousel (5 placeholder cases, swipebaar met pijltjes)
7. Ervaringen (`#ervaringen`) — `band--light` — quote-rotator (7 quotes, auto-rotate 5.5s + manual pijltjes)
8. Contact (`#contact`) — `band--alt` — mailto-CTAs naar `lize@studiobayu.com`

Strikte regel: **nooit twee opeenvolgende bands dezelfde kleur**. Als je een sectie toevoegt, herverdeel de classes.

---

## Visuele CMS-inspector (op `?edit=1`)

De site heeft een ingebouwde live style-editor (zie `src/components/Inspector.astro`). Gebruik `/?edit=1` om een rechter zij-paneel te openen met:

- **Element-tab**: klik op een element → Typography / Size / Box controls
- **Tokens-tab**: alle CSS custom properties (kleuren, fonts, frame-metrics, grain-intensity)
- **Reset element / Reset alles**
- **Export CSS** — clipboard met plak-klare CSS

**Persistentie**: localStorage (browser-local, per-device). Andere bezoekers zien de originele site.

Als Lize terugkomt met wijzigingen uit het paneel, kan ze:
1. De **Export CSS** output plakken in chat → ik bepaal of het naar `globals.css` (tokens) of `index.astro` (per-element overrides) hoort
2. Of gewoon in de browser blijven tweaken; wijzigingen blijven staan

**Upgrade-pad** (indien gevraagd): Vercel KV + Publish-knop zodat wijzigingen live gaan voor alle bezoekers zonder code-aanpassing.

---

## Copy-regels

- Concrete getallen altijd. Nooit "bespaar tijd" maar "8 uur per week terug".
- Geen buzzwords: "revolutionair", "game-changer", "holistische aanpak", "synergieën".
- Geen em-dashes (—) in copy. Gebruik een punt, komma of nieuwe zin.
- Actieve werkwoorden. Korte zinnen.
- **Uitzondering**: copy die door Lize zelf wordt aangeleverd, exact overnemen (ook als er em-dashes in staan). De regels gelden alleen voor nieuwe copy die Claude schrijft.

---

## Placeholders die nog vervangen moeten

- **Projecten (`#projecten`)**: 5 cards met `[Project titel]` en `[Placeholder beschrijving]` — vervangen zodra cases klaar zijn
- **Ervaringen (`#ervaringen`)**: quote 1-3 zijn echt (van Lize aangeleverd zonder namen); quote 4-7 zijn `[Placeholder quote N]` — vervangen zodra testimonials + namen/bedrijven binnen zijn
- **Portret-fotografie**: `.placeholder--portrait` divs in Intro en Voor-wie — vervangen door echte foto's
- **Pijler-afbeeldingen** (`#werkwijze`): 3x `.placeholder--square` — vervangen door echte visuals
- **Service-card afbeeldingen** (`#expertise`): 3x `.placeholder--portrait` — vervangen door echte visuals

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

### `/cms-inspector`
Voor (her)installatie of uitbreiding van de live style-editor (`?edit=1`). Al geïnstalleerd; roep alleen aan voor grotere uitbreidingen (bv. contenteditable text-editing, Vercel KV upgrade).

---

## SEO — verplicht bij elke nieuwe pagina

```html
<title>[Paginatitel] — Studio Bayu</title>
<meta name="description" content="...">
<link rel="canonical" href="https://studiobayu.com/[slug]">

<meta property="og:type" content="website">
<meta property="og:url" content="https://studiobayu.com/[slug]">
<meta property="og:title" content="[Paginatitel] — Studio Bayu">
<meta property="og:description" content="...">
<meta property="og:image" content="https://studiobayu.com/og-preview.png">
<meta property="og:image:width" content="1200">
<meta property="og:image:height" content="630">
<meta property="og:site_name" content="Studio Bayu">

<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="[Paginatitel] — Studio Bayu">
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

---

## Deploy-flow

Bij wijzigingen aan de code:

```bash
git add -A
git commit -m "korte beschrijving"
git push                        # triggert Vercel auto-deploy
vercel --prod --yes             # optioneel: forceer direct deploy zonder te wachten op webhook
```

Deploy-URL verifiëren met `curl -s -o /dev/null -w "%{http_code}" https://studio-bayu.vercel.app`.

---

## Openstaande TODO's (post-launch)

- Domein `studiobayu.com` DNS koppelen aan Vercel
- Echte OG-image (`public/og-preview.png` — nu placeholder)
- Echte favicon (`public/favicon.png`)
- Analytics (Plausible / GA4 / Meta Pixel — user-keuze)
- Legal: privacy, cookies, terms (afhankelijk van tracking-keuzes)
- Contactformulier of Calendly-embed (nu enkel mailto)
- Echte cases/projecten + echte ervaringen-quotes invullen
- Echte portret- en sectie-fotografie
- Upgrade `cms-inspector` → Vercel KV Publish-knop (indien Lize self-service CMS wil)
