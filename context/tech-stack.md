# Technology Stack

## Frontend
- **Language:** TypeScript
- **Framework:** Next.js 16 (App Router)
- **UI Library:** shadcn/ui
- **Styling:** Tailwind CSS
- **UI Primitives:** Radix UI
- **Icons:** SVG Sprite Sheets + CSS Sprite Sheets
- **Image Optimization:** Next.js Image (`next/image`)
- **Font Optimization:** Next.js Font (`next/font`)
- **Rendering:** Server Components, SSG, ISR, SSR
- **State Management:** React Hooks and Context API (when needed)
- **Forms:** React Hook Form + Zod
- **SEO:** Next.js Metadata API, JSON-LD, XML Sitemap, Robots.txt, Canonical URLs
- **Performance:** Code Splitting, Lazy Loading, Dynamic Imports, CDN Caching

## Backend/Core
- **Framework:** Next.js 16 (App Router)
- **Language:** TypeScript
- **Backend APIs:** Next.js Route Handlers
- **Server-side Operations:** Next.js Server Actions

## Database
- **Primary Database:** Dedicated `d2d` PostgreSQL database (initially Supabase hosted; host portable)
- **Database Access:** Server-only `pg` driver with `APP_DATABASE_URL`, parameterized SQL, and a bounded pool
- **Database Types:** Explicit TypeScript query result/DTO types
- **Security:** PostgreSQL Row Level Security (RLS) with a limited application role; administrator `DATABASE_URL` is migration-only
- **Authentication:** Supabase Auth remains separate from data access

## Communication
- **HTTP/API:** REST API (Next.js 16 Route Handlers)
- **Real-time/networking:**

## Testing
- **Unit:** Vitest + React Testing Library
- **Integration:** Vitest + Mock Service Worker (MSW)
- **End-to-end:** Playwright
- **UI Behavior Testing:** React Testing Library + Playwright
- **API Testing:** Vitest + Next.js Route Handler integration tests
- **Security Testing:** OWASP ZAP, npm audit, ESLint + eslint-plugin-security
- **Authentication & Authorization Testing:** Role-based access control, session validation, and unauthorized access tests
- **Database Security Testing:** Supabase PostgreSQL Row Level Security (RLS) policy tests

## Build / Package Tools
- **Package Manager:** npm (approved for initial setup)
- **Build Framework:** Next.js 16
- **Build Platform:** Vercel

## Deployment Target
- **Platform:** Vercel
- **Application Type:** Web-based application
- **Architecture:** Next.js 16 full-stack monolithic application
- **Database:** PostgreSQL, initially Supabase hosted

## Technology Rules
- Prefer the approved stack above.
- Do not introduce a new framework, database, or major dependency without justification and approval.
- Test critical UI behavior, REST API functionality, and complete user workflows.
- Validate authentication, authorization, and database access policies.
- Run automated tests and security checks before production deployment.

## Authentication Additions

- Approved `canvas` renders custom PNG CAPTCHA images in Node.js Route Handlers.
- Supabase Auth provides email/password identity; server-only admin operations require `SUPABASE_SERVICE_ROLE_KEY` alongside the public URL and anon key.
- Dedicated `AUTH_DATABASE_URL` stores challenge hashes and distributed rate limits in portable PostgreSQL with a restricted `d2d_auth` role.
- Auth browser tests use an isolated test-only identity provider; separate opt-in Vitest tests exercise real PostgreSQL permissions and concurrency.
