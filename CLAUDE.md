# FreeQuranBd Website

A professional, responsive, bilingual (Bangla/English) website for a Quran distribution organization in Bangladesh.

## Project Overview

**Purpose:** Provide a platform for requesting free Quran copies for schools, madrassas, and individual students across Bangladesh.

**Languages:** Bangla (default) and English with instant switching capability

**Target Audience:** Educational institutions, madrassas, and students in Bangladesh

## Technical Stack

- **HTML5** - Semantic markup
- **CSS3** - Custom styling with CSS variables, flexbox, and grid
- **Vanilla JavaScript** - Language switching and analytics event tracking
- **Google Fonts** - Amiri (Arabic), Noto Sans Bengali, Poppins

## Features

### 1. Bilingual Support
- **Default Language:** Bangla
- **Language Switching:** Instant toggle between Bangla and English
- **LocalStorage:** Saves user's language preference
- **Font Optimization:** Noto Sans Bengali for Bangla, Poppins for English

### 2. Responsive Design
- **Desktop:** Full-featured layout with decorative elements
- **Tablet (≤768px):** Optimized spacing and reduced decorations
- **Mobile (≤480px):** Touch-friendly interface, simplified layout
- **Breakpoints:** 768px, 480px

### 3. Accessibility
- **Skip Navigation:** Skip to main content link for keyboard users
- **Focus States:** Clear outlines on all interactive elements
- **Reduced Motion:** Respects `prefers-reduced-motion` preference
- **Semantic HTML:** Proper heading hierarchy and ARIA support
- **ARIA Labels:** `role="img"` and `aria-label` on emoji icons
- **Color Contrast:** WCAG AA compliant colors

### 4. Performance
- **Flexbox Layout:** Sticky footer, no JavaScript needed for layout
- **Font Preconnect & Preload:** Faster font loading with non-blocking stylesheet preload pattern
- **CSS Variables:** Easy theming and maintenance
- **Minimal Dependencies:** No frameworks or libraries
- **Pure-CSS Background Pattern:** Subtle radial-gradient dot pattern — no image bytes, GPU-composited
- **LCP Hints:** Logo image uses `fetchpriority="high"` and `decoding="async"`
- **Optimized Animations:** Smooth transitions with GPU acceleration

### 5. Email Request Flow
- **Direct Email CTA:** Request section contains a bilingual call to action and a `mailto:freequranbd@gmail.com?subject=Free%20Quran%20Request` link
- **GA4 Analytics:** Tracks language switches and email clicks (`email_type: request_primary` for the request CTA, `contact_footer` for the footer link) via `gtag()`
- **No Form Layer:** No HTML form, validation, or JavaScript form handling — requests go straight through the user's email client to minimize friction and avoid backend dependencies
- **Bilingual CTA Copy:** Request instruction and email link rendered in the active language

### 6. Design Elements
- **Color Scheme:**
  - Primary: #000000 (Black)
  - Secondary: #1a1a1a
  - Accent: #ffffff (White)
- **Arabic Calligraphy:** Decorative Bismillah and Islamic symbols
- **Gradient Headers/Footers:** Professional appearance
- **Card Layouts:** Service offerings with hover effects
- **Smooth Animations:** Fade-in effects on page load

## File Structure

```
freequranbd.com/
├── index.html          # Main HTML file with bilingual content
├── styles.css          # All CSS styles and responsive design
├── sitemap.xml         # XML sitemap for search engines
├── robots.txt          # Crawler directives
├── CLAUDE.md           # This documentation file
└── README.md           # (Optional) Project readme
```

## CSS Architecture

### Variables
- Color palette defined in `:root`
- Shadows, borders, and spacing standardized
- Easy theme customization

### Sections
1. **Reset & Base Styles** - Normalize and defaults
2. **Decorative Elements** - Arabic calligraphy positioning
3. **Header** - Logo, language switcher, tagline
4. **Navigation** - Anchor links to page sections
5. **Main Content** - Mission, services, request (email CTA) sections
6. **Footer** - Quote and contact information
7. **Responsive** - Media queries for all breakpoints
8. **Accessibility** - Focus states and skip links
9. **Print** - Optimized printing layout
10. **Animations** - Keyframes and transitions

### Layout Techniques
- **Flexbox:** Header, footer, language switcher, service cards
- **CSS Grid:** Services grid
- **Position Fixed:** Decorative calligraphy elements
- **Sticky Footer:** Flexbox on body element

## JavaScript Functionality

### Language Switching

Two functions split by intent:

```javascript
function applyLanguage(lang)  // pure DOM mutation, no side effects
function switchLanguage(lang) // applyLanguage + localStorage + GA4 event
```

- `applyLanguage()` updates the `data-lang` attribute on `<body>`, toggles the active button, and swaps `textContent` / `placeholder` from `data-en` / `data-bn` attributes. Used for restoring saved preferences on load.
- `switchLanguage()` wraps `applyLanguage()` and adds the persistent side effects (localStorage save + `language_switch` GA4 event). Only called from button click handlers.
- On first visit, no JS work is needed — the HTML ships with Bangla as the default. Saved preference is only re-applied when it differs from the default.

### Email Click Tracking
- `mailto:` links in the Request section and footer have inline `onclick` handlers that fire `gtag('event', 'email_click', { email_type })` so GA4 can distinguish the two call-to-action paths.

## Content Sections

1. **Header**
   - Language switcher (English/বাংলা)
   - Logo and organization name
   - Tagline

2. **Navigation**
   - Anchor links to Mission, Services, Request sections
   - Hidden in print layout

3. **Mission Statement**
   - Bismillah (Arabic)
   - Organization's mission and goals
   - Bilingual content

4. **Services**
   - Three service cards (Madrassas, Schools, Students)
   - ARIA-labeled emoji icons
   - Hover effects

5. **Request Section**
   - Bilingual heading and divider
   - Short bilingual instruction prompting the visitor to email
   - `mailto:` link to `freequranbd@gmail.com` with `subject=Free Quran Request` prefilled
   - GA4 `email_click` event (`email_type: request_primary`) on click

6. **Footer**
   - Quranic quote (Surah Al-'Alaq 96:1)
   - Translation in both languages
   - Copyright and contact information

## Browser Support

- **Modern Browsers:** Chrome, Firefox, Safari, Edge (latest versions)
- **Mobile Browsers:** iOS Safari, Chrome Mobile, Samsung Internet
- **Features Used:** CSS Grid, Flexbox, CSS Variables, LocalStorage
- **Fallbacks:** Graceful degradation for older browsers

## Responsive Breakpoints

### Desktop (>768px)
- Three-column service grid
- Full decorative elements
- Larger typography

### Tablet (≤768px)
- Single-column service grid
- Reduced decorations (opacity 0.05)
- Medium typography

### Mobile (≤480px)
- Compact spacing
- Smaller buttons and inputs
- Hidden decorative elements
- Optimized touch targets (44px minimum)

## Color Palette

| Color | Hex | Usage |
|-------|-----|-------|
| Primary Black | #000000 | Headers, buttons, links |
| Secondary Dark | #1a1a1a | Gradients, nav |
| Accent White | #ffffff | Highlights, text on dark |
| Text Dark | #000000 | Primary text |
| Text Light | #666666 | Secondary text |
| Background | #ffffff | Page background |
| White | #ffffff | Cards, buttons |
| Border | #d0d0d0 | Input borders, cards |

## Typography

- **Headings:** Poppins (600 weight)
- **Body Text (English):** Poppins (300, 400 weight)
- **Body Text (Bangla):** Noto Sans Bengali (400, 600 weight)
- **Arabic Text:** Amiri (400, 700 weight)

### Line Heights
- **English:** 1.6 (body), 1.8 (paragraphs)
- **Bangla:** 1.9 (body), 2.0 (paragraphs)
- **Arabic:** 1.6

## Request Submission

Requests are submitted by email rather than through an on-page form. The Request section presents a single `mailto:` link with a pre-filled subject line; the user's mail client opens for them to fill in details. Suggested contents (communicated to users via the FAQ schema and homepage copy):

- Full name and phone number
- Delivery address (district, division)
- Number of copies needed
- Preferred edition (Bangla translation, or Arabic with Bangla)
- Organization name and type (madrassa / school / individual / other), if applicable

**Recipient:** freequranbd@gmail.com

## Customization Guide

### Changing Colors
Edit CSS variables in `styles.css`:
```css
:root {
    --primary-color: #000000;
    --secondary-color: #1a1a1a;
    --accent-color: #ffffff;
}
```

### Changing Fonts
Update Google Fonts link and CSS font-family declarations

### Adding New Languages
1. Add language button in HTML
2. Add `data-[lang-code]` attributes to elements
3. Update `switchLanguage()` function

### Modifying the Request CTA
- Edit the bilingual instruction text and `mailto:` `href` in the `#request` section of `index.html`
- If changing the recipient address, also update the footer contact link, the JSON-LD `Organization.contactPoint.email`, the FAQ schema answers, and the meta descriptions

## Future Enhancements

Potential features for future versions:
- [ ] Reintroduce an on-page request form backed by a serverless endpoint (Formspree, Cloudflare Worker, etc.)
- [ ] Database storage of requests
- [ ] Admin dashboard for request management
- [ ] SMS notifications
- [ ] Request tracking system
- [ ] Gallery of distribution events
- [ ] Donation section
- [ ] Multiple language support (Urdu, Arabic)
- [ ] Dark mode toggle

## Development Notes

### Best Practices Followed
- ✅ Semantic HTML5
- ✅ Mobile-first approach
- ✅ Progressive enhancement
- ✅ Accessibility standards (WCAG 2.1)
- ✅ Clean, maintainable code
- ✅ Commented CSS sections
- ✅ Consistent naming conventions
- ✅ Cross-browser compatibility

### Known Limitations
- Request submission depends on the visitor having a configured email client (or being able to copy the address)
- No backend, so no server-side request capture, deduplication, or analytics beyond GA4 click events
- LocalStorage only (no cloud sync of language preference)
- Single-page design

## Testing Checklist

- [ ] Test on Chrome, Firefox, Safari, Edge
- [ ] Test on iOS and Android devices
- [ ] Test language switching (both directions; verify localStorage persistence)
- [ ] Verify GA4 `language_switch` event fires only on user click, not on page load
- [ ] Test the `mailto:` request link opens the email client with prefilled subject
- [ ] Verify GA4 `email_click` events fire for both the request CTA and footer link
- [ ] Test responsive breakpoints (768px, 480px)
- [ ] Test keyboard navigation and skip-to-main link
- [ ] Test screen reader compatibility
- [ ] Test print layout
- [ ] Test with reduced motion enabled
- [ ] Validate all JSON-LD blocks parse (Organization, WebSite, BreadcrumbList, FAQPage)

## Contact & Support

**Organization:** FreeQuranBd  
**Email:** freequranbd@gmail.com  
**Purpose:** Free Quran distribution in Bangladesh

---

**Domain:** https://freequranbd.com
**Built with:** Claude Code (Anthropic)
**Version:** 2.1
**Last Updated:** May 2026
**License:** To be determined by organization

## SEO

- **Structured Data:** Organization, WebSite, BreadcrumbList, FAQPage schemas (JSON-LD)
- **Meta Tags:** Open Graph, Twitter Card, geo tags, canonical URL
- **Sitemap:** `sitemap.xml` with hreflang alternate links
- **Robots:** `robots.txt` with sitemap reference
- **Analytics:** Google Analytics 4 (GA4) with custom event tracking
- **Google Search Console:** Verification meta tag configured
- **Favicon:** `favicon.ico` and `apple-touch-icon.png` references
- **Default Content Language:** Bangla (matches `<html lang="bn">`)
