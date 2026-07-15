# Benefinding — static site

Static, front-end-only duplicate of the usaassistance.org design, rebranded to **Benefinding**.
No backend: no lead capture, no analytics, no pixels, no ClickVault. Pure HTML/CSS + a few lines
of vanilla JS for the form, the demographics quiz, and the disclaimer toggle.

**Live:** https://bitcoin4eva.github.io/moneyflow/

## Pages

| Page | Path |
|---|---|
| Homepage (hero, tiles, lead form) | `index.html` |
| Eligibility profile (quiz) | `flow/1/demographics/` |
| Welcome / matched | `flow/1/welcome/` |
| Offer: education grant | `flow/1/edu-smart-ua/` |
| Offer: Day1 Labs clinical trials | `flow/1/day1-labs-clinical-trials/` |
| Offer: ActiveTrial clinical trials | `flow/1/active-trial-clinical-trials/` |
| Offer: Benefinds | `flow/1/benefinds/` |
| Offer: Mutual of Omaha reverse mortgage | `flow/1/mutual-of-omaha-reverse-mortgage/` |
| Offer: product review jobs | `flow/1/product-review-jobs/` |
| Complete | `flow/1/complete/` |

Flow order: demographics → welcome → edu-smart-ua → day1-labs → active-trial → benefinds →
mutual-of-omaha → product-review-jobs → complete.

## How it behaves without a backend

- Homepage lead form: validates client-side, shows the thank-you card, then continues into
  `flow/1/demographics/`. **No data is sent or stored anywhere.**
- Offer "Yes" buttons currently advance to the next step, same as "No thanks".

## Re-pointing the Yes buttons at real offers

Every Yes CTA keeps the original tracking link in a `data-offer-url` attribute, e.g.:

```html
<a href="../mutual-of-omaha-reverse-mortgage/"
   data-offer-url="https://go.boringserver.net/click/69910149a1e2eaf72ff83c47" ...>
```

To make a Yes button go to a live offer, copy the `data-offer-url` value (or any new URL)
into the `href` and add back `target="_blank" rel="noopener"`.

## Branding

- Logo: `assets/logo.svg` (404×144 — same box as the original, swap in place)
- Favicon: `assets/favicon.svg`
- Brand color: `--brand-primary: #1e3054` set on the `<html>` tag of every page
