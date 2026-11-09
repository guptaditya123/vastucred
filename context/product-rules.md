# Product Rules

This file contains invariants and non-negotiable product behavior for Door2DoorCare.

These rules apply to all features, frontend components, backend APIs, Server Actions, database operations, and integrations.

## Business Rules

- Door2DoorCare must support a scalable, multi-city home-services and residential property marketplace, without hardcoding any single metropolitan city.
- The product encompasses home repairs and maintenance, renovation services, room/flat rentals, property sales, and future property management. The initial MVP includes public discovery, service requests, and basic rental/sale listings as defined in project-overview.md.
- Guests must be able to browse approved service categories, public professional information, and published property listings without authentication.
- Browsing, public search, and filtering must not require login; protected actions such as booking, submitting property inquiries, creating listings, or managing records require authentication and authorization.
- Login prompts must occur only when needed for a protected action; preserve the intended destination or action safely after login.
- Business-critical operations must be validated on the server.
- Never trust client-provided prices, roles, permissions, ownership, listing status, or booking status.
- Service pricing must be calculated and verified using authoritative server-side data. Where pricing is quote-based or not defined, do not invent a price.
- Booking operations must enforce valid business-state transitions; confirmation requires all applicable business conditions.
- Duplicate requests must not create duplicate bookings, payments, inquiries where deduplication is required, or other critical transactions.
- Only authorized providers may accept or update their assigned service requests; only authorized customers and administrators may view or modify protected booking details.
- Renovation quotations, contractor assignments, scope changes, milestones, and payment conditions require explicit workflow definitions before implementation.
- Property owners or explicitly authorized representatives may create and manage listings. Publication, modification, removal, and moderation must enforce ownership and status rules.
- Only approved, published property listings may appear in public discovery. Draft, rejected, unpublished, and private records must remain inaccessible to guests.
- Property listings must clearly distinguish rent from sale, and room/shared accommodation from whole-unit properties; unsupported claims or invented availability must not be shown.
- Property inquiries must not disclose private contact information automatically; any contact-sharing workflow requires an explicit policy and authorization.
- Service availability and property discovery must use configured city, locality, and other supported location data; do not fabricate coverage in unsupported areas.
- Public service, category, property, and location pages must follow an SEO-first architecture and contain meaningful, relevant, unique content.
- Do not generate misleading, duplicate, empty, or unsupported location-specific pages.
- Business rules must remain consistent across frontend, APIs, Server Actions, and database operations.
- Undefined booking, cancellation, refund, commission, payment, property brokerage, verification, and dispute policies require explicit business decisions before implementation.

## Security Rules

- Security must follow defense-in-depth and least-privilege principles.
- Public access must be explicitly limited to approved, non-sensitive fields; authenticated access alone does not grant access to other users' private data.
- Privileged actions require explicit authorization in trusted server/core logic, not only the UI.
- Authentication and authorization must be enforced independently.
- Every protected API and Server Action must verify identity, permissions, and resource ownership where applicable.
- Implement role-based access control (RBAC) for protected operations; role definitions and privileges require explicit approval before implementation.
- Enforce ownership for customer, provider, booking, renovation, property listing, inquiry, and administrative data.
- Use Supabase Auth for authentication.
- Enable PostgreSQL Row Level Security (RLS) on applicable exposed tables; use deny-by-default policies and appropriate grants.
- Public database access policies must not expose private columns through broad table reads. Use explicitly scoped public projections, views, or separate public data structures where necessary.
- Never expose Supabase service-role keys, secrets, or privileged credentials to the client.
- Use secure session handling and appropriately configured cookies.
- Validate all untrusted inputs on the server using Zod or an equivalent approved mechanism.
- Use parameterized database operations.
- Prevent SQL injection, XSS, CSRF, SSRF, privilege escalation, and broken object-level authorization.
- Apply appropriate Content Security Policy (CSP) and HTTP security headers.
- Never trust client-submitted payment confirmations, prices, roles, ownership, or privileged state changes.
- Validate file uploads using size limits, file signatures, allowed formats, and access restrictions.
- Property and service photos may be public only when explicitly approved for publication; private documents and files must use protected access.
- Never expose exact residential addresses, private phone numbers, personal emails, identity documents, or customer information through public asset URLs, HTML, React Server Component payloads, API responses, metadata, structured data, or caches.
- Approximate public location may be shown; exact address disclosure requires an approved policy and appropriate consent/authorization.
- Never publicly cache authenticated or personalized responses.
- Use HTTPS for production communication.
- Apply additional protection to authentication, OTP, booking, property inquiry, listing modification, payment, and administrative operations.
- Avoid logging passwords, access tokens, session cookies, and unnecessary personal information.
- Follow OWASP ASVS and OWASP API Security guidance.
- Security checks must be included in automated testing.
- Keep dependencies updated and monitor known vulnerabilities.

## Bot Protection & Anti-Scraping Rules

- Treat automated AI crawlers, unauthorized property scrapers, abusive bots, and bulk API harvesting as primary security and reliability threats.
- Protect public home-service pages, professional profiles, rental and sale listings, search, filtering, and REST API endpoints against abusive automation.
- Prefer Vercel Firewall and approved platform-native bot protections at the edge before adding external security providers.
- Detect anomalous request volume, repetitive enumeration, high-volume pagination, scraping patterns, and expensive query abuse.
- Apply risk-based throttling, challenges, or blocking for suspicious traffic without forcing every legitimate guest to authenticate or complete a CAPTCHA.
- Enforce bounded pagination, response-size limits, query limits, and resource budgets for public discovery endpoints.
- Keep customer, tenant, property-owner, and service-provider private contact details out of public HTML, metadata, structured data, API payloads, and caches.
- Never assume a logged-in user is entitled to another user's private contact information; enforce explicit authorization and ownership rules.
- Use robots.txt to communicate crawler preferences, but never treat it as a security boundary.
- Distinguish verified search-engine indexing crawlers from AI training crawlers, AI search retrieval bots, and malicious scrapers.
- Allow verified search-engine indexing according to approved SEO rules, with reasonable resource controls; verify crawler identity rather than trusting User-Agent alone.
- Restrict AI training crawlers unless explicitly approved; AI search crawler policy requires a separate business decision.
- Challenge, throttle, or block malicious scraping and bulk harvesting; avoid permanent bans based solely on a single suspicious request.
- Apply protection before costly application or database work when possible.
- Do not disclose sensitive bot-detection logic, credentials, or internal security signals.
- Monitor suspicious traffic, HTTP 403/429 responses, database load, and traffic spikes without collecting unnecessary personal data.
- Do not introduce external CAPTCHA, bot detection, or rate-limiting services without justification and approval.
- Test bot protection, crawler verification, privacy boundaries, and false-positive effects on legitimate users and SEO.
- No fixed global rate-limit threshold is approved yet; establish thresholds from measured traffic and security requirements before launch.

## Reliability Rules

- Prioritize availability, correctness, and graceful degradation.
- Public SEO pages should remain available during temporary noncritical backend failures whenever safely possible.
- Use Server Components by default for public content.
- Prefer static generation and incremental static regeneration for suitable public pages; use server-side rendering for dynamic public content when required.
- Avoid unnecessary client-side JavaScript.
- Use caching where appropriate without compromising data correctness, listing publication status, or privacy.
- Published listing changes, removals, and privacy changes must invalidate or expire affected public caches within an explicitly defined freshness policy.
- Optimize heavy images, fonts, icons, and other assets; use SVG/CSS sprites where beneficial.
- Load noncritical assets lazily and prioritize critical above-the-fold content.
- Target Core Web Vitals: LCP ≤ 2.5 seconds, INP ≤ 200 milliseconds, and CLS ≤ 0.1.
- Performance targets are objectives, not guarantees of millisecond-scale complete page loads.
- Avoid unnecessary API requests and redundant database queries.
- Apply bounded pagination, query timeouts, and resource limits to service/property discovery.
- Use idempotency protection for critical operations.
- Critical database failures must prevent dependent operations from reporting success.
- Authorization or ownership verification failures must stop protected operations.
- Payment verification failures must prevent payment-dependent confirmation.
- Noncritical analytics or logging failures may degrade gracefully when safe.
- Do not bypass mandatory security controls to maintain availability.
- Define explicit fail-open or fail-closed behavior for security infrastructure failures before production.
- Return controlled errors without exposing internal implementation details.
- Monitor application errors, security events, and performance regressions.

## Data Rules

- Supabase PostgreSQL is the primary application database.
- All sensitive data must have explicit ownership and access rules.
- Separate public service/property discovery fields from private user, provider, owner, tenant, booking, and inquiry information.
- Customer information must only be accessible to authorized users and operations.
- Providers must only access customer and booking information required for authorized work.
- Property owners must only access their own private listing and inquiry records unless explicitly authorized otherwise.
- Administrative data access must require explicit authorization.
- Database access must follow least-privilege principles.
- Apply RLS and appropriate database grants to protect exposed data.
- Maintain database constraints for critical integrity requirements.
- Use transactions or equivalent consistency controls for multi-step critical operations.
- Prevent duplicate critical records through idempotency and uniqueness controls.
- Keep authoritative prices, payment states, booking states, and listing publication states under trusted server-side control.
- Define data retention and deletion policies before storing sensitive production information.
- Record security-relevant and business-critical audit events with appropriate actor, action, resource, outcome, and timestamp information.
- Protect audit records from unauthorized modification and disclosure.
- Do not store unnecessary personal information in logs.
- Store database credentials and secrets in approved server-side environment variables.
- Do not use the Vercel deployment filesystem as persistent storage for user-uploaded files.
- Initial application-owned static assets may be deployed through the Next.js public directory.
- User-uploaded property images and private documents require an approved durable storage design and explicit public/private access controls before implementation.
- Define backup, recovery, and restoration requirements before production deployment.
- Never expose private data through public SEO pages, metadata, structured data, or caches.

## AI Decision Rule

If a product/business rule required for implementation is undefined, do not invent it. Record the question/blocker and request a decision.

Additional requirements:

- Do not assume unspecified business workflows, pricing models, payment providers, role permissions, identity-verification requirements, property contact-sharing rules, or moderation policies.
- Do not weaken security, authorization, data ownership, privacy, or rate limiting to simplify implementation.
- Do not introduce new frameworks, databases, infrastructure services, or major dependencies without justification and approval.
- Follow the approved technology stack defined in tech-stack.md: Next.js 16, TypeScript, Supabase PostgreSQL, REST APIs, and Vercel, with the other approved frontend and testing tools.
- Prefer existing Next.js, Supabase, and Vercel capabilities before adding dependencies.
- Preserve existing product invariants when implementing new features.
- Document security-sensitive architectural decisions.
- Require tests for guest access, authorization, ownership, private-data non-disclosure, data integrity, booking state transitions, property publication rules, and rate-limiting behavior.
- If a requirement conflicts with security, reliability, SEO, or another product rule, report the conflict and request a decision.
- Never silently change a non-negotiable product rule.
