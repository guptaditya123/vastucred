# Architecture

## Architecture Style

- Lightweight, static/server-rendered application built with Next.js 16 App Router and TypeScript.
- Deployed on Vercel with zero runtime database dependencies for property discovery.
- File-driven data architecture: Property listings are loaded directly from a structured JSON dataset (`data/properties.json`) validated with Zod.

## Major Components

| Component | Responsibility |
|---|---|
| **Landing Page (`app/page.tsx`)** | Composes the Hero section, filter tabs, property showcase grid, and contact section. |
| **Data Layer (`lib/properties.ts`)** | Reads `data/properties.json`, parses and validates with Zod, and provides typed helper queries (`getProperties`, `getPropertyById`, etc.). |
| **Property Showcase UI** | Reusable React components: `PropertyGrid`, `PropertyCard`, `PropertyBadge`, `PropertyDetailModal`, and image carousels. |
| **Filter Controller** | Lightweight client component for instantaneous category toggling (`All` \| `Rent` \| `Sale`) without page reloads. |
| **Direct Contact Action** | Generates pre-filled WhatsApp / telephone direct contact links for instantaneous inquiry on specific properties. |

## Module Boundaries

- `data/properties.json`: Authoritative single source of truth for all nearby rental and sale property records.
- `lib/schema.ts`: Strict Zod schema (`PropertySchema`, `PropertyType`, `ListingType`, `PropertyStatus`) providing compile-time and runtime type safety.
- `lib/properties.ts`: Server-side data loader function reading the JSON file; handles caching, filtering, and error handling.
- `components/ui/*`: Generic shadcn/ui and Radix UI primitives (Button, Badge, Dialog, Drawer, Card, Tabs).
- `components/property/*`: Domain-specific property presentation components.

## Data Flow

```
[data/properties.json]
         │
         ▼
[Zod Schema Validation (lib/schema.ts)]
         │
         ▼
[Server Component (app/page.tsx)]
         │
         ▼
[Landing Page UI (Hero + Filter + PropertyGrid)]
         │
         ▼
[User Action: Filter (Rent/Sale) or Click "Inquire on WhatsApp"]
         │
         ▼
[Direct Contact with Owner / Agent]
```

## Architectural Constraints

- **No Management Dashboards:** Avoid adding complex authenticated backends, admin panels, or user dashboards.
- **No Heavy Database Overhead:** Maintain listings via `data/properties.json` rather than requiring a managed database for catalogue reading.
- **Strict Validation:** Every record in `data/properties.json` must strictly validate against the Zod schema. If a required field is missing, fail fast at build/load time.
- **Zero Client Hydration Bloat:** Prefer React Server Components by default; use Client Components strictly where interactive state (e.g. active filter tab, modal open/close) is needed.
- **SEO & Social Sharing:** Static metadata, Open Graph preview tags, and structured JSON-LD generated directly from the property dataset.
