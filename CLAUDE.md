# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Google Ads landing page for **Libet Service**, an industrial cleaning company in Santiago, Chile. The page is a single `index.html` file with all CSS and JS inline, designed for maximum lead generation via a GoHighLevel (GHL) embedded form.

- **Primary keyword:** "servicio de aseo industrial"
- **48 secondary keywords** across 8 clusters (see `keywords_libet_service.pdf`)
- **Live URL:** https://freddy-ztrata.github.io/landing-libet-service/
- **Company site:** https://libetservice.cl

## Architecture

Everything is in one file: `index.html` (~2600 lines). No build step, no frameworks, no dependencies.

- **CSS:** Inline `<style>` block. Uses CSS custom properties (`:root` vars), fluid typography with `clamp()`, Google Fonts (Sora + DM Sans).
- **JS:** Inline `<script>` at bottom. Vanilla JS only. Handles: scroll reveal (IntersectionObserver), counter animations, FAQ accordion, steps timeline progression, floating CTA.
- **Form:** GoHighLevel iframe (form ID: `yvCyhoYDwPSX38nb9D3h`, API: `api.hapee.ai`). Not HTML native.
- **Images:** Unsplash URLs with optimization params (`?w=600&q=80&auto=format`). Logo loaded from `libetservice.cl`.
- **Favicon:** `favicon.png` — "LS" monogram extracted from company logo (black on white).
- **Schema:** JSON-LD in `<head>` — LocalBusiness + Service + FAQPage.
- **Robots:** `noindex, nofollow` (this is an ads landing page, not meant for organic indexing).

## Deployment

Auto-deploys to GitHub Pages on every push to `main` via `.github/workflows/deploy.yml`.

```bash
git add index.html
git commit -m "description"
git push
# Deploys in ~1 minute
```

## Key Constraints

- **Single CTA = form.** Every button on the page scrolls to `#formulario`. No phone, no email, no WhatsApp CTAs.
- **No navigation links.** Zero external links. Logo is not clickable. This is a conversion-focused landing page.
- **Spanish only.** All copy in Latin American Spanish (Chilean context).
- **Images must show Latino/Chilean people.** No Black or Asian people in photos — this is for a Chilean B2B audience.
- **Brand colors:** Primary `#0f91e3`, text `#32373c`, dark bg `#0a1628`.
- **No phone/email in visible content.** Contact info only in JSON-LD schema for Google, not shown to users.

## Section Order (13 sections)

1. Fixed top bar (urgency + CTA link)
2. Hero (aurora effect, gradient text, word blur-in reveal)
3. Social proof bar (4 animated counters, re-trigger on scroll)
4. Problem → Solution (equal-height cards)
5. How it works (3 steps, progressive timeline animation)
6. Services detail (6 cards with Unsplash images)
7. Benefits (6 cards with hover effects)
8. Testimonials (3 glassmorphism cards)
9. Conversion form (GHL iframe)
10. FAQ accordion (8 questions, JSON-LD linked)
11. Final CTA
12. Minimal footer
13. Floating "Cotizar" button (appears after 3s)
