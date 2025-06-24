# Susanne Fortunato - Personal Website

A professional portfolio website for Susanne Fortunato, a healthcare technology leader and Director of Product Management.

## About

This is a static personal website showcasing Susanne's professional experience, work samples, and background in healthcare technology. The site highlights her achievements including:

- Leading product teams and scaling healthcare technology companies
- Successfully selling Wingspan Health to Curative in 2022
- Launching best-in-KLAS EMR systems for hospitals
- Building AI-driven healthcare solutions that impact millions of patients
- Creating HIPAA-compliant applications

## Site Structure

- **`index.html`** - Main homepage with professional introduction, career background, and contact information
- **`user-feedback.html`** - Page showcasing user testimonials and feedback
- **`what-to-read.html`** - Reading recommendations and resources
- **`links.html`** - Additional links and resources
- **`Resume-doc/`** - Resume documentation and related files

## Technologies Used

- **HTML5** - Semantic markup structure
- **CSS3** - Styling with Bootstrap framework
- **SCSS/Sass** - CSS preprocessing for maintainable stylesheets
- **Bootstrap 4** - Responsive grid system and components
- **jQuery** - JavaScript library for DOM manipulation
- **Font Awesome** - Icon library
- **Linearicons** - Additional icon set
- **Owl Carousel** - Image carousel functionality
- **Magnific Popup** - Lightbox for images and content

## Development Setup

### Prerequisites
- A web server or local development environment

### Local Development
1. Clone the repository
2. Serve the files using a local web server:
   ```bash
   # Using Python 3
   python -m http.server 8000
   
   # Using Node.js (if you have http-server installed)
   npx http-server
   
   # Using PHP
   php -S localhost:8000
   ```
3. Open `http://localhost:8000` in your browser

### SCSS Compilation
If you need to modify styles, the SCSS source files are in the `scss/` directory:
- `scss/main.scss` - Main stylesheet that imports all components
- `scss/theme/` - Custom theme components
- `scss/bootstrap/` - Bootstrap framework files

Compile SCSS to CSS using:
```bash
sass scss/main.scss css/main.css
```

## Deployment

This site is configured for GitHub Pages deployment with the custom domain `susannefortunato.com` (configured in `CNAME`).

## File Organization

```
├── index.html              # Main homepage
├── css/                    # Compiled CSS files
├── scss/                   # SCSS source files
├── js/                     # JavaScript files
├── img/                    # Images and assets
├── fonts/                  # Font files
├── Resume-doc/            # Resume documentation
├── favicon.png            # Main favicon (healthcare gradient)
├── favicon-*.png          # Favicon files in multiple sizes
├── apple-touch-icon.png   # iOS touch icon
└── CNAME                  # Custom domain configuration
```

## Recent Updates

### Career Updates (2024)
- Updated hero section to reflect current role as "Healthcare, Product & AI" leader
- Added Curative experience (Director of Product Management, 2022-Present)
- Updated Wingspan Health background to show successful acquisition by Curative
- Enhanced professional messaging to emphasize leadership and scaling experience

### Design Improvements
- Created and implemented custom healthcare gradient favicon
- Added favicon files in multiple sizes (16x16, 32x32, 48x48, 192x192, 512x512)
- Added Apple touch icon for iOS devices
- Updated all HTML files with proper favicon references

### Technical Improvements
- Fixed HTML syntax errors
- Validated all external links (GitHub, Twitter, LinkedIn)
- Confirmed responsive design implementation
- Tested cross-browser compatibility

## Responsive Design

The website is fully responsive with breakpoints for:
- **Mobile**: 320px - 767px
- **Tablet**: 768px - 991px  
- **Desktop**: 992px+
- **Large Desktop**: 1200px+

## Contact

For questions about this codebase or to get in touch with Susanne:
- Email: susanne.fortunato@gmail.com
- LinkedIn: [linkedin.com/in/sfortunato](https://www.linkedin.com/in/sfortunato)
- Twitter: [@scfortunato](https://twitter.com/scfortunato)
- GitHub: [github.com/sfortunato](https://github.com/sfortunato)