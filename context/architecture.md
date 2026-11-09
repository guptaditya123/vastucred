# Architecture

## Architecture Style

- Modular monolith using Next.js 16 App Router with TypeScript.
- Full-stack web application deployed on Vercel.
- PostgreSQL as the primary database, initially hosted by Supabase in a dedicated `d2d` database. The application uses a portable server-side PostgreSQL driver and a dedicated limited role. Supabase Auth remains in the provider's default database.
- Separate UI, application logic, and infrastructure responsibilities.

## Major Components

| Component | Responsibility |
|---|---|
| UI | Next.js pages, reusable React components, service discovery, property listings, and user interactions. |
| Application/Core | Business workflows, booking management, property management, validation, and authorization. |
| Infrastructure | PostgreSQL connection pool, SQL migrations, Supabase Auth, and external integrations. |

## Module Boundaries

- Catalogue SQL is encapsulated by `PostgresCatalogRepository`; customer summary SQL is encapsulated by `PostgresDashboardRepository`. Constructors receive explicit database dependencies.
- `CustomerDashboardService` depends on an identity resolver and `DashboardRepository` contract. It verifies identity before reading private activity and stores no request state.
- `lib/catalog.ts` and `lib/dashboard.ts` are server composition modules retaining the existing page/API contracts. Simple validation and React presentation remain functional.

- **Authentication:** User identity, sessions, and role-based access.
- **Home Services:** Service categories, professionals, availability, and bookings.
- **Renovation:** Renovation requests, quotations, and contractor information.
- **Property:** Rental listings, property sales, search, and inquiries.
- **Users:** Customer, provider, and property owner profiles.
- **Admin:** Platform administration and moderation.
- **Shared:** Reusable UI components, validation schemas, and common utilities.

Modules must communicate through defined interfaces and shared application services without unnecessary coupling.

## Communication

- **Frontend to Backend:** REST APIs using Next.js Route Handlers.
- **Server-side Operations:** Next.js Server Actions.
- **Database:** `pg` on the server through `APP_DATABASE_URL`; parameterized SQL and PostgreSQL RLS. `DATABASE_URL` is an administrator connection used only by the migration script.
- **Authentication:** Supabase Auth.
- **Real-time Communication:** Not defined for the initial MVP.

## Key Data Flows

- **Public Browsing:** Guest → Next.js page → server-side catalogue queries → PostgreSQL → service/property listings.
- **Service Booking:** Customer → Authentication → Validation → Booking service → Database → Booking status.
- **Property Listing:** Property owner → Authentication → Authorization → Listing validation → Database → Public listing.
- **Property Inquiry:** Customer → Authentication → Property inquiry service → Database → Authorized property owner.
- **Administration:** Admin → Authentication → Role verification → Authorized operation → Database.

## Architectural Constraints

- Keep domain logic independent from presentation details.
- Use reusable React components and class-based design patterns only where appropriate.
- Validate business-critical operations on the server.
- Enforce authentication, authorization, ownership, and PostgreSQL RLS. Supabase Auth remains the identity provider; a database host move does not require moving Auth.
- Protect private information from unauthenticated visitors.
- Apply bot protection and anti-scraping controls to public endpoints.
- Keep critical workflows independent from noncritical telemetry and logging.
- Follow the approved technology stack and product rules.
- Do not introduce new frameworks, databases, or architectural styles without approval.

## Authentication Implementation

AuthService composes CAPTCHA, OTP and identity contracts. PostgreSQL adapters use a dedicated `d2d_auth` connection via `AUTH_DATABASE_URL`, separate from catalogue access. CAPTCHA answers and OTPs use salted scrypt hashes and atomic single-use/attempt transactions. Supabase Auth alone manages passwords and identity; its admin key remains server-only. Auth Route Handlers explicitly validate origin, bounded input and distributed HMAC-keyed rate limits. Development OTP console delivery is opt-in; production delivery fails closed pending an approved provider.
