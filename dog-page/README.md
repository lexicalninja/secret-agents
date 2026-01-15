# Dog Picture Web Page

A simple, static HTML web page that displays a picture of a dog. Built with vanilla HTML and CSS, fully responsive, and WCAG 2.2 AAA compliant.

## Project Description

This is a single-page static website featuring a high-quality image of a golden retriever. The page demonstrates best practices for:
- Semantic HTML5 structure
- Responsive web design
- WCAG 2.2 AAA accessibility compliance
- Modern CSS with responsive breakpoints

## Image Source and License

**Image Source:** Unsplash  
**Image URL:** https://images.unsplash.com/photo-1552053831-71594a27632d  
**Photographer:** Chevanon Photography  
**License:** Unsplash License (free to use)  
**Direct Link:** https://unsplash.com/photos/a-golden-retriever-sitting-on-a-wooden-floor

The image is used under the Unsplash License, which allows free use for commercial and non-commercial purposes.

## Setup Instructions

### Local Development

1. **Clone or download** this repository
2. **Open the page** in a web browser:
   - Double-click `index.html`, or
   - Use a local HTTP server:
     ```bash
     # Using Python 3
     python -m http.server 8000
     
     # Using Node.js (with http-server)
     npx http-server
     ```
3. **View the page** at `http://localhost:8000` (or the port your server uses)

### File Structure

```
dog-page/
├── index.html          # Main HTML file
├── styles.css          # CSS stylesheet
├── README.md           # This file
└── ACCESSIBILITY.md    # Accessibility documentation
```

## Design Decisions

### Color Scheme
- **Background:** White (`#ffffff`) for maximum contrast and readability
- **Text:** Dark gray (`#1a1a1a`) for high contrast (16.8:1 ratio, AAA compliant)
- **Accent:** Blue (`#0066cc`) for focus indicators and skip link
- All color combinations meet WCAG 2.2 AAA standards (7:1 for normal text, 4.5:1 for large text)

### Typography
- **Font Family:** System font stack for optimal performance and native feel
- **Base Size:** 16px (1rem) for optimal readability
- **Heading:** 2.5rem (mobile) to 3rem (desktop) with proper hierarchy

### Layout
- **Container:** Max-width 1200px, centered
- **Spacing:** Responsive padding using rem units
- **Image:** Max-width 800px, centered, with rounded corners and subtle shadow

### Responsive Design
- **Mobile-first approach** with breakpoints at:
  - 320px (mobile)
  - 768px (tablet)
  - 1024px (desktop)
- All elements scale proportionally
- Text remains readable at 200% zoom

### Accessibility Features
- **Semantic HTML5** structure (header, main, figure, img)
- **Descriptive alt text** for images
- **Skip to main content** link for keyboard navigation
- **Focus indicators** with AAA compliant contrast
- **Proper heading hierarchy** (h1 only, appropriate for single-page site)
- **Language declaration** (`lang="en"`)

## Browser Compatibility

Tested and working in:
- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)

## Accessibility Compliance

This page meets **WCAG 2.2 AAA** standards:
- ✅ Color contrast ratios ≥ 7:1 for normal text
- ✅ Color contrast ratios ≥ 4.5:1 for large text
- ✅ Keyboard navigation with visible focus indicators
- ✅ Semantic HTML structure
- ✅ Descriptive alt text
- ✅ Text resizable up to 200% without loss of functionality
- ✅ No keyboard traps
- ✅ Proper heading hierarchy

See `ACCESSIBILITY.md` for detailed accessibility documentation.

## Performance

- **Image Loading:** Lazy loading enabled for better performance
- **File Size:** Minimal CSS and HTML
- **No External Dependencies:** Pure HTML/CSS, no frameworks
- **Optimized Image:** 1200px width, optimized quality

## License

This project code is available for use. The dog image is used under the Unsplash License.

## Development Notes

- Built with vanilla HTML5 and CSS3
- No JavaScript required
- Static site - no server-side processing needed
- Works with `file://` protocol or local HTTP server
