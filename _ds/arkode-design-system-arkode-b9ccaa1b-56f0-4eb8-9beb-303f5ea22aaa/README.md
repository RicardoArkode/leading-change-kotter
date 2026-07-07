# Arkode Design System — Mosaic v1

The official design system for **Arkode** — a consulting and implementation firm for mid-market companies (25–200 employees) in Mexico and the United States. Arkode implements **Odoo ERP and AI**, turning operational chaos into systems that run themselves.

**Mosaic** is the 2026 system: warm bone canvas, coral + navy, a pixel-art icon language, a generative mosaic motif, a structural hairline grid, and a grain texture that makes surfaces feel like material. Clean and editorial in the spirit of Mistral / Vercel / Apple — rendered entirely in Arkode's DNA.

> This is the canonical system. Everything new — sites, apps, decks, documents, social, email — goes through it. Link `styles.css` (or `kit/mosaic.css` inside the kit) and build from the kit.

## Index

Root
- `README.md` — this file (brand, content, visual foundations)
- `SKILL.md` — agent skill entrypoint
- `styles.css` — canonical entry stylesheet (imports `kit/mosaic.css`)
- `assets/` — brand marks & imagery
  - `arkode-complete.png` (wordmark, light bg) · `arkode-white.png` (wordmark, dark bg)
  - `arkode-icon.svg` (the “O” icon mark, navy + coral dot — **the canonical favicon**) · `arkode-icon-dark.svg` (white, for dark bg)
  - `team/` — team headshots (e.g. `rodrigo.jpg`)
  - `clients/` — client logos (Funeza, Marhnos, RGD Roofers, Torres Corzo, Connect, Rotoplas, Gayosso, Traxion, GT Logistics) for case studies, the trust marquee, proposal covers
  - `partners/` — partnership logos (Odoo; Anthropic / HubSpot / Metabase to come)

`kit/` — the system: foundation, engine, and every deliverable
- `mosaic.css` — **the foundation**: tokens, reset, type, buttons, scaffold, reveal, grain
- `pixel-option3.js` — pixel-art sprite engine (38 icons; two weights, recolorable, crisp at any size)
- `mosaic-canvas.js` — generative mosaic (animated coral/orange/navy tile field)
- `motion.js` — motion library (tag-stagger, hero-dissolve, scrollytelling, line-draw, donut, signal-pulse, data-mosaic, logo-sting, magnetic)
- `mosaic-reveal.js` — scroll reveal helper
- `image-slot.js`, `deck-stage.js` — drop-in starters (user image slots, slide deck shell)
- `assets/` — favicons + app icons generated from the real `arkode-icon.svg` mark (16/32/180/512 + coral), plus a copy of `arkode-icon.svg` / `arkode-icon-dark.svg`, `grain.svg`, `arkode-tokens.css`, `arkode-tokens.json`
- **Pages** — editable source `.html` files live directly in `kit/`; their self-contained `*-standalone.html` deliverables live in **`kit/share/`** (open/share these):
  - `Arkode-Design-System-Mosaic.html` — **the spec hub** (foundations, icons, components, data viz, slide templates, the full kit)
  - `Pixel-Icons.html` — icon set + the two weights (Inset 86% / Fine 70%) + usage
  - `Sales-Pitch-Deck-Master.html` — 14-slide navigable pitch deck
  - `Documents-Reports.html` — print-ready one-pager, case study, proposal cover, monthly report
  - `Acompanamiento-Post-Go-Live.html` — interactive proposal template (`[Cliente]` placeholders)
  - `Social-OG.html` — OG link card, LinkedIn square, announcement, quote, stat card
  - `Email-Signature.html` — newsletter shell + team signatures
  - `Photography-Art-Direction.html` — duotone treatments, mosaic crop, art-direction rules
  - `Motion-Scroll.html` — 7 reusable motion patterns, live
  - `Arkode-Favicon-App-Icon.html` — favicon / app icon showcase
  - `Tokens-Figma-Handoff.html` — token tables + downloadable `tokens.json` / `.css`

To preview the system, open `kit/share/Arkode-Design-System-Mosaic-standalone.html`.

**Working with files.** Edit the source `.html` in `kit/` (it pulls in shared `mosaic.css` + engine JS). To produce a shareable deliverable, bundle the source into `kit/share/<name>-standalone.html`. Source pages link to deliverables via `share/<name>-standalone.html`; the deliverables in `share/` link to each other by bare filename — so after re-bundling a source into `share/`, strip the `share/` prefix from any `*-standalone.html` links inside that output so siblings resolve.

---

## VISUAL FOUNDATIONS

### Color

All colors are CSS variables in `kit/mosaic.css`.

| Role | Token | Hex | Use |
|---|---|---|---|
| Canvas | `--canvas` | `#FAF8F3` | Default warm page background. |
| Bone | `--bone` | `#F4ECDE` | Alternate editorial section background. |
| Bone 2 | `--bone-2` | `#EFE6D6` | Wells, inset surfaces. |
| Ink / Navy | `--ink` | `#001C43` | Dark sections, primary text on light. |
| Ink soft | `--ink-soft` | `#33405E` | Strong body text. |
| Mute | `--mute` | `#6B7390` | Secondary text, captions. |
| Faint | `--faint` | `#9AA1B6` | Tertiary, mono micro-labels. |
| Line | `--line` | `#E4DECF` | Hairline borders, dividers. |
| Line 2 | `--line-2` | `#D7CFBC` | Stronger borders. |
| **Coral** | `--coral` | `#FF6C5D` | **The one functional accent per view.** Primary button, key gesture, the wordmark dot. |
| Coral deep | `--coral-deep` | `#E8503F` | Coral for text/hover (AA-safe). |
| Orange | `--orange` | `#FF8A3D` | Mosaic + illustration accent only. |
| Crimson | `--crimson` | `#C5362A` | Mosaic + negative/down deltas. |
| Blue | `--blue` | `#2A6FDB` | Mosaic + data series #2 / info. |
| Green | `--green` | `#1F8A5B` | Success, positive deltas, checks. |

**The one-coral rule.** Coral is the single functional accent in any UI view — if it's on the button, it's not on the headline. Orange / crimson / blue belong to the **generative mosaic and illustrations** only, never as a second UI accent. Scarcity keeps coral premium.

### Typography

Two families. Never more. **No Newsreader / serif italic** — Mosaic is sans + mono only.

- **Geist** (`--font`) — the workhorse. 400 body, 500 buttons/labels, 600 headings. Tracking tightens at size (`-0.045em` headings, `-0.05em` at display).
- **Geist Mono** (`--mono`) — eyebrows, numbered tags, capability labels, metadata. Uppercase, `0.1–0.16em` tracking.

Loaded via Google Fonts CDN in each page's `<head>`. Drop official `.woff2` in `fonts/` and add `@font-face` to `kit/mosaic.css` to self-host.

### Iconography — pixel sprites

The brand icon mark is the **“O” logo** (`assets/arkode-icon.svg`) — a navy ring with the coral dot biting the top-right; it is the favicon and app-icon source. For UI/illustration, the signature craft detail is the **pixel-art icon set**. `pixel-option3.js` renders **38 pixel-art icons** from data — each painted cell is a rounded square at one of **two weights**: `fine` (70% fill, the premium default) or `inset` (86% fill, for small/dense UI). Crisp at any size, recolorable with one attribute, zero image requests. Override with `data-weight="inset|fine"`; omit it and the engine auto-picks by size (≤ unit 3 → inset, ≥ 4 → fine). Full set + guidance: `Pixel-Icons.html`.

```html
<span data-px="arrowR" data-unit="3"></span>          <!-- inline -->
<span data-px="gear" data-unit="6" data-tint="#fff"></span>  <!-- sized + recolored -->
```

`data-unit` = pixel size (one number scales the whole icon). `data-tint` overrides color. Groups: **interface** (arrowR, arrowDownFull, plus, check, search, bell, gear, chat, user, bolt, target, mark), **industry** (brief, doc, database, factory, truck, cube, money, calendar, clock, mail, shield, bot, plug, cloud, code, globe), **data** (chartBar, chartLine, chartPie, trendUp, trendDown, dot, layers, squares). No emoji, ever. No unicode glyphs in body. The pixel `mark` is the favicon / app icon.

### Spacing & grid

4px base scale: `--space-1`…`--space-24` (4 / 8 / 12 / 16 / 24 / 32 / 48 / 64 / 96). Layout is a **6-column structural grid** with hairline dividers and small square corner ticks — the Mistral/Vercel margin system. `--maxw` 1180px, `--pad` `clamp(16px,4vw,56px)`.

### Radius, elevation, motion

- **Radius:** `--r-sm` 6px (badges/tags), `--r-md` 9px (buttons/inputs/rows), `--r-lg` 14px (cards/panels).
- **Elevation:** `--e1` hairline (resting), `--e2` soft 16px (hover/key), `--e3` deep 50px (modals/menus). Light, never heavy.
- **Motion:** one easing curve `--ease` `cubic-bezier(.22,.68,0,1)`; durations `--dur-fast` 120ms, `--dur-base` 200ms, `--dur-slow` 320ms. Fades + translates, no bounce. All patterns respect `prefers-reduced-motion`.

### Material — grain & mosaic

- **Grain:** add `class="grain"` to any dark or coral block. A subtle noise overlay (`assets/grain.svg`, `mix-blend:overlay`) makes the surface read as material, not flat. Apply to every ink/coral section.
- **Generative mosaic:** the animated coral/orange/crimson/navy/bone tile field (`mosaic-canvas.js`, `data-mz="<cols>"`). Used in heroes, section dividers, thumbnails. It can also **encode data** — light tiles proportional to a metric.
- **Circuit graphic:** pixel-icon nodes wired on a grid (coral = operations, navy = engineering), with signal-pulse dots traveling the wires.

### Surfaces

Default `--canvas`. Alternate sections `--bone`. Dark sections `--ink` (always with `grain`). No gradients on text, no decorative gradients on full sections, no stock photography — photography always takes a Mosaic treatment (see `Photography-Art-Direction.html`).

---

## CONTENT FUNDAMENTALS

### Tone
Direct, specific, practitioner. Every sentence earns its place. Arkode writes the way an operator talks after 10 implementations — calm, exact, confident without being loud.

### Pyramid Principle
Lead with the conclusion. Headline = the answer; body = the why. Never save the punchline.

### Numbers beat adjectives
"65% of a rep's time," not "a huge chunk." Every stat earns a cite or gets cut.

### Person & casing
"We" for Arkode, "you" for the client. Headlines in **sentence case**. Mono labels in **ALL CAPS**, short, numbered (`01 · MÉTODO`). Body in sentence case.

### Bilingual
Spanish artifacts for Mexico, English for the US — **never mixed in one composition, never machine-translated**. Numbers use English format in both (29%).

### Banned
The words *leverage, synergies, holistic, robust, transformative, paradigm, ecosystem*; "solutions" as filler; "world-class"; "next-gen". Gradients on text. Emoji in graphics. More than 2 font families. Stock photos. Corporate blue-gray.

### Voice samples
- ✅ "Implementamos Odoo en 12 semanas. Sin drama."
- ✅ "We replace the spreadsheet, not your team."
- ❌ "Leveraging our holistic, transformative methodology to unlock synergies."

---

## STARTING A NEW ARTIFACT

1. Link `styles.css` (or `kit/mosaic.css` from inside the kit). Load **Geist + Geist Mono** from Google Fonts, and `kit/pixel-option3.js` for icons.
2. Choose a background: `--canvas` (default), `--bone` (editorial), or `.sec.ink` + `.grain` (dark).
3. Open with the structural-grid convention: mono numbered eyebrow, logo, hairline rule.
4. One idea per section. One coral gesture per view (the one-coral rule).
5. Headline in Geist 600 sentence case; eyebrows + tags in Geist Mono uppercase; body in Geist 400.
6. Reach for the kit: don't rebuild a deck/doc/social card from scratch — copy the matching kit page and replace content.
7. Add grain to dark/coral surfaces; use the mosaic + circuit graphics for showpieces; keep motion to a few intentional moments.

## Caveats
- Fonts are Google-Fonts (Geist by Vercel, Geist Mono) loaded via CDN — drop official files in `fonts/` to self-host.
- Icons are a custom pixel sprite set (no external icon dependency).
- The interactive proposal (`Acompanamiento-Post-Go-Live.html`) is a **template**: replace `[Cliente]` / `[Año]` and the placeholder figures per client.
