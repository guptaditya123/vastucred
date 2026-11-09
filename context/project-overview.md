# Project Overview

## Problem

Finding or renting properties within a specific neighborhood or nearby locality is often unnecessarily complicated:
- Large real estate portals are cluttered, generic, full of expired listings, and overwhelm users with unwanted calls from distant brokers.
- Property owners with just a few properties to rent or sell in their local neighborhood need a simple, hassle-free way to showcase them without managing complex dashboards, paying heavy portal fees, or dealing with complicated CMS systems.
- Nearby tenants and buyers simply want a clean, fast, and straightforward view of available properties with honest details, clear pricing, and direct contact options.

Vastucred solves this by offering a fast, minimalist web landing page showcasing curated nearby residential properties for rent and sale, powered directly by a lightweight JSON dataset.

## Product

Vastucred is a lightweight, minimalist landing page and property showcase tailored for nearby/local residential properties.

Key characteristics:
- **JSON-Driven Data:** All property listings (rent and sell) are maintained directly in a structured, version-controlled JSON data file (e.g., `data/properties.json`). There is no complex database setup or administrative CMS required.
- **Minimalist Single Landing Page:** A clean, distraction-free landing page displaying available properties with quick filters for **Rent** and **Sale**.
- **No Management Dashboards:** No tenant/owner login, no password portals, and no administrative management dashboards. Adding or updating a property is as simple as updating the JSON file.
- **Hyperlocal & Direct:** Focused on nearby properties with upfront details (rent/sale price, security deposit, BHK, furnishing, area, amenities, and photos) and a direct contact call-to-action (e.g., WhatsApp message or phone call).

## Target Users

- **Primary user:** Nearby residents, students, working professionals, and families looking for local rooms, flats, or houses to rent or buy in the area.
- **Secondary user (Site Maintainer / Property Owner):** The owner or administrator who maintains listings by updating the structured JSON file.

## Core Use Cases

- **Use case 1:** View a curated collection of nearby residential properties directly on a fast-loading landing page.
- **Use case 2:** Switch easily between **All**, **For Rent**, and **For Sale** properties.
- **Use case 3:** View essential property details: high-quality images, monthly rent / sale price, security deposit, BHK configuration, furnishing status, area, and key amenities.
- **Use case 4:** Connect directly with the owner or representative via a single click (WhatsApp chat, phone call, or simple inquiry modal).
- **Use case 5:** Maintain and update property details, pricing, availability status (`available`, `rented`, `sold`), or add new properties by editing the JSON file.

## MVP Scope

- **Minimalist Hero Section:** Clean introduction highlighting nearby property availability.
- **Category Filter:** Instant toggling between **All**, **Rent**, and **Sell**.
- **Property Cards & Grid:** High-impact, responsive cards displaying property photos, badges (Rent/Sale, Available/Rented), pricing, BHK, furnishing, and locality.
- **Property Detail View:** A lightweight modal or dedicated detail section showing full photo gallery, detailed description, amenities list, and neighborhood highlights.
- **Direct Contact CTA:** Clickable action to start a WhatsApp conversation with pre-filled property details or direct phone call.
- **JSON Schema & Validation:** Zod schema validating `data/properties.json` at build time to prevent malformed data or broken UI.
- **Mobile-First & SEO Optimized:** Blazing fast load times, Next.js Image optimization, Open Graph tags, and responsive design for all screen sizes.

## Out of Scope

- User authentication, login, signup, and user profiles.
- Customer dashboards, owner management portals, or administrative backends.
- Dynamic database CRUD operations or CMS admin panels.
- Complex multi-city search engines and high-volume pagination.
- Online payment processing, digital rent escrow, or contract drafting.
- Home repairs, handyman services, or renovation contractors.
- Commercial real estate.

## Constraints

- **Platform:** Web-based responsive application.
- **Data Source:** Local, strongly-typed JSON file (`data/properties.json`).
- **Frontend Framework:** Next.js 16 (App Router), TypeScript, Tailwind CSS, shadcn/ui primitives.
- **Validation:** Zod for validating the JSON property schema.
- **Deployment:** Vercel (static site generation / server components for optimal speed and zero database latency).
- **Performance:** Instant page load, Core Web Vitals targets (LCP ≤ 1.5s, CLS ≤ 0.05).
- **Mobile Friendly:** Smooth touch interactions, optimized image loading, and responsive layouts.

## Success Criteria

- The landing page loads almost instantaneously with zero reliance on external database roundtrips.
- Visitors can view nearby rental and sale properties and filter between Rent and Sell effortlessly.
- Prospective tenants and buyers can click a direct contact button (e.g. WhatsApp/Call) to reach out immediately.
- The site owner can add, update, or remove properties simply by editing `data/properties.json`.
- Automated build, type-check, and lint pass cleanly with 100% valid JSON data.
