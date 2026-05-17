# collinvaness.com — Author Site

Static HTML / CSS site for **Collin Vaness**, hosted on GitHub Pages.
Built to the visual system defined in *Author Brand Guide v1.0* (one folder up).

## What's in this repo

```
website/
├── index.html              Home — hero, six-series grid, about, newsletter
├── books.html              All series listed
├── about.html              Full bio + brand pillars
├── newsletter.html         Newsletter signup page
├── press.html              Press kit — bios, downloads, contact
├── contact.html            Email contacts by topic
├── 404.html                Branded error page
├── series/                 One page per series
│   ├── ruined-sky.html
│   ├── vanguard-protocol.html
│   ├── orbital-mandate.html
│   ├── iron-revenants.html
│   ├── silent-threshold.html
│   └── nothing-to-declare.html
├── css/styles.css          Single stylesheet — design tokens + components
├── assets/
│   ├── wordmark.svg        Primary wordmark
│   ├── wordmark-light.svg  Wordmark on dark backgrounds
│   ├── wordmark-mono.svg   Single-color wordmark
│   ├── shortmark.svg       Slash + V short mark
│   ├── shortmark-dark.svg  Short mark on dark
│   ├── favicon.ico         Favicon (multi-size)
│   ├── favicon-32.png      Favicon @ 32px
│   ├── favicon-180.png     Apple touch icon
│   ├── favicon-512.png     PWA / large icon
│   ├── og-image.png        1200×630 Open Graph / Twitter card image
│   ├── og-image.svg        Source for the OG image
│   └── covers/             Placeholder series covers (replace as real covers ship)
├── CNAME                   Custom domain pointer
├── .nojekyll               Tells GitHub Pages not to run Jekyll
├── robots.txt              Allow all + sitemap reference
└── sitemap.xml             Search engine sitemap
```

## Publishing to GitHub Pages

### One-time setup

1. **Create a new public repository** on GitHub. Two common patterns:
   - **Repo named `collinvaness.github.io`** → site lives at `https://collinvaness.github.io`
   - **Any other repo name + a custom domain** → recommended for `collinvaness.com`
2. From this `/website/` folder:
   ```bash
   git init
   git add .
   git commit -m "Initial site: brand v1.0"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<repo>.git
   git push -u origin main
   ```
3. In the repo's **Settings → Pages**, set:
   - **Source:** Deploy from a branch
   - **Branch:** `main` / `(root)`
4. Wait 30–60 seconds. The site is live.

### Custom domain (collinvaness.com)

1. Buy the domain (Cloudflare, Namecheap, Google Domains, etc.).
2. At your DNS provider, create:
   ```
   A     @     185.199.108.153
   A     @     185.199.109.153
   A     @     185.199.110.153
   A     @     185.199.111.153
   CNAME www   <your-username>.github.io.
   ```
3. The `CNAME` file in this repo already points at `collinvaness.com`. Edit it if you use a different domain.
4. In **Settings → Pages**, enter the custom domain. Enable **Enforce HTTPS** once the certificate is issued (a few minutes).

## Updating the site

The site is static HTML — open any file in a text editor, change it, push.

### Common updates

| What you want to do | Where to do it |
| --- | --- |
| Update a bio | `about.html`, `press.html`, and the `<meta>` tags on `index.html` |
| Add a new book | New `<article class="book-detail">` block on the relevant series page |
| Swap a placeholder cover | Replace the SVG in `assets/covers/` (keep the same filename) |
| Wire up newsletter | Replace the `<form action="#">` in `index.html` and `newsletter.html` with your provider's form action URL |
| Add Amazon / Goodreads links | Replace the `href="#"` placeholders in every footer |

### Preview locally

```bash
cd website/
python3 -m http.server 8080
# Open http://localhost:8080
```

Or use any static-file server you prefer (live-server, http-server, caddy, etc.).

## Newsletter integration

The signup forms in `index.html` and `newsletter.html` are markup-only. To make them functional:

- **Substack:** copy the embed code from your Substack settings into the `<form>` block.
- **Buttondown:** form action = `https://buttondown.email/api/emails/embed-subscribe/<your-username>`
- **ConvertKit:** paste the JS embed code in place of the form.
- **Mailchimp:** form action = the long URL from Mailchimp's "embedded forms" generator.

Each provider has a slightly different `name` attribute for the email field — check their docs.

## Style and content rules

The visual system, color palette, typography, voice, and application rules all live in:

> `/Author Website/Collin_Vaness_Author_Brand_Guide_v1.0.docx`

When making changes, the brand guide is the source of truth — update the doc first, then the site.

## License

Source code: MIT (do what you want).
Content (text, cover art, bios, brand assets): © 2026 Collin Vaness, all rights reserved.
