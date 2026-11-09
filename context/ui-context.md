# UI Context

## Purpose

This document defines the global UI/UX design system, visual conventions, interaction patterns, accessibility standards, and reusable component rules for Vastucred. It applies to the minimalist landing page and property showcase interface. Feature-specific screens, fields, and functionality belong in `context/feature-specs/`, not this file.

---

# 1. UI Goals

- Deliver a modern, clean, premium, trustworthy, and easy-to-use interface.
- Maintain a consistent visual language across the entire application.
- Prioritize clarity, accessibility, performance, and predictable interactions.
- Keep navigation and system feedback obvious without visual clutter.
- Prefer functional simplicity over decorative complexity.

---

# 2. Target Platforms

- **Primary platform:** Responsive web application using Next.js 16.
- **Supported form factors:** Mobile, tablet, and desktop browsers.
- **Design approach:** Mobile-first responsive layouts, progressively enhanced for larger screens.
- Do not assume a native mobile or desktop application.
- Define exact breakpoint values through the approved Tailwind configuration; avoid arbitrary per-feature breakpoints.

---

# 3. Application Layout

- Use a clean header with brand logo, concise tagline, and quick contact link.
- Minimalist hero section introducing the nearby property collection with Rent / Sell toggle tabs.
- Clean responsive property grid showcasing available homes with high-quality photo cards.
- Prefer spacious page containers, clear visual hierarchy, and responsive grids.
- Use consistent alignment, content widths, and section spacing.
- On narrow screens, adapt navigation and side panels rather than compressing desktop layouts.
- Do not prescribe feature-specific menu items or pages here.

## Layout Rules

- Keep primary actions discoverable and navigation predictable.
- Avoid unnecessary nested cards, panels, and competing focal points.
- Use established layout primitives before introducing a new pattern.
- Feature direct WhatsApp and call actions prominently on each property card.

---

# 4. Visual Design

## Colors

Use centrally defined semantic design tokens. The approved core palette is:

| Token | Hex | Usage |
|---|---|---|
| `brand-primary` | `#356DBE` | Brand accents, navigation emphasis, links, selected states |
| `text-strong` | `#000000` | Prominent headings and high-emphasis text |
| `surface-muted` | `#F6F6F6` | Subtle backgrounds and secondary surfaces |
| `surface-base` | `#FFFFFF` | Primary backgrounds, cards, and content surfaces |

Supporting tokens inspired by the approved reference UI:

| Token | Hex | Usage |
|---|---|---|
| `action-emphasis` | `#2451F5` | Select high-emphasis calls to action |
| `surface-blue-soft` | `#EAF0FF` | Selected areas, subtle highlights |
| `border-subtle` | `#E5E7EB` | Borders and dividers |
| `text-muted` | `#64748B` | Secondary descriptions and metadata |

- Use a soft blue gradient for selected large decorative surfaces; keep readable foreground contrast.
- Use light backgrounds, rounded white cards, subtle borders, and restrained shadows.
- Use semantic success, warning, error, and information tokens; exact values must be defined and contrast-tested in the theme before use.
- Never hardcode arbitrary colors inside feature components.
- Do not rely on color alone to communicate state.
- The approved default is a light theme; dark mode is not assumed.

---

# 5. Typography

- **Primary typeface:** Golos Text, loaded using `next/font`.
- Use a clear type hierarchy: page title, section heading, card heading, body, secondary text, and caption.
- Prefer bold, high-impact headings for prominent editorial sections and restrained typography in operational interfaces.
- Use a consistent scale with responsive adjustments.
- Avoid introducing other font families without approval.
- Maintain accessible line heights, readable sizes, and sufficient contrast.

---

# 6. Spacing

- Follow Tailwind's configured spacing scale and shared layout tokens.
- Typical rhythm: 4, 8, 12, 16, 24, 32, and 48 px, with larger section spacing where appropriate.
- Use generous whitespace around major content areas and consistent internal padding in cards and forms.
- Avoid one-off spacing values unless justified by a reusable design need.
- Standardize border radii, shadows, and container widths through shared tokens.

---

# 7. Reusable Components

- Prefer existing shadcn/ui components and Radix UI primitives before creating custom ones.
- Build reusable, typed functional React components for common patterns: buttons, inputs, selects, checkboxes, radio groups, cards, tabs, dialogs, drawers, tables, badges, tooltips, pagination, search fields, filters, toasts, skeletons, and empty states.
- Separate generic UI primitives from layout components and feature-specific compositions.
- Reuse components through props, variants, and composition; avoid duplicated styling and behavior.
- Do not modify generated `components/ui/*` files unnecessarily; prefer wrappers or composition when practical.
- Keep feature-specific content and business behavior outside the shared component library.

---

# 8. Buttons and Actions

- Use a consistent action hierarchy: primary, secondary, tertiary, and destructive.
- Use rounded or pill-shaped buttons in line with the approved visual references.
- Use `#356DBE` as the standard brand action color; reserve `#2451F5` for selected high-emphasis actions, consistently applied.
- Black buttons may be used as a deliberate visual variant where contrast and hierarchy warrant it.
- Show visible hover, focus, pressed, loading, and disabled states.
- Primary actions use the shared `Button`: `primary` (#356DBE), `primary-hover` (#2C5DA3), and `primary-active` (#244D89), with white text throughout. Use darker shades of the same blue for interaction states; feature-level CSS must not override those colors. Outline/secondary actions retain their separate light-surface treatment.
- Avoid multiple competing primary actions within the same decision area.
- Confirm destructive or irreversible actions.
- Use semantic buttons for actions and links for navigation.

---

# 9. Forms

- Use React Hook Form and Zod where appropriate, following the approved technology stack.
- Give fields visible labels, validation messages, required/optional cues, and help text where useful.
- Keep form controls visually consistent in size, border, radius, and focus treatment.
- Make validation actionable and accessible; do not rely only on placeholders.
- Disable duplicate submissions while pending where appropriate.
- Treat client validation as UX; server validation remains authoritative.

---

# 10. Data Tables

- Use consistent table patterns for headers, row density, sorting, filtering, pagination, and row actions.
- Provide loading, empty, error, and permission-aware states.
- Prefer readable tables on wide screens and appropriate responsive alternatives on narrow screens.
- Avoid loading unbounded datasets in the browser.
- Use clear labels and accessible action menus rather than crowding rows.

---

# 11. Modals and Dialogs

- Use dialogs for focused, short interactions and confirmations.
- Use a full page or dedicated flow for complex, lengthy tasks.
- Each dialog needs a descriptive title, clear actions, and an obvious close/cancel mechanism.
- Use accessible Radix/shadcn primitives for focus management and keyboard behavior.
- On mobile, consider a drawer or full-screen treatment when more usable.

---

# 12. Application States

- Every data-driven component must consider loading, empty, error, success, unauthorized, and disabled states where applicable.
- Use skeletons for content loading when they reduce perceived layout shift.
- Provide recovery actions for recoverable failures.
- Do not display sensitive content during unauthorized or pending states.
- Never implement only the happy path.

---

# 13. Feedback

- Give immediate, proportional feedback for user actions.
- Show pending states while requests are processing and clear success or failure outcomes afterward.
- Prefer inline messages for contextual feedback and toasts for brief non-blocking updates.
- Prevent misleading success messages before server confirmation.

---

# 14. Responsive Design

- Design mobile-first, then enhance tablet and desktop layouts.
- Use responsive grids, fluid containers, adaptable navigation, and appropriately sized touch targets.
- Move complex side panels into drawers or dedicated views on smaller screens where suitable.
- Preserve essential actions and information on all supported screen sizes.
- Test realistic content lengths, zoom, orientation changes, and narrow viewports.

---

# 15. Accessibility

- Use semantic HTML, logical heading order, keyboard-accessible controls, visible focus indicators, and meaningful labels.
- Follow WCAG 2.2 AA as the accessibility target where applicable.
- Maintain sufficient text and control contrast, including on gradients and colored buttons.
- Support reduced motion preferences and avoid unnecessary animation.
- Provide alt text for informative images and mark decorative imagery appropriately.
- Do not communicate important status using color or icons alone.

---

# 16. Permissions

- Render actions and information according to the user's authorized state.
- Guest-facing interfaces may show only approved public information.
- Hidden or disabled controls are presentation decisions, never authorization enforcement.
- Protected operations must still be validated on the server.
- Do not reveal private information through UI props, HTML, metadata, or client payloads.
- Define role-specific capabilities in feature specifications, not in this global UI file.

---

# 17. Navigation

- Use predictable, consistent navigation patterns across the application.
- The approved visual direction includes compact, rounded navigation and clearly indicated active states.
- Preserve browser back/forward behavior and meaningful URLs.
- Keep navigation usable with keyboard, touch, and assistive technologies.
- Avoid introducing new navigation paradigms for individual features without justification.
- Feature-specific navigation labels and routes belong in feature specifications.

---

# 18. Icons

- Use the approved SVG Sprite Sheets and CSS Sprite Sheets approach where beneficial.
- Keep icon style, stroke weight, alignment, and sizing consistent.
- Prefer accessible labels when icons convey actions or important meaning.
- Avoid adding an unrelated icon library without approval.
- Use decorative icons sparingly and do not substitute them for clear text.

---

# 19. Notifications

- Use toasts for small non-blocking outcomes, inline messages for contextual feedback, banners for broad notices, and dialogs for important decisions.
- Keep wording concise, specific, and actionable.
- Ensure notification content is accessible to assistive technologies where appropriate.
- Avoid modal interruptions for routine successes.

---

# 20. Performance

- Prefer Next.js 16 Server Components for noninteractive content.
- Use Client Components only where browser interaction or client state requires them.
- Use `next/image`, `next/font`, responsive image sizes, lazy loading, and appropriate code splitting.
- Avoid unnecessary rerenders, repeated requests, large client bundles, and layout shifts.
- Follow approved SSG, ISR, SSR, and caching strategies where appropriate.
- Optimize Core Web Vitals with targets of LCP <= 2.5 s, INP <= 200 ms, and CLS <= 0.1.
- Keep public content SEO-friendly without compromising privacy or security.

---

# 21. UI State Ownership

- Keep local interaction state inside the owning component when practical.
- Use React Hooks and Context API only when shared state is genuinely needed.
- Treat server-derived data as authoritative; avoid unnecessary duplication into global client state.
- Keep state transitions predictable and avoid conflicting sources of truth.
- Do not introduce additional state-management frameworks without approval.

---

# 22. Feature UI Requirements

Each UI-related feature specification must define, as applicable:

- Screens or routes affected.
- Reusable components and new component needs.
- User actions and interaction states.
- Loading, empty, error, success, disabled, and unauthorized behavior.
- Permission and public/private visibility requirements.
- Responsive behavior and accessibility expectations.
- Observable acceptance criteria.

Do not define feature-specific functionality in this file.

---

# 23. AI Coding Agent Rules

- Read this file and the relevant feature specification before changing UI.
- Inspect existing components, layouts, and design tokens first.
- Follow the approved Golos Text, blue/black/white theme, and supporting semantic tokens.
- Prefer shadcn/ui, Radix UI, Tailwind CSS, and reusable functional components.
- Do not invent feature behavior, routes, permissions, or business rules.
- Implement all relevant loading, error, empty, and permission states.
- Preserve accessibility, responsive behavior, and performance.
- Avoid unrelated redesigns and unnecessary new dependencies.
- Keep feature logic out of generic shared components.
- Request approval before materially changing the design system.

---

# 24. UI Decision Priority

When UI decisions are unclear, use this order:

- Approved feature specification and product rules.
- Existing application patterns and shared components.
- This UI context and approved visual references.
- Existing design tokens and theme configuration.
- Ask for clarification when the decision materially affects behavior or consistency.

Do not invent a competing design system.

---

# 25. Definition of Done

A UI change is complete when:

- Its approved requirements and acceptance criteria are met.
- The approved theme and reusable component patterns are followed.
- Responsive behavior is verified on mobile, tablet, and desktop.
- Loading, empty, error, and permission states are handled where relevant.
- Accessibility and keyboard interaction are checked.
- Public/private data visibility remains correct.
- No unrelated UI or behavior has regressed.
- Relevant component, integration, and end-to-end tests pass.
- Lint, type checks, and `npm run build` pass where applicable.
