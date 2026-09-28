# Lantern Taxes — lantern.tax

Static landing page for Lantern Taxes, a Singapore tax advisory firm for venture-backed startups
and their employees. Plain HTML and CSS, no build step, hosted on GitHub Pages.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The landing page |
| `styles.css` | All styling (design tokens at the top of the file) |
| `404.html` | Custom not-found page |
| `favicon.svg` | Lantern favicon |
| `CNAME` | Custom domain for GitHub Pages (`lantern.tax`) |
| `.nojekyll` | Tells GitHub Pages to serve files as-is |
| `robots.txt`, `sitemap.xml` | Search engine hints |

## Editing

Open `index.html` in any editor. Copy lives directly in the HTML. Colours, fonts and spacing are
CSS custom properties in the `:root` block at the top of `styles.css`.

To add a photo of Marcus, drop an image into the repo and replace the `portrait-initials` block in
the About section with:

```html
<img class="portrait" src="marcus-koh.jpg" alt="Marcus Koh">
```

## Local preview

```sh
python3 -m http.server 8000
```

Then open http://localhost:8000. A local server is needed for `404.html`, which uses absolute paths.

## Deployment

The site is served from the `main` branch root of this repository by GitHub Pages.
Pushing to `main` publishes.

## DNS for lantern.tax

At the DNS provider for `lantern.tax`, set:

| Type | Name | Value |
| --- | --- | --- |
| A | `@` | `185.199.108.153` |
| A | `@` | `185.199.109.153` |
| A | `@` | `185.199.110.153` |
| A | `@` | `185.199.111.153` |
| AAAA | `@` | `2606:50c0:8000::153` |
| AAAA | `@` | `2606:50c0:8001::153` |
| AAAA | `@` | `2606:50c0:8002::153` |
| AAAA | `@` | `2606:50c0:8003::153` |
| CNAME | `www` | `tilted-ramen-bowl.github.io` |

Once DNS resolves, enable **Enforce HTTPS** in the repository's Pages settings.
