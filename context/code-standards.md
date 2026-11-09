# Code Standards

## General

- Prefer small, modular, maintainable, and reusable code with clear responsibilities.
- Follow SOLID principles where applicable.
- Use class-based design patterns for domain and application logic when they improve maintainability, extensibility, or testability.
- Prefer composition over inheritance.
- Do not introduce classes, interfaces, factories, or design patterns unnecessarily.
- Preserve existing conventions when modifying established code.
- Avoid duplicated business logic and unnecessary abstractions.
- Follow DRY (Don't Repeat Yourself), KISS (Keep It Simple), and separation of concerns.
- Use TypeScript strict mode.
- Avoid `any`; prefer explicit types, interfaces, generics, and `unknown` when appropriate.
- Use descriptive naming conventions.
- Prefer immutable data structures where practical.
- Keep functions and methods focused on a single responsibility.
- Avoid deeply nested conditional logic.
- Write code that is easy to understand, test, extend, and maintain.

### Formatting & Naming Conventions

- Use ESLint for static code analysis and linting.
- Use Prettier for consistent code formatting, subject to dependency approval.
- Use 2-space indentation for TypeScript, TSX, JSON, and configuration files.
- Use semicolons consistently.
- Prefer single quotes for TypeScript and JavaScript strings.
- Use trailing commas where supported.
- Use `camelCase` for variables, functions, and methods.
- Use `PascalCase` for classes, interfaces, types, and React components.
- Use `UPPER_SNAKE_CASE` for true application-wide constants.
- Use `kebab-case` for feature folders and general-purpose file names.
- Use `.ts` for TypeScript modules and `.tsx` for React components.
- Keep imports organized and remove unused imports.
- Prefer named exports for reusable modules, except where Next.js conventions require default exports.
- Avoid excessively long files; split modules when responsibilities become unclear.
- Add comments to explain complex decisions and non-obvious business logic rather than restating the code.

## Boundaries

- Keep domain and application logic separate from UI and infrastructure where practical.
- Use explicit DTOs and contracts at important application boundaries.
- Validate external data before passing it into domain logic.
- Keep React components focused on presentation and user interaction.
- Keep business-critical rules in trusted server-side application logic.
- Avoid directly coupling domain logic to Supabase client implementations.
- Use repository or service abstractions only when they provide a meaningful benefit.
- Separate data access, business validation, and response formatting.
- Do not duplicate authorization or business rules across Route Handlers and Server Actions.
- Use shared server-side services for operations accessed through multiple entry points.
- Do not expose server-only modules, credentials, or privileged operations to client components.

### Class-Based Design Patterns

- Prefer classes for stateful domain services, complex business workflows, and implementations that benefit from encapsulation.
- Use interfaces or abstract classes to define contracts when multiple implementations or meaningful substitution requirements exist.
- Apply Strategy Pattern when multiple interchangeable business algorithms are required.
- Apply Factory Method or Abstract Factory when object creation involves multiple implementations or complex construction rules.
- Apply Adapter Pattern when integrating incompatible external interfaces.
- Apply Repository Pattern when separating complex data access from business logic is beneficial.
- Apply Dependency Injection to improve testability and reduce tight coupling where appropriate.
- Use Observer or event-driven patterns only when actual event-based coordination is required.
- Avoid Singleton Pattern for request-specific state, authentication context, or mutable shared data.
- Do not implement design patterns solely for architectural consistency.
- Prefer simple functions for straightforward validation, formatting, transformations, and stateless operations.
- Keep class constructors lightweight and avoid hidden side effects.
- Use explicit dependencies rather than accessing unrelated global state.

### Frontend Architecture & Reusable Components

- Use functional React components with TypeScript.
- Prefer React Server Components by default in Next.js 16.
- Use Client Components only when browser APIs, interactivity, or client-side state are required.
- Follow component composition and reusable component patterns.
- Build shared UI components for repeated interface elements.
- Prefer existing shadcn/ui and Radix UI primitives before creating custom alternatives.
- Use Tailwind CSS consistently for styling.
- Avoid duplicating common UI patterns across pages.
- Separate reusable UI primitives, feature-specific components, and page-level components.
- Keep components focused on a single responsibility.
- Use explicit TypeScript props interfaces or types.
- Prefer controlled components when appropriate for forms and reusable inputs.
- Use React Hook Form and Zod for complex forms and validation.
- Avoid unnecessary global state.
- Prefer local React state and Context API when appropriate.
- Avoid prop drilling through many component levels when composition or Context provides a clearer solution.
- Extract reusable hooks for shared client-side behavior.
- Avoid placing business-critical validation exclusively inside frontend components.
- Do not use class-based React components unless required for a justified compatibility reason.
- Follow accessibility best practices, including keyboard navigation, semantic HTML, and appropriate ARIA attributes.
- Design responsive components for mobile, tablet, and desktop screens.
- Avoid unnecessary client-side JavaScript and hydration.
- Use Next.js Image and Font optimization capabilities.
- Follow the approved SVG Sprite Sheets and CSS Sprite Sheets approach where beneficial.

### Next.js & API Standards

- Follow Next.js 16 App Router conventions.
- Use Route Handlers for REST API endpoints.
- Use Server Actions for appropriate server-side mutations and form operations.
- Keep Route Handlers and Server Actions thin.
- Delegate complex business logic to reusable server-side services.
- Validate all incoming API and Server Action inputs.
- Use consistent API response contracts.
- Return appropriate HTTP status codes.
- Apply authentication, authorization, and ownership validation to protected operations.
- Avoid exposing internal implementation details in API responses.
- Use server-side rendering, static generation, and incremental static regeneration where appropriate.
- Keep public SEO pages accessible without authentication.
- Ensure public responses contain only approved public data.
- Avoid exposing private data through metadata, structured data, caches, or server-rendered output.
- Apply appropriate caching and revalidation strategies.
- Do not cache personalized or sensitive responses publicly.

## Error Handling

- Handle expected failures explicitly.
- Do not silently swallow errors.
- Use meaningful and consistent error messages.
- Distinguish validation, authentication, authorization, business, infrastructure, and unexpected errors.
- Use structured application errors where beneficial.
- Do not expose stack traces, database errors, credentials, or internal implementation details to clients.
- Log errors with sufficient context for debugging without exposing sensitive information.
- Handle asynchronous failures explicitly.
- Use controlled error responses for APIs and Server Actions.
- Implement graceful degradation for noncritical failures where safe.
- Do not report successful operations when required database operations fail.
- Never bypass authorization or mandatory security controls to recover from failures.

## Security

- Validate all untrusted inputs on the server.
- Use Zod or approved validation mechanisms for request validation.
- Never log secrets, credentials, access tokens, or session cookies.
- Never bypass authentication, authorization, or ownership checks for convenience.
- Apply least-privilege and deny-by-default principles.
- Use Supabase Auth for authentication.
- Apply PostgreSQL Row Level Security where applicable.
- Protect server-only environment variables and privileged Supabase credentials.
- Prevent SQL injection, XSS, CSRF, SSRF, and broken object-level authorization.
- Validate uploaded file types, sizes, and signatures.
- Protect private customer, professional, and property owner information.
- Expose only approved public fields to unauthenticated visitors.
- Apply bot protection and anti-scraping controls to public pages and APIs.
- Use configurable, distributed rate limiting where required.
- Avoid hardcoding rate-limit thresholds without an approved policy.
- Use appropriate HTTP security headers and Content Security Policy.
- Follow the security requirements defined in `product-rules.md`.
- Add automated security tests for critical application workflows.

## Configuration

- Do not hardcode environment-specific hosts, credentials, secrets, or URLs.
- Use environment variables for environment-specific configuration.
- Validate required configuration values during application initialization where appropriate.
- Keep server-only secrets separate from public configuration.
- Use the `NEXT_PUBLIC_` prefix only for values explicitly safe to expose to browsers.
- Maintain separate configurations for development, testing, and production.
- Do not commit production credentials or secret environment files to version control.
- Keep configuration names consistent and clearly documented.
- Prefer approved Next.js, Supabase, and Vercel configuration capabilities.
- Do not introduce new infrastructure services or major dependencies without approval.

## Testing

- Add or update tests whenever application behavior changes.
- Use Vitest for unit and appropriate integration tests.
- Use React Testing Library for React component behavior.
- Use Mock Service Worker (MSW) for controlled API mocking where appropriate.
- Use Playwright for end-to-end browser testing.
- Test reusable UI components and important user interactions.
- Test form validation, loading states, error states, and accessibility-related behavior.
- Test REST API request validation, response contracts, and error handling.
- Test authentication, authorization, and resource ownership.
- Test Supabase RLS policies where applicable.
- Test public guest access and ensure private information is not exposed.
- Test critical booking, property listing, and service workflows.
- Test duplicate requests and idempotency for critical operations.
- Test bot protection, rate limiting, and abuse prevention behavior.
- Test important failure paths and edge cases.
- Keep tests deterministic and independent wherever practical.
- Mock external dependencies for isolated tests.
- Use integration tests to validate real interactions between important application components.
- Run automated checks before production deployment.
- Do not modify tests simply to hide implementation failures.