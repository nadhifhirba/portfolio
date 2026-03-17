# NHADesign Portfolio V5C

Static HTML portfolio for Nadhif Hirba (NHADesign). Single-page, no build step required.

## Structure
```
index.html      — Full portfolio (all-in-one: HTML + CSS + JS)
images/         — Project images in WebP + JPEG fallback format
vercel.json     — Security headers + cache rules for Vercel deployment
```

## Key Technical Decisions
- **No Three.js** — Aurora shaders run on raw WebGL (~2KB vs ~600KB). Same GLSL fragment shader.
- **GSAP deferred** — Loaded with `defer` + initialized in `DOMContentLoaded` listener.
- **Fonts non-blocking** — Google Fonts loaded with `media="print" onload` pattern.
- **Images WebP** — All local images in WebP with JPEG fallback via CSS `image-set()`.
- **SRI hashes** — GSAP CDN scripts have `integrity` attributes.
- **Prefers-reduced-motion** — Animations disabled, GSAP skipped, canvases hidden.

## Lighthouse Scores (last run: 2026-03-16)
- Performance: 100
- Accessibility: 100
- Best Practices: 100
- SEO: 100

## Deployment
```bash
vercel --prod
```
Uses free Vercel tier. No env vars needed.

## Editing Content
All content is in `index.html`:
- Work cards: search for `class="wcard"`
- Built section: search for `class="bent"`
- Media section: search for `class="ment"`
- Statement: search for `class="stmt"`

## Adding Images
1. Copy image to `images/`
2. Convert: `cwebp -q 80 image.jpg -o image.webp`
3. Reference in HTML: `style="background-image:image-set(url(images/x.webp) type('image/webp'),url(images/x.jpg) type('image/jpeg'))"`
