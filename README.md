# Ecopro Training Centre - Kebun Abi

Bilingual (Bahasa Malaysia / English) single-page brochure site for Ecopro Training Centre,
a sustainable farming training centre in Kampung Nesam, Kangar, Perlis.

Volunteer project. The intended owner of the domain and hosting account is ETC, not Taufiq.

## What this is

One HTML file, one folder of images. No build step, no framework, no backend, no database.
Open `index.html` in a browser and it works.

```
index.html          the whole site
assets/
  farm-aerial.jpg   hero background (drone shot of the kebun)
  hakimi.jpg        Dr. Mahamad Hakimi
  ismail.jpg        Ismail Mahamad Hakimi
  sakiinah.jpg      Sakiinah binti Mahamad Hakimi
  logo-ecopro.png   ECOPRO wordmark (white "ECO", needs a dark background)
  logo-lockup.png   round full lockup, used as the favicon
  og-card.jpg       1200x630 preview card shown when the link is shared on WhatsApp
```

## Editing the text

Malay is the real content in the HTML. English lives in a `data-en` attribute on the same tag.

```html
<h2 data-en="One farm, one cycle.">Satu kebun, satu kitaran.</h2>
```

To change the Malay, edit between the tags. To change the English, edit inside `data-en`.
Both languages sit side by side so they cannot drift apart.

This ordering is deliberate: with JavaScript switched off or broken, the page still renders
as a complete Malay site. Search engines see real text, not empty tags.

## Preview locally

```bash
cd ~/Projects/ecopro-site
python3 -m http.server 8899
# open http://127.0.0.1:8899/
```

## Current preview

<https://taufiq0177.github.io/ecopro-site/> - temporary, hosted from this repo via GitHub
Pages. It is marked `noindex` and carries a draft banner. This link gets retired once ETC
attaches their own domain.

## Before it goes live

1. Delete the `<div class="draftbar">...</div>` element near the top of `<body>`.
2. Delete the `<meta name="robots" content="noindex, nofollow">` tag in `<head>`. Leaving it
   in means Google never lists the site at all.
3. Fill in the four items currently tagged `SAHKAN` / `PERLU` in the contact section:
   WhatsApp number, email, confirmed address, visiting hours.
4. Repoint `og:image` and `og:url` from the GitHub Pages address to the real domain
   (e.g. `https://kebunabi.com/assets/og-card.jpg`). They must be absolute URLs or the
   WhatsApp link preview breaks.

## Hosting

Static files. Any static host works. The recommendation is Cloudflare Pages on an account
owned by ETC, with the domain registered through Cloudflare Registrar at cost price, so the
whole thing is one login to hand over and roughly RM45 a year with no hosting fee.

## Content provenance

All copy, photography and the logo come from ETC's own Softr site at
`https://ecopro-my.softr.app/`. Two stock photographs that shipped with the Softr template
were discarded. The English text was drafted for this build and still needs ETC's sign-off.
No facts were invented: every figure on the page traces back to ETC's own words.
