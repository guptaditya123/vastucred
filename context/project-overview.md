# Project Overview

## Problem

People living in metropolitan cities face multiple challenges when managing their homes and properties.

Finding reliable plumbers, electricians, carpenters, painters, appliance repair technicians, renovation contractors, and other skilled professionals is often difficult and time-consuming.

Customers frequently depend on different service providers, applications, and local contacts for their everyday household requirements.

Similarly, people looking to rent rooms, find apartments, buy properties, or sell their existing properties often rely on separate platforms, brokers, and intermediaries.

This fragmented ecosystem creates several problems:

- Difficulty finding reliable and skilled service professionals.
- Lack of transparent pricing and service quality.
- Time-consuming service discovery and booking.
- Limited access to verified professionals and contractors.
- Difficulty managing complete home renovation projects.
- Dependence on multiple platforms for home services and property transactions.
- Challenges finding suitable rental accommodations and tenants.
- Lack of a centralized solution for home maintenance and property management.

Door2DoorCare aims to address these problems by bringing home services, renovations, and property-related solutions together on a single digital platform.

## Product

Door2DoorCare is a web-based, all-in-one home services and property solutions platform designed for people living in metropolitan cities.

The application will connect customers with skilled professionals for plumbing, electrical work, carpentry, painting, appliance repairs, household maintenance, and complete flat renovations.

It will also allow users to discover, list, rent, buy, and sell residential properties, including individual rooms, flats, and apartments.

The long-term goal is to create a unified ecosystem where users can manage their everyday home and property requirements through a single platform.

## Target Users

- **Primary user:** Residents of metropolitan cities, including homeowners, tenants, working professionals, families, property buyers, and people seeking household repair, maintenance, or renovation services.
- **Secondary user:** Plumbers, electricians, carpenters, painters, appliance technicians, renovation contractors, interior designers, landlords, property owners, property sellers, and authorized real estate professionals.

## Core Use Cases

- **Use case 1:** Find and book professionals for plumbing, electrical work, carpentry, painting, appliance repairs, and other household maintenance services.
- **Use case 2:** Request quotations and hire contractors for partial or complete home renovation projects.
- **Use case 3:** Search for rooms, flats, apartments, and shared accommodations available for rent.
- **Use case 4:** Allow property owners to publish rental listings and connect with potential tenants.
- **Use case 5:** Search for residential properties available for purchase.
- **Use case 6:** Allow property owners to list residential properties for sale and receive inquiries.
- **Use case 7:** Discover service providers based on location, service category, and availability.
- **Use case 8:** View professional profiles, service descriptions, ratings, and customer reviews.
- **Use case 9:** Submit service requests, schedule appointments, and monitor booking status.
- **Use case 10:** Manage household maintenance requests and access previous service records.

## MVP Scope

The proposed initial MVP will focus on validating the core home services marketplace and basic property discovery workflows, with public browsing available without login.

- **Required capability 1:** User registration, login, and profile management for actions requiring authentication.
- **Required capability 2:** Role-based access for customers, service professionals, property owners, and administrators.
- **Required capability 3:** Public browsing of home service categories, professional listings, and approved public profile details without login.
- **Required capability 4:** Public browsing of rental and sale property listings, including approved photos, descriptions, amenities, prices, and approximate locations without login.
- **Required capability 5:** Guest-accessible search and filtering by city, locality, PIN code, service category, property type, and price.
- **Required capability 6:** Service professional profiles, availability, and publicly approved ratings and reviews.
- **Required capability 7:** Authenticated service request creation, booking management, and booking status tracking.
- **Required capability 8:** Service request acceptance, rejection, and status updates by authorized professionals.
- **Required capability 9:** Authenticated property listing creation, editing, and management by authorized owners.
- **Required capability 10:** Authenticated property inquiries and controlled owner contact workflows.
- **Required capability 11:** Administrative dashboard for managing users, professionals, services, and property listings.
- **Required capability 12:** Basic ratings, reviews, and service history with appropriate access controls.
- **Required capability 13:** Protect private phone numbers, email addresses, exact residential addresses, and other sensitive information from guest access unless specifically authorized for publication.
- **Required capability 14:** Restrict public API responses, rendered HTML, Server Component payloads, and metadata to approved public information; enforce access rules using authorization and Supabase RLS where applicable.
- **Required capability 15:** Require authentication only for protected actions, preserve the user's intended action through login, and maintain mobile-responsive, SEO-friendly public pages.

## Out of Scope

The following capabilities are proposed for later phases and will not be included in the initial MVP:

- Native Android and iOS applications.
- AI-powered service recommendations and automated matching.
- Advanced renovation project management and milestone tracking.
- Complete property transaction processing and legal documentation.
- Automated rental agreement generation.
- Advanced subscription and loyalty programs.
- Automated contractor bidding and tender management.
- Multi-country operations.
- Advanced analytics and predictive maintenance.

## Constraints

- **Platform:** Initially a web-based application.
- **Target Market:** Metropolitan cities, with location-based service availability.
- **Frontend:** Next.js 16, TypeScript, Tailwind CSS, shadcn/ui, and Radix UI.
- **Backend:** Next.js 16 Route Handlers and Server Actions using a full-stack monolithic architecture.
- **Database:** PostgreSQL, initially hosted by Supabase, with server-only TypeScript access through a limited PostgreSQL role. The host is configurable independently of Supabase Auth.
- **Communication:** REST APIs.
- **Deployment:** Vercel.
- **Security:** Authentication, authorization, input validation, secure data access, and PostgreSQL Row Level Security where applicable.
- **Privacy:** Customer addresses, contact details, and property information must be protected from unauthorized access.
- **Performance:** Responsive interfaces, optimized page loading, and efficient database queries.
- **Compatibility:** Support modern desktop and mobile browsers.
- **Scalability:** The architecture should support expansion into additional metropolitan cities without requiring a complete application rewrite.
- **Service Availability:** Services and property listings must be filtered according to supported locations.
- **Regulatory Compliance:** Property listings, professional verification, customer data processing, and transactions must follow applicable laws and regulations.

## Success Criteria

The proposed MVP will be considered successful when:

- Guests can browse and search services and property listings without logging in, while private information remains protected.
- Users can register, log in, and manage their profiles.
- Customers can discover relevant home services based on their location.
- Customers can submit service requests and track booking status.
- Service professionals can manage their profiles and respond to service requests.
- Property owners can create, update, and manage rental or sale listings.
- Users can search for properties and submit inquiries.
- Administrators can manage users, service categories, professionals, and property listings.
- Core user workflows pass automated unit, integration, and end-to-end tests.
- Authentication, authorization, public-data exposure, and database security checks pass.
- The application operates reliably on Vercel across supported desktop and mobile browsers.
- The system supports multiple metropolitan cities through configurable location data.

Quantitative targets for user acquisition, booking completion, response times, service reliability, and customer satisfaction will be finalized during MVP planning.
