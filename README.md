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
  farm-aerial.jpg   hero background (drone shot of the kebun), 1280px wide
  hakimi.jpg        Dr. Mahamad Hakimi
  ismail.jpg        Ismail Mahamad Hakimi
  sakiinah.jpg      Sakiinah binti Mahamad Hakimi
  logo-ecopro.png   ECOPRO wordmark (white "ECO", needs a dark background)
  icon.png          leaf mark cropped from the wordmark. Favicon and touch icon
  logo-lockup.png   round full lockup. Not loaded by the page, kept as ETC's archive copy
  og-card.jpg       1200x630 preview card shown when the link is shared on WhatsApp
```

## Page weight

Most visitors are on a phone on a rural Malaysian connection, so first paint is kept small.
Only three files load before the hero is complete: the HTML, `farm-aerial.jpg` and
`logo-ecopro.png`. The three team portraits are `loading="lazy"` and only fetch when the
visitor scrolls to them.

Current first paint is about 320 KB. If you replace the hero photo, resize it to 1280px wide
and save it at JPEG quality 74 or lower. The hero sits under a heavy dark gradient, so a
smaller file is not visible: dropping it from 1600px to 1280px changed the rendered page by
0.4 percent and nothing else.

Do not point the favicon at a full logo file. A logo with a ring of small text is an
unreadable smudge at 32 pixels, and the browser downloads it on every single page load.
`icon.png` exists for this.

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

## When ETC sends the missing details

Decided: the details come back to this repo and get committed here, rather than being handed
over as a file for someone to paste in. The four unconfirmed items are already tagged
`class="tbc"` in `index.html`, so filling them in is a four line edit plus a push. Keeping it
in one place means the Malay and the English cannot drift apart, and the pre-launch checklist
below stays the single source of truth for what is still outstanding.

Nothing supplied by ETC gets paraphrased or "tidied". An address, a phone number and an
opening time are facts. They go in exactly as given.

## Hosting

Static files, so any static host works.

Decided for launch: rebuild the site on **Cloudflare Pages under an account owned by ETC**,
then delete the GitHub Pages copy. Not a transfer of this GitHub repository.

The reasoning: ETC needs the domain, the DNS, the certificate and the hosting to sit behind
one login they control. Cloudflare covers all four for free apart from the domain itself,
which is roughly RM45 a year at cost through Cloudflare Registrar. Handing over a GitHub
repository instead would mean a farm training centre maintaining a developer account they
will never open again, and the volunteer who built it staying on as the permanent unpaid
webmaster. That is the failure mode this project is specifically trying to avoid.

Deploying is a drag and drop of this folder into Cloudflare Pages. No git, no build step, no
command line. Whoever holds the ETC account can do it.

One caveat on the domain. Cloudflare Registrar does not sell `.my` domains, so if ETC prefers
`kebunabi.my` over `kebunabi.com` the domain has to be bought from a MYNIC accredited
registrar and pointed at Cloudflare's nameservers. The hosting side is unchanged either way.

Once the Cloudflare copy is live and the domain resolves, delete the GitHub repository. Two
public copies of the same site competing in search results helps nobody.

## Content provenance

All copy, photography and the logo come from ETC's own Softr site at
`https://ecopro-my.softr.app/`. Two stock photographs that shipped with the Softr template
were discarded. The English text was drafted for this build and still needs ETC's sign-off.
No facts were invented: every figure on the page traces back to ETC's own words.
