# CLAUDE.md - ecopro-site

Volunteer project. Bilingual single-page brochure site for **Ecopro Training Centre - Kebun Abi**,
a sustainable farming training centre in Kampung Nesam, Kangar, Perlis.

## Stack

Plain HTML + CSS + a small vanilla JS block. Single file (`index.html`) plus `assets/`.
No framework, no build step, no package manager, no backend. Keep it that way.

## Hard rules

1. **Malay is the source content, English is the attribute.** Text sits between the tags in
   Bahasa Malaysia; the English translation goes in `data-en` on the same element. Never move
   Malay into an attribute. The page must render as a complete Malay site with JavaScript off.
2. **Never invent facts about ETC.** Every number, name, credential, collaborator and date on
   this page traces back to ETC's own copy. If a fact is not sourced, it does not go on the page.
   Unknown details get a `<span class="tbc">` tag, not a plausible guess.
3. **The logo needs a dark background.** "ECO" in the wordmark is white. Do not place
   `logo-ecopro.png` on the pale `--husk` section.
4. **No em dash** anywhere, including copy and comments. Hyphen, comma or colon.
5. **Draft banner stays until ETC signs off.** `.draftbar` is removed at launch, not before.
6. **Guard first paint.** The audience is on phones on rural Malaysian connections. Only the
   HTML, `farm-aerial.jpg` and `logo-ecopro.png` may load before the hero is complete, and the
   total stays near 320 KB. Any new photo below the fold gets `loading="lazy"`. Hero replacements
   get resized to 1280px and saved at JPEG quality 74 or lower; the dark gradient over the hero
   hides the difference. The favicon is `icon.png` and never a full logo file.

## Design tokens

Set as CSS custom properties at the top of `index.html`.

| Token | Value | Use |
|---|---|---|
| `--ink` | `#1E201A` | page background |
| `--charcoal` / `--charcoal-2` | `#2C2F28` / `#3A3D35` | alternating dark sections |
| `--leaf` | `#8EA822` | ETC brand green, buttons and rules |
| `--leaf-lift` | `#B4CE3A` | small green type on dark (contrast) |
| `--husk` | `#E4E2D3` | body text, and the pale "field manual" section |
| `--clay` | `#A8552F` | the cycle diagram, and `.tbc` confirm tags |

Type: Barlow Condensed (display), Newsreader (body), IBM Plex Mono (labels and data).

## The cycle diagram

The signature element in `#kitaran`. It is a real closed nutrient loop, which is why the
numbering 01-06 is honest rather than decorative: waste -> compost -> vermicompost -> BSFL ->
Azolla -> catfish and rice -> back to waste. This is Dr. Hakimi's actual K2K research subject.

Desktop places the six nodes around an SVG circle by absolute percentage. Mobile collapses to a
vertical dashed chain with a "kembali ke 01" chip. If you edit node positions, edit both.

## Ownership

ETC owns the domain and hosting account, not Taufiq. Any hosting suggestion that leaves Taufiq
as the permanent unpaid webmaster, or puts the site on his Contabo box, is the wrong answer.

## Screenshot gotcha

Sections use `vh`-based padding, so a very tall headless window inflates the spacing wildly and
makes full-page screenshots misleading. Check layout at a realistic viewport height.
