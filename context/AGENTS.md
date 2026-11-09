# AI Agent Instructions

This file is the entry point for AI coding agents working on the Door2DoorCare repository.

## Base Context

Before significant implementation, read the relevant information from:

- `context/project-overview.md` — product definition,
   goals, features, and scope
- `context/architecture.md` — system structure,
   boundaries, storage model, and invariants
- `context/tech-stack.md`
- `context/product-rules.md`
- `context/code-standards.md` -  implementation rules
   and conventions
- `context/ui-context.md` - theme, colors, typography,
   and component conventions
- The relevant file under `context/feature-specs/`
- `context/progress-tracker.md` to understand implementation progress and blockers

Do not load irrelevant context merely because it exists.

Follow the approved Next.js 16, TypeScript, Supabase PostgreSQL, and Vercel architecture.

## Feature Workflow

- Understand the feature specification, business rules, and acceptance criteria.
- Inspect the existing implementation before proposing changes.
- Identify affected UI components, application services, REST APIs, database models, configuration, and tests.
- Identify missing product, security, or architecture decisions; do not guess them.
- Produce a small, independently verifiable implementation plan.
- Implement one feature unit at a time without unrelated changes.
- Reuse existing React components, hooks, services, and utilities where appropriate.
- Apply class-based design patterns only when they provide meaningful benefits.
- Validate business-critical operations on the server.
- Add or update unit, integration, end-to-end, and security tests as applicable.
- Run relevant build, lint, type-checking, and testing commands.
- Review changes for regressions, privacy leaks, security issues, and architectural violations.
- Update relevant context files and `progress-tracker.md` after implementation.

## Non-Negotiable Rules

- Never invent missing business requirements or user permissions.
- Never bypass authentication, authorization, ownership checks, or Supabase RLS.
- Never expose private customer, professional, or property information through public pages or APIs.
- Preserve guest access to approved public service and property listings.
- Follow bot protection, anti-scraping, and configurable rate-limiting rules.
- Never trust client-provided prices, roles, booking states, or privileged data.
- Keep domain logic separate from presentation and infrastructure where practical.
- Use reusable functional React components and existing shadcn/ui primitives.
- Avoid unnecessary classes, dependencies, abstractions, and architectural complexity.
- Never change unrelated functionality just to complete a feature.
- Preserve existing public contracts unless explicitly approved.
- Follow SEO-first and performance-conscious development practices.
- Do not introduce new frameworks, databases, or infrastructure without approval.
- Do not silently modify approved product rules or technology decisions.
- Never hardcode secrets, credentials, or environment-specific configuration.
- Do not claim completion until acceptance criteria and relevant tests have been verified.
- Record unresolved requirements and implementation blockers in `context/progress-tracker.md`.

<!-- BEGIN:nextjs-agent-rules -->

## This is NOT the Next.js you know

This version has breaking changes — APIs, conventions, and file structure may all differ from your training data. Read the relevant guide in `node_modules/next/dist/docs/` (resolved from this file's directory; in monorepos the `next` package may not be visible from the repo root) before writing any code. Heed deprecation notices.

This block is written and re-added by `next dev` — verify at `node_modules/next/dist/server/lib/generate-agent-files.js`. Removing it from a diff only re-creates the uncommitted change; committing it with your work keeps the tree clean.

<!-- END:nextjs-agent-rules -->
