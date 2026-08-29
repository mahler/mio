# Mio for Hugo

Mio is a simple Hugo theme that integrates the Bootstrap 5 CSS framework via CDN.

## Features

- Responsive Bootstrap 5 layout
- Basic navigation bar
- Stylish article and list pages
- Footer with copyright
- Easy to customize via parameters

## Installation

1. Clone this repository into your Hugo site's `themes` directory:

   ```bash
   git clone https://github.com/yourusername/mio.git themes/mio
   ```

2. Set the theme in your site's configuration file (`config.toml`, `config.yaml`, or `config.json`).

   Example `config.toml`:

   ```toml
   theme = "mio"
   title = "My Hugo Site"
   ```

## Customization

You can override the following parameters in your site config:

- `params.description`: Site description (used for meta tag).
- `params.customCSS`: Path to a custom CSS file (relative to site root) to load after Bootstrap.
- `params.googleAnalyticsID`: Optional Google Analytics 4 measurement ID, such as `G-XXXXXXXXXX`.
- `params.googleAdsenseID`: Optional Google AdSense publisher ID, such as `ca-pub-0000000000000000`.
- `params.social`: Optional footer links for common social sites.
- `params.footerLinks`: Optional custom footer links.

### Adding Custom CSS

To add custom CSS styling to your site:

1. Create a CSS file in your site's `static/` directory. For example: `static/css/custom.css`

2. Add your custom styles to the file:
   ```css
   /* static/css/custom.css */
   body {
     background-color: #f8f9fa;
   }
   
   .navbar-brand {
     font-weight: bold;
   }
   ```

3. Configure the `customCSS` parameter in your site's `config.toml`:
   ```toml
   [params]
     customCSS = "css/custom.css"
   ```

The custom CSS file will be loaded after Bootstrap, allowing you to override Bootstrap styles as needed.

Footer links are optional. Mio supports common social links plus custom links:

```toml
[params.social]
  twitter = "https://twitter.com/example"
  x = "https://x.com/example"
  facebook = "https://www.facebook.com/example"
  github = "https://github.com/example"
  instagram = "https://www.instagram.com/example"
  reddit = "https://www.reddit.com/user/example"
  linkedin = "https://www.linkedin.com/in/example"
  youtube = "https://www.youtube.com/@example"
  mastodon = "https://mastodon.social/@example"
  tiktok = "https://www.tiktok.com/@example"
  bluesky = "https://bsky.app/profile/example.bsky.social"

[[params.footerLinks]]
  name = "Newsletter"
  url = "https://example.com/newsletter"

[[params.footerLinks]]
  name = "Store"
  url = "https://example.com/store"
```


Categories are supported too. A post can belong to multiple categories:

```yaml
---
title: "Post with Categories"
categories:
  - Guides
  - Tutorials
---
```

Category pages are available at `/categories/` and `/categories/<category>/`.

Posts can define an optional `header_image` front matter value. The image is shown on the post page and in post lists:

```yaml
---
title: "Post with Image"
header_image: "images/example.jpg"
header_image_alt: "Description of the header image"
---
```

## Development

The theme uses Bootstrap 5 from the CDN. If you prefer to host Bootstrap locally, download the files and place them in `static/` and adjust the links in `layouts/_default/baseof.html`.

## Example Site

An example Hugo site is available in `exampleSite/` for local testing:

```bash
hugo server --source exampleSite --themesDir ../.. --theme mio
```

To build the sample without starting a server:

```bash
hugo --source exampleSite --themesDir ../.. --theme mio
```

## License

MIT

## Additional Templates

- `layouts/_default/archive.html` – Monthly archive page (create a page with `type: "archive"` or use as a section).
- `layouts/_default/taxonomy.html` – Tag (or taxonomy) overview page listing all tags with counts.
- `layouts/_default/term.html` – Individual tag page showing all posts tagged with that term.

To use the archive page, create an `archive.md` in your content root (or in a section) with front matter:

```markdown
---
title: "Archives"
type: "archive"
date: 2026-01-01
---
```

Then visit `/archives/` to see posts grouped by month.

Tag pages are automatically generated at `/tags/` (overview) and `/tags/<tag>/` (individual tag).

## Sitemap

Hugo generates `sitemap.xml` automatically for sites using Mio. Make sure your site has a real `baseURL` in its config:

```toml
baseURL = "https://example.com/"
```

Then build the site and visit `/sitemap.xml`.

## Google Services

Enable Google Analytics 4 or Google AdSense by setting the relevant params:

```toml
[params]
  googleAnalyticsID = "G-XXXXXXXXXX"
  googleAdsenseID = "ca-pub-0000000000000000"
```

Both are optional. If unset, Mio does not emit those scripts.

## Recent updates

- 2026-08-29: Restored `exampleSite` static assets into `static/` (added `static/css/demo.css` and `static/images/component-grid.svg`, `static/images/mio-workbench.svg`). Shortcodes in `layouts/shortcodes` were synced from the upstream repository.
