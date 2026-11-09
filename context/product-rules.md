# Product Rules

This file contains invariants and non-negotiable product behavior for Vastucred.

These rules apply to all components, schemas, page layouts, and configurations.

## Business Rules

- **Minimalist Scope:** Vastucred is a lightweight, single-page property showcase dedicated exclusively to nearby residential properties for **Rent** and **Sale**.
- **No Management Dashboards:** There are no customer dashboards, owner dashboards, or admin control panels. Property data is maintained directly by updating a local, structured JSON file (`data/properties.json`).
- **No User Accounts:** There is no registration, login, session cookies, or user profile management. All visitors have instant guest access.
- **Strict Listing Types:** Every property in the JSON file must explicitly specify its listing type as either `rent` or `sale`.
- **Status Visibility:** Each property must have an availability status (e.g., `available`, `reserved`, `rented`, `sold`). "Rented" or "Sold" properties may be styled with clear badges or hidden based on maintainer preference.
- **Authoritative Pricing:**
  - For rental properties: Must display monthly rent, and optionally security deposit and maintenance charges.
  - For sale properties: Must display total price, and optionally price per sq ft or carpet area.
  - No hidden or misleading charges.
- **Direct Contact:** The primary conversion action is direct contact (e.g. WhatsApp chat with a pre-filled property reference, or a direct phone call link).
- **Hyperlocal Focus:** Highlight local neighborhood landmarks, distance to nearby essentials (metro, market, schools), and approximate locality rather than arbitrary distant listings.
- **Excluded Features:** Home maintenance services, handyman bookings, renovation projects, commercial properties, online rent payments, and legal deed processing are strictly excluded.

## Data & Schema Rules

- All property data lives in a structured file: `data/properties.json`.
- The dataset must be strictly validated using a **Zod** schema (e.g. `PropertySchema`) at build/runtime.
- Mandatory fields for each property:
  - `id`: Unique identifier (string / slug).
  - `title`: Clear descriptive title (e.g., "Spacious 2 BHK Apartment near Central Park").
  - `type`: `rent` | `sale`.
  - `propertyType`: `room` | `flat` | `independent_house` | `villa` | `studio`.
  - `bhk`: Number of bedrooms (e.g. `1 RK`, `1 BHK`, `2 BHK`, `3 BHK`, `4+ BHK`).
  - `price`: Numeric price or rent per month.
  - `deposit`: Numeric deposit (optional for sale).
  - `location`: Neighborhood / locality name and nearby landmarks.
  - `images`: Array of local or approved remote image paths.
  - `amenities`: Array of key amenities (e.g., "Parking", "Power Backup", "Balcony", "Gated Security").
  - `furnishing`: `unfurnished` | `semi-furnished` | `fully-furnished`.
  - `status`: `available` | `rented` | `sold`.
  - `contact`: Contact phone / WhatsApp number for inquiries.
- Malformed data or missing mandatory fields must trigger validation errors and not render broken UI.

## Privacy & Security Rules

- Only public, authorized contact numbers or WhatsApp handles must be listed in the property contact config.
- Do not expose exact private unit numbers or personal sensitive documents in public data.
- Input validation: If a lightweight inquiry form is used, sanitize all inputs and avoid storing unnecessary personal data.
- No database credentials, service-role keys, or secrets are required on the client.
- External images (if used) must use approved domains configured in `next.config.ts`.

## UI & Performance Rules

- **Static Generation (SSG) / React Server Components:** The landing page renders as a static/server-rendered page with zero database latency.
- **Instant Filtering:** Filtering between `All`, `Rent`, and `Sell` must be instant and seamless with zero page reload.
- **Mobile First:** Ensure large touch targets, accessible buttons, and optimized layouts for smartphone screens.
- **Image Optimization:** All property photos must use `next/image` with appropriate aspect ratios and blur placeholders or responsive sizing.
- **Core Web Vitals:** Target LCP ≤ 1.5 seconds, CLS ≤ 0.05, and INP ≤ 100 milliseconds.
