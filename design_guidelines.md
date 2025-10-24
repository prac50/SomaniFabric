# Somani Fabric - Comprehensive Design Guidelines

## Design Approach

**Selected Approach:** Hybrid (Reference-Based + Design System)
- **Reference Inspiration:** Shopify (e-commerce catalog), Stripe (trust/credibility), Notion (clean B2B aesthetic)
- **Rationale:** B2B fabric distribution requires professional credibility while showcasing products effectively. The hybrid approach balances visual appeal for product presentation with utilitarian efficiency for catalog browsing.

## Core Design Elements

### Typography
**Font Family:** Inter (via Google Fonts CDN)
- **Headings:** 
  - H1: font-bold text-5xl md:text-6xl lg:text-7xl (Hero headlines)
  - H2: font-bold text-4xl md:text-5xl (Section titles)
  - H3: font-semibold text-2xl md:text-3xl (Subsections)
  - H4: font-semibold text-xl (Card titles)
- **Body:** font-normal text-base md:text-lg leading-relaxed
- **Small Text:** text-sm (labels, captions)
- **CTA Buttons:** font-semibold text-base

### Layout System
**Spacing Units:** Tailwind units of 4, 6, 8, 12, 16, 20, 24 for consistent rhythm
- Section padding: py-16 md:py-24 lg:py-32
- Card padding: p-6 md:p-8
- Container max-width: max-w-7xl mx-auto px-4 md:px-6

**Grid Systems:**
- Product catalog: grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6
- Feature highlights: grid-cols-1 md:grid-cols-3 gap-8
- Network cities: grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4

### Component Library

**Navigation:**
- Sticky header with logo (left), navigation links (center), WhatsApp + Request Quote CTA (right)
- Mobile: Hamburger menu with full-screen overlay
- Footer: 4-column grid (About, Quick Links, Product Categories, Contact Info) with newsletter signup

**Hero Sections:**
- Home: Full-width banner with fabric texture background image, headline, subheadline, dual CTAs (View Catalog + Request Quote), trust indicators below (e.g., "Serving 500+ Businesses | 15+ Cities")
- Category pages: Medium-height hero (60vh) with category-specific fabric imagery, breadcrumb navigation

**Product Cards:**
- Image (16:9 aspect ratio), fabric name, category tag, key specs (GSM, composition), "Add to Enquiry" button
- Hover: Subtle scale (scale-105) and shadow elevation
- Badge for "New Arrival" or "Popular"

**Trust Elements:**
- Stats section: 4-column grid showing "Years in Business," "Cities Covered," "Happy Clients," "Fabric Variants"
- Testimonial cards: Quote, company name, industry, city (no photos needed)
- Partner/Client logo grid: 6-8 logos in grayscale

**Forms:**
- Consistent input styling: border-2, rounded-lg, p-4, focus ring in accent color
- Labels above inputs with required asterisks
- Submit buttons: full-width on mobile, auto-width on desktop
- Success/error states with inline validation

**Interactive Elements:**
- Floating WhatsApp button: Fixed bottom-right, rounded-full with icon, green background with blur backdrop
- Request Quote modal: Centered overlay with backdrop blur, form fields, close button
- Enquiry drawer: Slide-in from right, shows selected items, "Send via WhatsApp" CTA
- Search & filters: Sticky filter bar on catalog page with dropdowns for category, fabric type, GSM range

**Data Display:**
- How We Work: 4-step process with numbered icons, title, description in vertical cards
- Network coverage: City cards with location icon, city name, "Coverage areas" list, "Contact Local Agent" button
- FAQ accordion: Question header with chevron icon, expandable answer panel

## Page-Specific Layouts

**Home Page Structure:**
1. Hero with fabric imagery + dual CTAs
2. Trust stats (4-column grid)
3. Product niches (3 large cards: Uniform, Denim, Suiting-Shirting with imagery + description)
4. How We Work (4-step process)
5. Testimonials (2-column grid)
6. Network coverage map/city highlights
7. CTA section: "Ready to Transform Your Business?" with form + WhatsApp option

**Catalog Page:**
- Sticky search/filter bar at top
- Product grid with sidebar filters (desktop) or top filters (mobile)
- Pagination at bottom
- "Download PDF Line Sheet" button prominently placed

**Category Pages (Uniform/Denim/Suiting):**
- Hero with category image
- Category description + USPs (2-column layout)
- Featured products from category
- FAQ accordion
- "View Full Catalog" + "Request Sample" CTAs

**Network Page:**
- Map visualization (decorative) showing coverage
- City grid with search functionality
- "Become a Sub-Agent" section with benefits list + application form

**About Page:**
- Founder story with professional photo (side-by-side layout)
- Company values (icon + text cards)
- Timeline of growth milestones
- Team section (if applicable)

**Contact Page:**
- 2-column split: Lead form (left) + Contact information with office hours, WhatsApp link, email (right)
- Embedded location indicators for major offices

## Images

**Hero Images:**
- Home: High-quality fabric rolls/texture close-up (colorful, professional)
- Uniform page: Professional uniforms in workplace setting
- Denim page: Denim fabric texture or jeans manufacturing
- Suiting-Shirting page: Formal fabrics, suits display

**Supporting Images:**
- Product catalog: Individual fabric swatches/samples (consistent white background, professional lighting)
- How We Work: Icon illustrations (no photos needed)
- About page: Founder professional headshot, office/warehouse photos
- Network page: Map graphic (decorative, simplified India map)

## Animations
Minimal, purposeful animations only:
- Fade-in on scroll for sections (subtle, once)
- Button hover states (scale, shadow)
- Card hover effects (elevation change)
- Smooth scroll for anchor links
- Modal/drawer slide transitions

## Accessibility
- Semantic HTML structure
- ARIA labels for interactive elements
- Keyboard navigation support
- Focus states with visible outlines
- Alt text for all images
- Color contrast meeting WCAG AA standards
- Form labels and error messages

This design system creates a professional, trustworthy B2B platform that emphasizes credibility, ease of product discovery, and seamless inquiry generation while maintaining visual appeal appropriate for the fabric industry.