# Frontend Code Structure

This document describes the key folders and files inside the `frontend/` directory.

## Quick start
- Install: `npm i`
+ Run locally: `npm run dev` (opens at `http://localhost:3000`)

## Top-level files
- `package.json`: project scripts and dependencies.
- `next.config.ts`, `tsconfig.json`: Next.js and TypeScript configs.
- `components.json`: shadcn/ui config and path aliases (e.g. `@/components`, `@/lib/utils`).

## Directory layout

- `app/`
  - `page.tsx` — main route `/`.
  - `layout.tsx` — application layout wrapper.
  - `globals.css` — Tailwind/CSS reset and global styles referenced by `components.json`.
  - `demo/page.jsx` — demos or example page at `/demo`.

- `components/`
  - `header.tsx`, `hero-section.tsx` — top-level shared components.
  - `ui/` — small, reusable UI elements (buttons, dropdowns, textarea, theme toggle, animated background, etc.).

- `lib/`
  - `utils.ts` — shared helper functions.

- `public/` — static assets (SVGs, images) served at the root.

## Styling & UI
- Tailwind CSS is used (see `app/globals.css` and `components.json` Tailwind settings).
- `components.json` defines aliases and UI registry settings used by the `shadcn` tooling.

## Import aliases
The project uses path aliases from `components.json`; examples:

- `@/components` → `components/`
- `@/lib/utils` → `lib/utils.ts`

Example import:

```ts
import Header from '@/components/header'
import { format } from '@/lib/utils'
```

## Notes
- Routes use the Next.js App Router (`app/` directory).
- Keep small, generic controls inside `components/ui/` and page-specific components at top-level `components/`.
