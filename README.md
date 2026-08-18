# Zhunming Ma · Photography Portfolio — Redesign

A complete, animation-rich redesign of your personal photo site, in the soft **"atelier / analog"** aesthetic you liked from the reference image (warm paper, painterly washes, film grain, elegant serif, a poetic tagline and an *Explore* entrance). It reuses your **exact 84 photos** across 2025 / 2024 / 2023.

Everything is in a single self-contained `index.html` (no build step).

---

## Preview it locally

Any static server works. From this folder:

```bash
python -m http.server 8000
# then open http://localhost:8000
```

Or just double-click `index.html` (some browsers block a few things on `file://`; a local server is best).

---

## What's inside

| Area | Details |
|------|---------|
| **Themes** | **Atelier** (warm light, default) ⇄ **Nocturne** (refined dark). Toggle top-right. Your original light/dark toggle is preserved. |
| **Languages** | **EN / 中文** toggle. Full bilingual UI + poetic tagline. |
| **Hero** | Cinematic preloader, handwritten signature, split-text serif tagline, magnetic *Explore* button, scroll cue. |
| **Gallery** | Matted "fine-art print" cards, masonry (3 → 2 → 1 columns), sticky year-timeline synced to scroll, year filters (All / 2025 / 2024 / 2023), hover captions. |
| **Lightbox** | Click any photo → fullscreen viewer with prev/next (arrows, ← → keys, swipe), caption, index, `Esc` to close. |
| **Motion** | GSAP + ScrollTrigger + Lenis smooth-scroll: staggered reveals, in-frame parallax, animated counters, marquee, drifting light-leaks, film grain. All respect `prefers-reduced-motion`. |
| **Responsive** | Verified from 375px phones to desktop; zero horizontal overflow; hamburger menu on mobile. |

Libraries load from CDN (GSAP, Lenis) and fonts from Google Fonts — all standard for a Vercel deploy.

---

## The photos

All 84 images are referenced by absolute URL from your current live site, e.g.
`https://zhunming-personal-photo-web.vercel.app/images/Abu Dhabi1.jpg`

So the gallery works **immediately, anywhere**, as long as your current deployment stays up.

**To make it fully self-contained** (recommended once you're happy):
1. Copy your repo's `public/images/` folder into this folder (so you have `./images/...`).
2. In `index.html`, change one line:
   ```js
   const BASE = "https://zhunming-personal-photo-web.vercel.app/images/";
   // →
   const BASE = "images/";
   ```

---

## Deploy — three options

**A. New Vercel project (safest — non-destructive)**
Drag this folder onto <https://vercel.com/new>, or run `npx vercel` inside it. You get a fresh URL to compare. When happy, move your domain over in the Vercel dashboard. Images load from the old domain until you self-host them (see above).

**B. Replace your current site**
Point the `personal-photo-web` Vercel project at this static `index.html` (add the images folder), or drop it into your repo's output. This swaps the React app for this static page.

**C. Keep your AI Studio / React pipeline**
Hand this `index.html` to the AI Studio assistant as the design spec and ask it to rebuild the React version to match. The data model (`RAW` in the script) mirrors your current `{title, location, file}` structure.

---

## Customize (edit `index.html`)

- **Email / socials** — search for `zhunmingm@gmail.com` and the `.socials` block; replace the Instagram / 小红书 `href="#"` placeholders with your real links.
- **Taglines & copy** — all text lives in the `I18N` object (`en` + `cn`). Edit `hero_l1` / `hero_l2`, `intro_text`, `about_*`, etc.
- **Default theme** — change `<html data-theme="atelier">` to `nocturne` for a dark-first site.
- **Photo titles / locations / order** — edit the `RAW` object (grouped by year).
- **Colors** — the palette lives in CSS custom properties under `html[data-theme="atelier"]` / `[data-theme="nocturne"]`.

---

*Built with the `ui-ux-pro-max` design system (Vintage Analog / editorial pattern) + GSAP motion.*
