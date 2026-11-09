# Initial Project Setup

> Read `AGENTS.md` and `context/ui-context.md` before starting.

## Goal

Bootstrap the Next.js 16 project with tooling, design system, and database connection ready for feature development.

## Requirements

- Initialise Next.js 16 (App Router, TypeScript strict, `npm`, root `app/` layout).
- Install and configure Tailwind CSS with design tokens from `ui-context.md`.
- Load Golos Text via `next/font` and wire into `tailwind.config.ts`.
- Set up shadcn/ui, install base components, configure `cn()` in `lib/utils.ts`.
- Set up Supabase browser, server, and middleware clients under `lib/supabase/`.
- Add root `proxy.ts` for Supabase Auth session refresh (Next.js 16 entry point).
- Create `.env.example` with all required keys; keep `.env.local` out of git.
- Configure ESLint, Prettier, and a Husky pre-commit hook.
- Set up Vitest, React Testing Library, and Playwright.
- Create `app/layout.tsx`, `app/globals.css`, and a placeholder `app/page.tsx`.

## Acceptance Criteria

- [x] `npm run dev` and `npm run build` pass with no errors.
- [x] All installed shadcn/ui components import without errors.
- [x] `cn()` works correctly.
- [x] No dark mode styles appear by default.
- [x] Supabase clients initialise without errors.
- [x] `npm test` and `npm run test:e2e` run successfully.

## Open Questions

- Which Node.js and npm versions to pin?
- Supabase CLI as dev dependency or `npx`?
