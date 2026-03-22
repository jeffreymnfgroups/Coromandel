# Coromandel Branding Solutions

A fully responsive, single-page marketing agency website for **Coromandel Branding Solutions** — based in Pondichery, Tamil Nadu. We specialize in building a Local Visibility System that helps local businesses get found, earn trust, and capture more enquiries every single day. 

Designed with a clean, professional aesthetic and a smooth user experience across all devices.

---

## 🛠️ Built With

| Technology | Purpose |
|---|---|
| [Vue 3](https://vuejs.org/) (Composition API) | UI framework & component architecture |
| [Vite](https://vitejs.dev/) | Build tool & dev server |
| [Vue Router](https://router.vuejs.org/) | Single-page anchor link routing |
| CSS3 with Custom Properties | Design system & theming |
| Intersection Observer API | Scroll-triggered animations |

---

## ✨ Features

- **Single-page application** — Seamless navigation across different sections using Vue Router with anchor links and smooth scrolling
- **Professional aesthetic** — Custom CSS property design system tailored for branding services
- **Scroll animations** — Fade-in and slide-up transitions on sections using the native Intersection Observer API
- **Fully responsive** — Mobile-first layout optimized for all screen sizes and devices
- **Service & Portfolio display** — Easily maintainable grid systems for showcasing services like Google Business Profile Optimization, Review Growth, and Local SEO
- **Reusable component system** — Modular architecture using intuitive Vue components for easy scaling and updates
- **Dynamic copyright year** — Computed property keeps the footer year always current

---

## 📁 Project Structure

```text
src/
├── assets/
│   ├── main.css               # Global CSS variables, reset, utilities, animations
│   └── *.webp                 # Local optimized images
├── components/
│   ├── NavBar.vue             # Sticky nav with hamburger menu & anchor links
│   ├── HeroSection.vue        # Full-viewport hero
│   ├── ServicesSection.vue    # Service grid
│   ├── AboutSection.vue       # Two-column layout with stats row & photo grid
│   ├── PortfolioSection.vue   # Filterable 6-project grid
│   ├── TestimonialsSection.vue # 3-card testimonial layout
│   ├── ContactSection.vue     # Two-column contact form with validation
│   ├── FooterSection.vue      # 4-column footer with dynamic year
│   ├── PageHero.vue           # Reusable page banner
│   └── CtaBanner.vue          # Reusable CTA box
├── router/
│   └── index.js               # Vue Router config with anchor hash navigation
├── views/
│   └── HomeView.vue           # Main view combining all sections
├── App.vue                    # Root: NavBar + RouterView + FooterSection
└── main.js                    # App entry — mounts Vue with router + global CSS
```

---

## 🚀 Getting Started

### Prerequisites

- Node.js `^20.19.0` or `>=22.12.0`
- npm

### Installation

```bash
# Clone the repository
git clone <repository-url>
cd lumen-agency-main # or whatever your directory is named

# Install dependencies
npm install

# Start local development server
npm run dev
```

The dev server will be available at `http://localhost:5173`.

### Build for Production

```bash
npm run build
```

Output is generated in the `dist/` folder.

### Preview Production Build

```bash
npm run preview
```

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
