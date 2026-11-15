# Site audit

Static site for IDEALL Impact gUG. Issues are ordered. Each one has a mitigation.

Constraints for whoever picks this up: GitHub Pages publishes `main` with Jekyll. Pages settings cannot be changed. Do not add a publish workflow. Do not add `.nojekyll`. `_config.yml` excludes `README.md`. This file stays in `.github/` so the site does not publish it.

## 1. The domain does not serve this site

`ideall-impact.org` and `www.ideall-impact.org` should serve this repository. They still serve the Squarespace placeholder. `CNAME` already contains `ideall-impact.org`.

Mitigation: at the DNS host, point the apex at GitHub Pages (`185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`) and point `www` at `ideall-impact-gug.github.io`. Remove the Squarespace records. Confirm the next Pages build keeps the custom domain from `CNAME`.

## 2. Legal pages disagree

The homepage legal popup and `impressum.html` / `datenschutz.html` do not say the same thing.

- Popup: HRB 279296 B, Amtsgericht Charlottenburg (Berlin). Impressum: HRB “wird nachgereicht”. Use the number already on the homepage. It matches the public register.
- Impressum and Datenschutz write the city as `13599 Берлін`. On the German pages, use `13599 Berlin`.
- The contact block says only “Berlin” and omits the phone already printed on the Impressum, +49 174 88 15828.
- Footer “Recht” opens the popup. Link Impressum and Datenschutz to the two real pages and drop the popup, so there is one legal text.
- The popup and the privacy page say the site stores a cookie consent. The site sets no cookies. Say that.
- Impressum cites § 55 Abs. 2 RStV. Use § 18 Abs. 2 MStV.
- Footer year is 2025. Use the current year.

Mitigation: one legal source, the two HTML pages, with the corrections above. Do not invent an IBAN (the page says it will be added) or a street. A commercial directory lists Gartenfelderstraße 132d, 13599 Berlin, and the register extract redacts the street. Confirm the street with the client before printing it.

## 3. Logo and SDG images are missing

`index.html` loads `assets/brand/IDEALL_Impact_logo.png` and eight files `assets/un/SDG_01.png`, `SDG_04.png`, `SDG_05.png`, `SDG_08.png`, `SDG_09.png`, `SDG_10.png`, `SDG_16.png`, `SDG_17.png`. Those files are not in the repo, so the first screen is broken images.

Mitigation: add the logo from the client and the SDG images beside it. Until the logo file exists, use a text wordmark so the header does not show a broken image.

## 4. Language switch is unreliable

DE, EN, and UK are several scripts that update the page on timers. The controls are links to `#de`, `#en`, and `#uk`, so they replace the section links. The legal popup stays German, the SDG captions stay English, and the choice is forgotten on reload.

Mitigation: one dictionary and real buttons. Persist the choice. Translate every visible string, including donation, about, footer, and SDG captions.

## 5. Impressum stylesheet is invalid

`impressum.html` writes CSS with doubled braces (`body{{ ... }}`), so the page is unstyled. `datenschutz.html` is fine.

Mitigation: use single braces.

## 6. Favicon link is wrong

`favicon.svg` is at the repo root. The homepage does not link it. The legal pages link `assets/favicon.svg`, which is not there.

Mitigation: point every page at `favicon.svg`.

## 7. Sharing and search metadata is missing

No meta description, no canonical link, no Open Graph tags, no `h1`. `og-image.svg` is unused. Facebook and LinkedIn want a PNG or JPG preview.

Mitigation: add a German description, a canonical URL of `https://ideall-impact.org/`, Open Graph tags, and an `h1`. Add a PNG or JPG preview when one exists. `robots.txt` and `sitemap.xml` already use that domain.
