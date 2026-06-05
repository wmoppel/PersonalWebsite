# Will Moppel — Professional Website

Personal portfolio website showcasing my game development and 3D
animation work. Built as a fast, static, content-focused site for
game-studio and CS professional applications.

**Live site:** https://willmoppel.com &nbsp;·&nbsp; 
---

## Overview

A static portfolio site with no backend by design — every page is pre-rendered
for speed and reliability. Currently live with a full homepage (hero, bio,
skills, education, and contact). Game and 3D project showcases are the next
planned addition — see the Roadmap below.

## Tech Stack

| Area | Choice |
| --- | --- |
| Framework | [Astro](https://astro.build) — static output, zero JavaScript shipped by default |
| Language | TypeScript (strict mode) |
| Styling | Tailwind CSS v4 — **CSS-first config** (no `tailwind.config.js`; tokens live in `src/styles/global.css`) |
| Fonts | Self-hosted via [Fontsource](https://fontsource.org) — Space Grotesk (display), Inter (body) |
| Hosting | Cloudflare Pages — global CDN, auto-deploys on push to `main` |
| Email | Cloudflare Email Routing + Gmail "send as" |
| Images | Cloudflare R2 _(planned)_ |
| Media | YouTube / Vimeo embeds, lightbox gallery _(planned)_ |

## Sections

Hero · About · Skills · Education · Projects (placeholder) · Contact

## Getting Started

### Prerequisites

- **Node.js** ≥ 22.12.0 (set in `package.json` `engines` field)
- **npm** (ships with Node)

### Local development

```bash
npm install      # install dependencies
npm run dev      # start the dev server at http://localhost:4321
```

The dev server hot-reloads on save.

### Commands

| Command | Action |
| --- | --- |
| `npm install` | Install project dependencies |
| `npm run dev` | Start the local dev server at `localhost:4321` |
| `npm run build` | Build the production site to `./dist` |
| `npm run preview` | Preview the production build locally before deploying |
| `npm run astro ...` | Run Astro CLI commands (e.g. `astro add`, `astro check`) |

## Project Structure

```text
/
├── public/              # static assets served as-is (favicon, etc.)
├── src/
│   ├── components/       # reusable section components (Hero, About, Skills, ...)
│   ├── layouts/
│   │   └── BaseLayout.astro   # shared <head>, meta tags, font + theme imports, <slot/>
│   ├── pages/           # file-based routes; index.astro is the homepage
│   └── styles/
│       └── global.css   # Tailwind import + @theme design tokens
├── astro.config.mjs     # Astro configuration
├── package.json
└── tsconfig.json        # TypeScript config (strict)
```

## Design System

**Important — this project uses Tailwind CSS v4, which is CSS-first.** There is no
`tailwind.config.js`. All design tokens are defined in the `@theme` block in
`src/styles/global.css`, and each token name automatically becomes a utility
class (e.g. `--color-accent` → `text-accent` / `bg-accent` / `border-accent`).
To adjust the palette, edit the token values in that one file.

| Token | Value | Usage |
| --- | --- | --- |
| `--color-base` | `#0a0f1c` | Page background (deep navy-black) |
| `--color-surface` | `#121a2e` | Cards / raised sections |
| `--color-surface-2` | `#1a2440` | Elevated surfaces / hover states |
| `--color-ink` | `#e8ecf6` | Primary text (near-white) |
| `--color-muted` | `#93a0bd` | Secondary / muted text |
| `--color-accent` | `#4d8bff` | Electric-blue accent |
| `--color-accent-hover` | `#6ba0ff` | Accent hover state |
| `--color-line` | `#243149` | Borders / dividers |
| `--font-display` | Space Grotesk Variable | Headings |
| `--font-body` | Inter Variable | Body text |

> **Note on fonts:** Fontsource packages are imported via their `/wght.css` path
> (e.g. `import "@fontsource-variable/inter/wght.css";`) rather than the bare
> package name. Strict TypeScript rejects untyped side-effect imports, and the
> `.css` path sidesteps that. Keep this pattern when adding fonts.

> **`text-base` is a color utility, not a font-size utility:** because
> `--color-base` is defined in `@theme`, Tailwind v4 generates `text-base` as a
> color class (equivalent to `color: var(--color-base)`), shadowing the built-in
> font-size meaning. To set `font-size: 1rem` explicitly, use `text-[1rem]`, or
> just omit it — the body default is already `1rem`.

## Deployment

The site auto-deploys to **Cloudflare Pages** on every push to `main` — there is
no manual deploy step.

- **Build command:** `npm run build`
- **Output directory:** `dist`
- **Framework preset:** Astro

Push to `main` → Cloudflare rebuilds and publishes.

## Roadmap

- [x] Project scaffolding (Astro + TypeScript strict + Tailwind v4)
- [x] Cloudflare Pages deploy pipeline (auto-deploy on push)
- [x] Base layout (tokens, self-hosted fonts)
- [x] Homepage sections (hero, about, skills, education, contact)
- [x] Custom domain + Cloudflare Email Routing + Gmail send-as
- [ ] Game project showcases (YouTube trailer embeds, facade-loaded for performance)
- [ ] 3D showcases (Vimeo reel embeds + still galleries)
- [ ] Content collections for projects (typed schema, data-driven pages)
- [ ] Image hosting on Cloudflare R2
- [ ] SEO pass (Open Graph tags, sitemap, favicon) + Lighthouse audit

## Contact

- **Email:** will@willmoppel.com
- **LinkedIn:** https://www.linkedin.com/in/will-moppel-e197/
- **GitHub:** https://github.com/wmoppel

## License

Source code is public for reference. Project content — text, images, videos, and
artwork — is © Will Moppel and not licensed for reuse.
