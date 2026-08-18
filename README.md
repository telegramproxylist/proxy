# Telegram Proxy Guide

A 5-page static site (pure HTML/CSS/JS, no build step, no frameworks) covering
Telegram's SOCKS5 and MTProto proxy options, meant to be hosted on GitHub
Pages and linked out to a main site.

## Pages

| File                        | Purpose                                   |
|------------------------------|--------------------------------------------|
| `index.html`                 | Homepage / blog index                      |
| `mtproto-proxy-guide.html`    | Blog post — MTProto proxy explainer        |
| `socks5-proxy-guide.html`     | Blog post — SOCKS5 proxy setup guide       |
| `socks5-vs-mtproto.html`      | Blog post — comparison article             |
| `about.html`                  | About / disclaimer page                    |

Every page links out to `https://telegramproxies.com` (nav bar, footer, and
inline in the article body) with `rel="noopener"` and UTM tags per link
location, so you can see in analytics which page/section sends the clicks.

## Deploy on GitHub Pages

1. Create a new **public** GitHub repo, e.g. `telegram-proxy-guide`.
2. Push these files to the repo root (don't nest them in a subfolder unless
   you update the paths):
   ```bash
   git init
   git add .
   git commit -m "Initial site"
   git branch -M main
   git remote add origin https://github.com/YOUR-USERNAME/telegram-proxy-guide.git
   git push -u origin main
   ```
3. On GitHub: **Settings → Pages → Build and deployment → Source → Deploy
   from a branch**, pick `main` and `/ (root)`, then **Save**.
4. Your site will be live at:
   `https://YOUR-USERNAME.github.io/telegram-proxy-guide/`

### Before/after you publish

- Find-and-replace `YOUR-USERNAME.github.io/telegram-proxy-guide` in every
  `.html` file (canonical + `og:url` tags), plus `robots.txt` and
  `sitemap.xml`, with your actual GitHub Pages URL — or your custom domain if
  you attach one.
- Optional custom domain: add a `CNAME` file to the repo root containing just
  your domain (e.g. `proxyguide.example.com`), then point a `CNAME` DNS
  record at `YOUR-USERNAME.github.io`. GitHub's Pages docs walk through the
  exact DNS records: https://docs.github.com/pages/configuring-a-custom-domain-for-your-github-pages-site
- Submit the sitemap in Google Search Console once the domain is verified,
  so indexing doesn't rely on crawl discovery alone.

## A note on the link-building intent

Using a GitHub Pages microsite mainly to place outbound links to a main
domain is a form of what Google's Search Essentials calls a "link scheme,"
and sites built primarily for that purpose can be devalued or penalized if
identified — see https://developers.google.com/search/docs/essentials/spam-policies#link-spam.
The content on this site is written to stand on its own regardless (it's a
genuine explainer, not link-farm filler), which is the safer version of this
approach, but worth knowing going in.

## Local preview

No build step needed — open `index.html` directly in a browser, or serve it
locally:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Structure

Flat — no subfolders, just files:

```
telegram-proxy-guide/
├── index.html
├── about.html
├── mtproto-proxy-guide.html
├── socks5-proxy-guide.html
├── socks5-vs-mtproto.html
├── style.css
├── script.js
├── favicon.svg
├── robots.txt
├── sitemap.xml
└── README.md
```
