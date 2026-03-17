# NHADesign Portfolio v5

Static single-file portfolio for **Nadhif Hirba** (NHADesign). No build step, no dependencies — just one HTML file, images, and a Vercel config.

Live: [nhadesign.com](https://nhadesign.vercel.app)

## Structure

```
index.html       — Full portfolio (HTML + CSS + JS, all-in-one)
images/          — Project images (WebP + JPEG fallback)
vercel.json      — Security headers + cache rules
CLAUDE.md        — AI agent context (architecture, editing guide)
```

## Local dev

Open `index.html` directly in a browser — no server needed.

Or serve locally with:

```bash
npm run dev
```

## Deploy

```bash
npm run deploy
```

Requires [Vercel CLI](https://vercel.com/docs/cli) and a linked project (`vercel link`).

## Adding images

1. Copy source image to `images/`
2. Resize to max 900px: `sips -Z 900 image.png --out image.png`
3. Convert to WebP: `cwebp -q 80 image.jpg -o image.webp`
4. Reference in HTML: `data-bg="image-set(url(images/x.webp) type('image/webp'),url(images/x.jpg) type('image/jpeg'))"`

## Tech notes

- **No Three.js** — Aurora runs on raw WebGL (~2KB vs ~600KB)
- **No framework** — Vanilla JS, no bundler, no node_modules
- **Images lazy-loaded** — Work card backgrounds via IntersectionObserver
- **Performance** — Lighthouse 100/100/100/100 (A/BP/SEO), ~90+ Performance
