# Copilot Instructions for Milestones Academy

## Project Overview
Milestones Academy is a fully responsive website for a local daycare center. It's a static HTML/CSS website with minimal JavaScript, built with Bootstrap 5 and featuring interactive elements like image carousels, a Mapbox-integrated map, and a Netlify form.

**Live Site:** https://milestonesacademykaty.com

## Technology Stack
- **HTML5** with semantic structure
- **Bootstrap 5.3.3** for responsive layout and components
- **CSS3** with custom animations and media queries
- **Mapbox GL JS v2.9.1** for the interactive location map
- **Netlify** for form handling (data-netlify="true")
- **CDN-hosted dependencies** (no build process or package manager)

## Architecture & Key Sections

The site is a single-page application organized into distinct sections (accessible via navbar links):

1. **Navbar** - Fixed header with phone info bar, logo, social media icons (Facebook, Instagram, Email)
2. **Banner** - Hero section with animated title and background image
3. **About** - Two-column layout: text content + image carousel (25 images of children/activities)
4. **Programs** - Three program cards (Nursery/Infant, Toddler, Preschool) with custom background colors
5. **Facilities** - Two-column layout: facilities carousel (11 images) + descriptive text
6. **Curriculum** - Educational approach and enrichment activities description
7. **FAQ** - Accordion-style Q&A section (Curriculum section continues with this)
8. **Contact & Map** - Contact info list + Mapbox map centered on Katy, TX location
9. **Footer** - Copyright and developer credit
10. **Modal** - Enrollment form triggered by multiple CTA buttons throughout the site

## Key Conventions & Patterns

### Colors
- **Primary Blue**: `#22aee1` (navbar, banner borders, facilities section background)
- **Secondary Red**: `rgba(243, 53, 5, 0.875)` (phone number button, toddler card)
- **Accent Yellow**: `rgba(243, 164, 5, 0.875)` (preschool card)
- Dark backgrounds use Bootstrap's `bg-dark` class

### Images
- All images in `/img/` directory
- Social media icons in `/icons/` directory
- Use `loading="lazy"` attribute for performance on all images
- Carousel images follow naming: `kids0.jpg`–`kids24.jpg` (about section), `facility(1).jpg`–`facility(11).jpg` (facilities section)

### Layout & Responsiveness
- Mobile-first approach using Bootstrap grid (`col-md`, `col-lg`)
- Media queries in CSS for screens ≤768px and ≤466px
- Fixed navbar with `position: fixed` and `top: 0`
- Padded body with `body::before` pseudo-element (height: 100px) to account for fixed navbar
- Use `clamp()` for fluid spacing that adapts between breakpoints

### Animations
- **Fade-in-up animation** (`.fadeInUp`): Used on banner text with 2.5s duration
- **Bounce animation** (`.bounce-animation`): Applied to social media icons on hover
- All animations defined in CSS with smooth `cubic-bezier` easing

### Forms
- Enrollment modal uses Netlify form handling (`data-netlify="true"`)
- Form element: `<form name="contact" action="POST" data-netlify="true">`
- Fields: first-name, last-name, email, phone (all in form inputs with `name` attributes)
- Triggered by buttons with `data-bs-toggle="modal" data-bs-target="#enroll"`

### Maps
- Mapbox integration with access token (stored in inline `<script>`)
- Map container ID: `map`
- Default center: `[-95.811570, 29.806277]` (Katy, TX)
- Default zoom: 14
- Style: `mapbox://styles/mapbox/streets-v11`

## File Structure
```
/
├── index.html          # Main page (557 lines) - all content in single file
├── style.css           # Custom styles (257 lines)
├── README.md           # Project overview
├── img/                # Images (logo, banners, kids photos, facility photos)
├── icons/              # Social media and program icons
└── .github/
    └── copilot-instructions.md  # This file
```

## No Build/Test/Lint Commands
This is a static site with no build process, package manager, or automated tests. Changes can be tested by opening `index.html` directly in a browser or deploying to Netlify.

## Common Tasks

**Update program descriptions:** Edit the three card contents in the Programs section (each with class `card-text`)

**Add carousel images:** 
- For About section: add `<div class="carousel-item">` with `img src="img/kidsN.jpg"` 
- For Facilities section: follow same pattern in `#facilitiesCarousel`
- Always add corresponding `<button>` in `carousel-indicators`

**Modify colors:** Update hex values in CSS (search for color values like `#22aee1`)

**Update contact info:** Edit the Contact Info list at the bottom (look for `Contact Info` heading)

**Modify Mapbox map:** Change `center` coordinates or `zoom` level in the inline map script
