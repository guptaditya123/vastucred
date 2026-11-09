# Technology Stack

## Frontend
- **Framework:** Next.js 16 (App Router)
- **Language:** TypeScript (strict mode)
- **UI Components:** shadcn/ui primitives
- **Styling:** Tailwind CSS
- **UI Primitives:** Radix UI
- **Typography:** Golos Text (via `next/font`)
- **Image Optimization:** Next.js Image (`next/image`)
- **Rendering:** React Server Components (RSC) + Static Site Generation (SSG)
- **Interactive State:** React Hooks (for active filter tab and modal states)
- **Icons:** Lucide React / SVG icons
- **SEO:** Next.js Metadata API, Open Graph tags, JSON-LD Structured Data

## Data Layer
- **Source:** Local structured JSON file (`data/properties.json`)
- **Schema Validation:** Zod (runtime and build-time validation)
- **Type Safety:** TypeScript types inferred directly from Zod schemas
- **Storage:** File-based, version-controlled directly in git (no database required for listing display)

## Testing
- **Unit & Component Testing:** Vitest + React Testing Library
- **Schema Validation Testing:** Vitest tests for `data/properties.json` data integrity

## Build & Deployment
- **Package Manager:** npm
- **Build Platform:** Vercel (Edge / CDN static caching)
- **Runtime:** Node.js

## Technology Rules
- Keep the application simple, lightweight, and fast.
- Do not add complex database connections, authentication providers, or CMS backends.
- Maintain property data directly in `data/properties.json` and validate all changes with Zod.
- Test responsive layouts and JSON schema validation before deployment.
