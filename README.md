# Fruit Lovers Page

[![CI Workflow](https://github.com/bedrum/fruit-container/actions/workflows/ci.yml/badge.svg)](https://github.com/bedrum/fruit-container/actions)

A responsive, mobile-first Web showcase displaying fruit categories with dynamic layouts and responsive design breakpoints.

---

## 📌 Project Overview

**Fruit Lovers Page** is a clean, responsive single-page web application designed to highlight fruit selections through a modern layout. Built with standard semantic HTML5 and vanilla CSS3, the project utilizes viewport clamp functions, CSS flexbox, and media queries to adapt seamlessly across mobile, tablet, desktop, and large desktop screens.

---

## ✨ Key Features

- **Responsive Mobile-First Architecture:** Fluid adjustments across multiple device viewports.
- **Dynamic Breakpoints:**
  - **Mobile (< 520px):** Single-column flex layout with blue primary palette.
  - **Tablet (≥ 520px):** Multi-column flex layout with green theme and `#e0eafc` background.
  - **Desktop (≥ 760px):** Expanded layout with distinct purple accent `#540d6e` and warm peach background `#ffe5d9`.
  - **Large Desktop (≥ 910px):** High-density display layout with vibrant orange header `#ff9800` and light warm background `#fff3e0`.
- **Fluid Typography & Image Scaling:** Utilizes `clamp()` and `aspect-ratio` for smooth scaling without layout shift.
- **Semantic HTML5:** Built using standard web accessibility and structural tags (`<header>`, `<section>`, `<footer>`).

---

## 🛠️ Technology Stack

- **HTML5:** Semantic document structure.
- **CSS3:** Flexbox, CSS variables/clamp functions, custom media queries.
- **Node.js / HTMLHint:** HTML linting and code quality verification.
- **GitHub Actions:** Automated CI pipeline for linting and asset verification.

---

## 📁 Project Structure

```
fruit-container/
├── .github/
│   └── workflows/
│       └── ci.yml          # GitHub Actions CI workflow configuration
├── banner.jpg              # Main hero banner image
├── fruit-1.jpg             # Apple image asset
├── fruit-2.jpg             # Orange image asset
├── fruit-3.jpg             # Mango image asset
├── fruit-4.jpg             # Banana image asset
├── fruit-5.jpg             # Avocado image asset
├── index.html              # Main HTML entry point
├── style.css               # Mobile-first stylesheet
└── README.md               # Project documentation
```

---

## 🚀 Getting Started

### Prerequisites

No build tools or server dependencies are strictly required to view the webpage. To run code quality checks locally, ensure you have Node.js installed:

- **Node.js:** `>= 18.0.0` (optional, for local linting)

### Running Locally

1. **Clone the repository:**
   ```bash
   git clone https://github.com/bedrum/fruit-container.git
   cd fruit-container
   ```

2. **Open in Browser:**
   Simply open `index.html` in your web browser of choice, or run a local static web server:
   ```bash
   npx serve .
   # or using Python
   python3 -m http.server 8080
   ```

---

## 🧪 Testing and Linting

The project includes static analysis and asset reference validation:

1. **Lint HTML:**
   ```bash
   npx htmlhint index.html
   ```

2. **Verify Asset References:**
   ```bash
   python3 -c "
   import sys, pathlib, html.parser
   class Extractor(html.parser.HTMLParser):
       def __init__(self): super().__init__(); self.links = []
       def handle_starttag(self, tag, attrs):
           a = dict(attrs)
           if tag in ('img', 'link'): self.links.append(a.get('src') or a.get('href'))
   p = Extractor()
   with open('index.html') as f: p.feed(f.read())
   missing = [l for l in p.links if l and not pathlib.Path(l).exists()]
   if missing: print('Missing:', missing); sys.exit(1)
   print('All assets exist.')
   "
   ```

---

## ⚙️ CI/CD Pipeline

Automated checks are configured via GitHub Actions (`.github/workflows/ci.yml`). On every push or pull request to the `main`/`master` branch:
- HTML structure is validated with `htmlhint`.
- All local static asset paths (`src` and `href` attributes) are checked to guarantee no missing or broken assets exist.

---

## 👤 Author & License

- **Developer:** Mizan MiT
- **License:** Open source under standard repository rights.
