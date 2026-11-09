# Initial Project Setup

> Read `AGENTS.md` and `context/ui-context.md` before starting.

## Goal

Bootstrap the Next.js 16 project with tooling, design system, and component primitives ready for minimalist landing page development.

## Requirements

- Initialise Next.js 16 (App Router, TypeScript strict mode, `npm`, root `app/` layout).
- Install and configure Tailwind CSS with design tokens from `ui-context.md`.
- Load Golos Text via `next/font` and wire into `tailwind.config.ts`.
- Set up shadcn/ui, install base components (Button, Badge, Card, Dialog, Tabs), configure `cn()` in `lib/utils.ts`.
- Install Zod for schema validation.
- Create `.env.example` with public site configuration.
- Configure ESLint and Prettier.
- Set up Vitest and React Testing Library.
- Create `app/layout.tsx`, `app/globals.css`, and a clean placeholder `app/page.tsx`.

## Acceptance Criteria

- [ ] `npm run dev` and `npm run build` pass with no errors.
- [ ] All installed shadcn/ui components import without errors.
- [ ] `cn()` utility works correctly.
- [ ] Light theme styles render as default without flashes.
- [ ] Zod imports and validates schemas as expected.
- [ ] `npm test` runs successfully.

## Open Questions

- None.
