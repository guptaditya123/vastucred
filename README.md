# Vastucred

A fast, minimalist web landing page for showcasing nearby residential properties for **Rent** and **Sale**, driven directly by structured JSON data.

## Features

- **Minimalist Landing Page:** Clean, distraction-free property showcase designed for nearby residents and seekers.
- **Rent & Sell Categories:** Instant toggling between **All**, **Rent**, and **Sale** properties without page reloads.
- **JSON-Driven Data:** Properties are maintained directly in `data/properties.json` and validated strictly with Zod. No complex database or management dashboards required.
- **Direct Contact:** Instant inquiry action connecting prospective tenants/buyers directly via WhatsApp or phone.
- **Mobile First & SEO Ready:** Blazing fast performance, responsive design, and optimized images using Next.js 16.

## Architecture & Tech Stack

- **Framework:** Next.js 16 (App Router, React Server Components)
- **Language:** TypeScript (Strict)
- **Styling:** Tailwind CSS, shadcn/ui primitives
- **Data Layer:** Local `data/properties.json` validated with Zod schemas
- **Deployment:** Vercel (Edge-ready static site generation)

See the [`context/`](./context) directory for detailed specifications and architecture guidelines.
