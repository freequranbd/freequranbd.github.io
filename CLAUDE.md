# FreeQuranBd Website

A professional, responsive, bilingual (Bangla/English) website for a Quran distribution organization in Bangladesh.

## Project Overview

**Purpose:** Provide a platform for requesting free Quran copies for schools, madrassas, and individual students across Bangladesh.

**Languages:** Bangla (default) and English with instant switching capability

**Target Audience:** Educational institutions, madrassas, and students in Bangladesh

## Technical Stack

- **HTML5** - Semantic markup
- **CSS3** - Custom styling with CSS variables, flexbox, and grid
- **Vanilla JavaScript** - Language switching and form handling
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
- **Color Contrast:** WCAG AA compliant colors

### 4. Performance
- **Flexbox Layout:** Sticky footer, no JavaScript needed for layout
- **Font Preconnect:** Faster font loading
- **CSS Variables:** Easy theming and maintenance
- **Minimal Dependencies:** No frameworks or libraries
- **Optimized Animations:** Smooth transitions with GPU acceleration

### 5. Form Functionality
- **Email Integration:** Uses `mailto:` to send requests to webadmin@outlook.com
- **Form Validation:** HTML5 required fields
- **Bilingual Labels:** All fields translated in both languages
- **Dropdown Options:** Organization type, language preference
- **Textarea Fields:** Address and detailed needs

### 6. Design Elements
- **Color Scheme:** 
  - Primary: #1a5f3f (Islamic green)
  - Secondary: #2d8659
  - Accent: #d4af37 (Gold)
- **Arabic Calligraphy:** Decorative Bismillah and Islamic symbols
- **Gradient Headers/Footers:** Professional appearance
- **Card Layouts:** Service offerings with hover effects
- **Smooth Animations:** Fade-in effects on page load

## File Structure

```
frequranbd.github.io/
├── index.html          # Main HTML file with bilingual content
├── styles.css          # All CSS styles and responsive design
├── CLAUDE.md          # This documentation file
└── README.md          # (Optional) Project readme
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
4. **Main Content** - Mission, services, form sections
5. **Footer** - Quote and contact information
6. **Responsive** - Media queries for all breakpoints
7. **Accessibility** - Focus states and skip links
8. **Print** - Optimized printing layout
9. **Animations** - Keyframes and transitions

### Layout Techniques
- **Flexbox:** Header, footer, language switcher, service cards
- **CSS Grid:** Services grid, form rows
- **Position Fixed:** Decorative calligraphy elements
- **Sticky Footer:** Flexbox on body element

## JavaScript Functionality

### Language Switching
```javascript
function switchLanguage(lang)
```
- Updates `data-lang` attribute on body
- Switches text content using data attributes
- Updates placeholders and options
- Saves preference to localStorage

### Form Handling
- Captures form data
- Formats email body
- Opens default email client with pre-filled content
- Shows success message in current language
- Resets form after submission

## Content Sections

1. **Header**
   - Language switcher (English/বাংলা)
   - Logo and organization name
   - Tagline

2. **Mission Statement**
   - Bismillah (Arabic)
   - Organization's mission and goals
   - Bilingual content

3. **Services**
   - Three service cards (Madrassas, Schools, Students)
   - Language availability badge
   - Hover effects

4. **Request Form**
   - Personal information (name, phone, email)
   - Organization details
   - Delivery address
   - Request specifics (quantity, language preference)
   - Additional details textarea
   - Submit button

5. **Footer**
   - Quranic quote (Surah Al-Isra 17:9)
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
- Two-column form rows
- Full decorative elements
- Larger typography

### Tablet (≤768px)
- Single-column service grid
- Single-column form
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
| Primary Green | #1a5f3f | Headers, buttons, links |
| Secondary Green | #2d8659 | Gradients, accents |
| Accent Gold | #d4af37 | Highlights, decorations |
| Text Dark | #2c3e50 | Primary text |
| Text Light | #6c757d | Secondary text |
| Background | #f8f9fa | Page background |
| White | #ffffff | Cards, buttons |
| Border | #e0e0e0 | Input borders, cards |

## Typography

- **Headings:** Poppins (600 weight)
- **Body Text (English):** Poppins (300, 400 weight)
- **Body Text (Bangla):** Noto Sans Bengali (400, 600 weight)
- **Arabic Text:** Amiri (400, 700 weight)

### Line Heights
- **English:** 1.6 (body), 1.8 (paragraphs)
- **Bangla:** 1.9 (body), 2.0 (paragraphs)
- **Arabic:** 1.6

## Form Fields

1. **Full Name** (required) - text input
2. **Phone Number** (required) - tel input
3. **Email Address** (optional) - email input
4. **Organization Type** (required) - select dropdown
   - Madrassa
   - School
   - Individual Student
   - Other
5. **Organization Name** (optional) - text input
6. **Complete Address** (required) - textarea
7. **Number of Copies** (required) - number input (1-500)
8. **Preferred Language** (required) - select dropdown
   - Bangla Translation
   - Bangla with Arabic
9. **Additional Details** (required) - textarea

## Email Template

The form generates a structured email with:
- Requester information
- Organization details
- Delivery address
- Request specifics
- Submission timestamp (Bangladesh Time)

**Recipient:** webadmin@outlook.com

## Customization Guide

### Changing Colors
Edit CSS variables in `styles.css`:
```css
:root {
    --primary-color: #1a5f3f;
    --secondary-color: #2d8659;
    --accent-color: #d4af37;
}
```

### Changing Fonts
Update Google Fonts link and CSS font-family declarations

### Adding New Languages
1. Add language button in HTML
2. Add `data-[lang-code]` attributes to elements
3. Update `switchLanguage()` function

### Modifying Form
- Edit form fields in HTML
- Update email template in JavaScript
- Adjust form validation as needed

## Future Enhancements

Potential features for future versions:
- [ ] Backend API integration for form submission
- [ ] Database storage of requests
- [ ] Admin dashboard for request management
- [ ] Email verification
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
- Email submission requires user's email client
- No server-side validation
- LocalStorage only (no cloud sync)
- Single-page design

## Testing Checklist

- [ ] Test on Chrome, Firefox, Safari, Edge
- [ ] Test on iOS and Android devices
- [ ] Test language switching
- [ ] Test form validation
- [ ] Test email submission
- [ ] Test responsive breakpoints
- [ ] Test keyboard navigation
- [ ] Test screen reader compatibility
- [ ] Test print layout
- [ ] Test with reduced motion enabled

## Contact & Support

**Organization:** FreeQuranBd  
**Email:** webadmin@outlook.com  
**Purpose:** Free Quran distribution in Bangladesh

---

**Built with:** Claude Code (Anthropic)  
**Version:** 1.0  
**Last Updated:** December 2024  
**License:** To be determined by organization
