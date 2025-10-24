# Somani Fabric - B2B Fabric Distribution Platform

## Overview

Somani Fabric is a comprehensive B2B fabric distribution platform serving 500+ businesses across 15+ cities in India. The application specializes in three primary fabric categories: uniform fabrics, denim, and suiting/shirting materials. It functions as both a product catalog and lead generation system, enabling businesses to browse fabric collections, submit inquiries, and connect with the distribution network.

The platform prioritizes professional credibility while maintaining an accessible, e-commerce-inspired user experience. It targets corporate uniform suppliers, fashion brands, tailors, and garment manufacturers seeking reliable fabric sourcing.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture

**Framework**: React with TypeScript, using Vite as the build tool and development server.

**Routing**: Wouter for lightweight client-side routing. The application follows a multi-page structure with distinct routes for home, catalog, category pages (uniform, denim, suiting-shirting), network information, about, contact, and admin.

**State Management**: 
- **React Query (@tanstack/react-query)** for server state and API data fetching with built-in caching
- **Zustand** for client-side state (enquiry cart functionality with localStorage persistence)
- Local component state with React hooks for UI interactions

**UI Component System**: shadcn/ui ("new-york" style variant) providing pre-built, accessible components built on Radix UI primitives. The design system uses Tailwind CSS with custom HSL-based color tokens and CSS variables for theming.

**Design Philosophy**: Hybrid approach combining reference-based design (inspired by Shopify's catalog, Stripe's credibility, Notion's B2B aesthetic) with a custom design system. Typography uses Inter font family with systematic heading scales and consistent spacing based on Tailwind's spacing units.

**Theme Support**: Light/dark mode toggle with theme persistence in localStorage, controlled via React Context.

**Form Handling**: React Hook Form with Zod schema validation for type-safe form submissions across contact forms, quote requests, and sub-agent applications.

### Backend Architecture

**Server Framework**: Express.js running on Node.js with TypeScript support via tsx runtime.

**API Design**: RESTful endpoints serving JSON data. Current implementation uses static JSON files (`server/data/*.json`) for product catalog, testimonials, and city coverage data rather than database queries. This suggests the product catalog is curated/updated manually rather than user-generated.

**Data Storage Strategy**: 
- **Static Data**: Products, testimonials, and network cities stored in JSON files
- **Form Submissions**: In-memory storage (`MemStorage` class) for contact forms, quote requests, and sub-agent applications. This is intended for demonstration—production would require database persistence.

**Database Configuration**: Drizzle ORM configured with PostgreSQL dialect (`@neondatabase/serverless` driver), though not actively used in current codebase. Schema defined in `shared/schema.ts` using Zod for runtime validation. The database setup appears prepared for future implementation when persistence becomes necessary.

**Development Workflow**: Vite middleware mode integrates frontend and backend in development, with HMR support. Production build separates static assets (client) from server bundle (esbuild).

### Key Architectural Decisions

**Monorepo Structure with Shared Types**: The `shared/` directory contains Zod schemas that generate TypeScript types used by both client and server, ensuring type safety across the stack. This eliminates type mismatches between API contracts and reduces duplication.

**Static Data Approach**: Products and content are served from JSON files rather than a database. This was chosen because:
- Product catalog is manually curated by business owners
- Content updates are infrequent and controlled
- Eliminates database dependency for read-heavy operations
- Simplifies deployment and reduces infrastructure complexity

The tradeoff is that content updates require code deployments, which is acceptable given the B2B context where catalog changes are deliberate and reviewed.

**Enquiry System (Not Shopping Cart)**: Unlike e-commerce platforms, this doesn't process payments. The "enquiry drawer" collects product interests and generates WhatsApp messages for quote requests. This reflects the B2B sales model where pricing is negotiated rather than fixed.

**WhatsApp Integration**: Primary CTA for communication uses WhatsApp Web API with pre-formatted messages. This was chosen because:
- Common communication channel in Indian B2B markets
- Lower friction than email forms
- Enables immediate human interaction
- Familiar to target customer base

**Form Submission Without Backend Persistence**: Forms currently use in-memory storage, indicating the platform is in MVP/demo stage. The architecture anticipates database integration (Drizzle ORM setup exists) when scaling requirements emerge.

**API Route Separation**: Routes defined in `server/routes.ts` follow RESTful conventions with clear separation of concerns. Error handling uses try-catch with appropriate HTTP status codes.

### Design System Implementation

**Tailwind Configuration**: Custom theme extends default Tailwind with:
- Border radius customization (lg: 9px, md: 6px, sm: 3px)
- HSL-based color system with CSS variables enabling theme switching
- Extended color palette including card, popover, and sidebar variants
- Elevation utilities (`hover-elevate`, `active-elevate-2`) for interactive feedback

**Component Aliases**: Path aliases configured for clean imports:
- `@/` → client/src
- `@shared/` → shared schema definitions
- `@assets/` → attached_assets

**Responsive Design**: Mobile-first approach with breakpoints at md (768px) and lg (1024px). Navigation switches to hamburger menu on mobile, grid layouts adjust column counts responsively.

## External Dependencies

### Core Libraries
- **React 18+** with TypeScript for type-safe UI development
- **Vite** for fast development server and optimized production builds
- **Express.js** for backend API server
- **Wouter** for lightweight client-side routing

### UI & Styling
- **Tailwind CSS** for utility-first styling with PostCSS processing
- **shadcn/ui** component library built on Radix UI primitives
- **Radix UI** (@radix-ui/react-*) for accessible headless components
- **class-variance-authority** & **clsx** for conditional styling
- **Lucide React** for icon components

### Data & Forms
- **@tanstack/react-query** for server state management and API caching
- **React Hook Form** for performant form handling
- **Zod** for schema validation and type inference
- **@hookform/resolvers** for Zod integration with React Hook Form
- **Zustand** for client-side state management

### Database (Prepared but Not Active)
- **Drizzle ORM** with drizzle-zod for type-safe database access
- **@neondatabase/serverless** as PostgreSQL driver (Neon database platform)
- **connect-pg-simple** for PostgreSQL session storage (future use)

### Development Tools
- **tsx** for running TypeScript in Node.js
- **esbuild** for production server bundling
- **Replit plugins** (@replit/vite-plugin-*) for development environment integration

### Third-Party Integrations
- **WhatsApp Web API** (wa.me links) for business communication
- **Google Fonts CDN** (Inter font family)
- **Unsplash** image URLs for product imagery (placeholder content)

### Date & Utilities
- **date-fns** for date formatting and manipulation
- **nanoid** for generating unique identifiers
- **embla-carousel-react** for carousel/slider components
- **vaul** for drawer components
- **cmdk** for command menu interfaces
- **input-otp** for OTP input functionality
- **react-day-picker** for calendar/date picker
- **recharts** for data visualization (configured but not visibly used)