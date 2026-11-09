# Code Standards

## General Principles

- **Simplicity First (KISS):** Keep the codebase simple, modular, and maintainable. Avoid unnecessary abstractions, factories, or patterns.
- **Single Source of Truth:** Property data is managed in `data/properties.json` and validated strictly via Zod schemas.
- **TypeScript Strict Mode:** Maintain 100% strict typing. Avoid `any`; use inferred types from Zod schemas and explicit React component props.
- **Component Reusability:** Build reusable, accessible UI components with shadcn/ui and Radix UI.
- **Clean Formatting:** Use 2-space indentation, consistent semicolons, and single quotes for strings.

## Architecture & Data Standards

- **Server Components by Default:** In Next.js 16, prefer React Server Components for non-interactive rendering. Use `"use client"` only for components requiring browser interaction (such as category tab filtering, image gallery modals, or direct contact triggers).
- **Zod Data Validation:**
  - Define all property schemas in `lib/schema.ts`.
  - Validate the `data/properties.json` dataset using `safeParse` or `parse` in the data loader.
  - Fail fast with actionable error messages if JSON data does not meet schema requirements.
- **Helper Utilities:** Keep data fetching and filtering helpers inside `lib/properties.ts`.
- **No Unnecessary State:** Avoid global state libraries (Redux, Zustand) since the application is a lightweight landing page. Use simple React `useState` for local UI interactions.

## Frontend & Styling Conventions

- **Tailwind CSS:** Use Tailwind classes for layout, typography, colors, and spacing following tokens in `ui-context.md`.
- **Responsive Design:** Design mobile-first. Ensure smooth touch targets (minimum 44x44px for buttons) and clean responsive grids.
- **Next.js Image:** Always use `next/image` with explicit width/height or `fill` with `sizes` to avoid Layout Shift (CLS).
- **Direct Action Links:** Construct clean, encoded links for direct WhatsApp actions (`https://wa.me/<number>?text=...`) and phone links (`tel:<number>`).

## Error Handling & Reliability

- Provide graceful fallback UI if property images fail to load or if a filter returns no results (clean empty state).
- Ensure the landing page renders smoothly even if optional property fields (e.g. deposit or extra amenities) are omitted in the JSON.
- Never expose private personal data in client payloads or public JSON files.

## Testing Standards

- Test Zod validation against `data/properties.json` to prevent malformed listings from breaking the build.
- Test property card rendering, filtering between Rent and Sale, and modal open/close interactions using Vitest and React Testing Library.
- Verify production build with `npm run build` prior to committing.
