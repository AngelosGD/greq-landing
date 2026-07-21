## Commands

```sh
npm run dev               # dev server at localhost:4321
npm run dev -- --background  # start in background
npx astro dev status      # check background server
npx astro dev logs        # tail background server logs
npx astro dev stop        # stop background server
npm run build             # build to dist/
npm run preview           # serve production build locally
npm run astro check       # typecheck only
```

No test, lint, or formatting scripts exist.

## Stack

- **Astro 7** + TypeScript (`astro/tsconfigs/strict`), ESM (`"type": "module"`)
- **Tailwind CSS v4** via `@tailwindcss/vite` (no PostCSS config, no `tailwind.config.*`)
  — `@import "tailwindcss"` in `src/styles/global.css`
- Node `>=22.12.0`
- VS Code extension: `astro-build.astro-vscode`

## Structure

Single-page Spanish landing site for "GReq" (API endpoint design tool).

```
src/
  pages/index.astro              → entry, renders all sections in order
  layouts/Layout.astro           → html shell, imports Glow.astro + global.css
  components/
    Navbar.astro
    Hero.astro
    Preview.astro
    Funciones1.astro             → imported as `Funciones` in index.astro
    Funciones2.astro
    Funciones3.astro
    Design.astro
    Footer.astro
    Glow.astro                   → background effect, used by Layout
  styles/global.css              → @import "tailwindcss"; html {scroll-behavior: smooth}
  assets/                        → astro.svg, background.svg
public/                          → favicon.*, preview*.png
```

## Quirks

- `Funciones1.astro` imported as `Funciones` in `index.astro`.
- `Layout.astro` has `<html lang="en">` despite Spanish content.
- Layout has no `<meta name="description">` — agents adding SEO should include it.
- `CLAUDE.md` is an unmaintained duplicate of this file.

## Generated / ignored

| Path | Origin |
|---|---|
| `dist/` | build output |
| `.astro/` | generated types + dev state |
| `.agents/skills/` | installed via `skills-lock.json` (3 design skills) |
| `node_modules/` | dependencies |
| `.env`, `.env.production` | env files (gitignored) |
