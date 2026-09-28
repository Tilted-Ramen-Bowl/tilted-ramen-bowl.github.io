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
| `marcus.jpeg`, `marcus-480.jpg` | Partner photo: original and a 480 px copy used on the page |
| `og-image.jpg`, `og-image.html` | Social-media preview image (2400x1260) and the HTML layout it is rendered from |
| `CNAME` | Custom domain for GitHub Pages (`lantern.tax`) |
| `.nojekyll` | Tells GitHub Pages to serve files as-is |
| `robots.txt`, `sitemap.xml` | Search engine hints |

## Editing

Open `index.html` in any editor. Copy lives directly in the HTML. Colours, fonts and spacing are
CSS custom properties in the `:root` block at the top of `styles.css`.

To change the partner photo, replace `marcus.jpeg` and regenerate the 480 px copy:

```sh
sips -Z 480 -s format jpeg -s formatOptions 82 marcus.jpeg --out marcus-480.jpg
```

## Regenerating the social preview image

`og-image.html` is a 1200x630 layout. Render it at 2x and convert to a JPEG under 300 KB (WhatsApp's limit):

```sh
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless=new --hide-scrollbars \
  --window-size=1200,630 --force-device-scale-factor=2 --screenshot=og-image.png "file://$PWD/og-image.html"
sips -s format jpeg -s formatOptions 82 og-image.png --out og-image.jpg
```

Chat apps cache previews. After changing the image, share the link with a query string
(for example `https://lantern.tax/?v=2`) to force a fresh preview, or use Facebook's Sharing Debugger.

## Local preview

```sh
python3 -m http.server 8000
```

Then open http://localhost:8000. A local server is needed for `404.html`, which uses absolute paths.

## Deployment

The site is served from the `main` branch root of this repository by GitHub Pages.
Pushing to `main` publishes.

## DNS for lantern.tax

The Pages custom domain is the apex `lantern.tax`. `www.lantern.tax` redirects to it once both
records below resolve to GitHub. At the DNS provider for `lantern.tax`, set:

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
