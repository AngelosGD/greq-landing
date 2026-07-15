## Commands

```sh
npm run dev         # start dev server
astro dev --background  # start dev server in background (useful in agent sessions)
astro dev stop      # stop background server
astro dev status    # check background server status
astro dev logs      # follow background server logs
npm run build       # build to dist/
npm run preview     # preview production build locally
npm run astro check # run Astro type checking
```

**No test, lint, or formatting scripts are configured.**

## Stack

- **Astro 7** with TypeScript (`astro/tsconfigs/strict`), ESM (`"type": "module"`)
- **Tailwind CSS v4** via `@tailwindcss/vite` plugin (no PostCSS config)
- Tailwind is imported in `src/styles/global.css` with `@import "tailwindcss"`
- Node `>=22.12.0` required

## Pages

Single-page Spanish landing site for "GReq" (API endpoint design tool).

Entry: `src/pages/index.astro` uses `src/layouts/Layout.astro` (which imports `Glow.astro` background effect) and renders sections: `Navbar`, `Hero`, `Preview`, `Funciones1`, `Funciones2`, `Funciones3`, `Design` (`Design.astro` is a stub).

## Generated / ignored

| Path | Origin |
|---|---|
| `dist/` | build output |
| `.astro/` | generated types + dev state |
| `.env`, `.env.production` | environment (gitignored) |

## Type checking

Run `npm run astro check`. There is no `tsc` script.
