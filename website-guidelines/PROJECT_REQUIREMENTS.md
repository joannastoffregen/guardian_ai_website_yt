# Project Requirements — Guardian AI Landing Page

## 1. Project Overview

**What:** Guardian AI is a security-focused SaaS platform delivering real-time threat detection, automated defense mechanisms, and developer-first observability tools.

**Who:** Primary target users include developers, DevOps & SRE teams, security engineers, compliance teams, tech founders, and mid-to-large organizations evaluating SOC2-ready platforms.

**Goal:** Build trust, show technical credibility, and highlight ease of integration. Enable users to sign up and explore product documentation, converting curious visitors into users.

**Performance:** The website must load blazing fast and be fully responsive across desktop, mobile, and tablet.

---

## 2. Tech Stack

| Technology | Purpose |
|------------|---------|
| **Next.js** | React framework with App Router, server-side rendering, and font optimization |
| **React** | UI component library |
| **TypeScript** | Type-safe JavaScript |
| **Tailwind CSS** | Utility-first CSS framework |
| **Three.js** | 3D graphics for hero section guardian angel model |
| **Framer Motion** | Animation library for entrance effects and transitions |
| **Motion** | Animation utilities (used in GlowingEffect component) |
| **Lucide React** | Icon library |
| **clsx** + **tailwind-merge** | Utility for conditional class names |

---

## 3. Dependencies

### Core Framework
- `next`
- `react`
- `react-dom`
- `typescript`

### Styling
- `tailwindcss`
- `postcss`
- `autoprefixer`
- `clsx`
- `tailwind-merge`

### 3D Graphics
- `three`
- `@react-three/fiber` (optional, for React integration)
- `@react-three/drei` (optional, for helpers)

### Animation
- `framer-motion`
- `motion` (or `@motionone/react`)

### Icons
- `lucide-react`

### Fonts
- Satoshi (local font files)
- Instrument Serif (via Google Fonts via Next.js)

---

## 4. Design System

All visual design decisions, component patterns, color system, typography, spacing, and animation guidelines are documented in **[STYLE_GUIDE.md](./STYLE_GUIDE.md)**.

**Key Design Principles:**
- Dark-first aesthetic (#0a0a0a backgrounds)
- Primary cyan accent (#01FFFF) for text accents and glows
- Orange accent (#ffa260) for subtle glows only (never text)
- Premium, technical, minimal aesthetic
- High contrast for readability

---

## 5. Page Sections

| # | Section | Description | Spec File |
|---|---------|-------------|-----------|
| 1 | Navigation Bar | Fixed header with logo, links (Features, Pricing, Docs), and Sign Up CTA | [1.navigation-bar.md](../website-sections/1.navigation-bar.md) |
| 2 | Hero Section | Centered headline with 3D guardian angel model, CTAs (Get Started, View Docs) | [2.hero-section.md](../website-sections/2.hero-section.md) |
| 3 | Trust Logos | Marquee of company logos with fade edges | [3.trust-logos-section.md](../website-sections/3.trust-logos-section.md) |
| 4 | Features | Bento grid layout with 7 feature cards, each with mini UI mock | [4.features-section.md](../website-sections/4.features-section.md) |
| 5 | How It Works | 3-step process (Connect, Analyze, Protect) with visual cards | [5.how-it-works-section.md](../website-sections/5.how-it-works-section.md) |
| 6 | Core Capabilities | Grid of 6 capability items with icons | [6.core-capabilities-section.md](../website-sections/6.core-capabilities-section.md) |
| 7 | Pricing | 3-tier pricing cards (Starter, Pro, Enterprise) with "Most Popular" highlight | [7.pricing-section.md](../website-sections/7.pricing-section.md) |
| 8 | Testimonials | Large quote with author info, highlight pills, and stats bar | [8.testimonials-section.md](../website-sections/8.testimonials-section.md) |
| 9 | FAQ | Collapsible accordion with 6 questions | [9.faq-section.md](../website-sections/9.faq-section.md) |
| 10 | Footer | Multi-column layout with logo, nav links, social icons, copyright | [10.footer-section.md](../website-sections/10.footer-section.md) |

---

## 6. File Structure

```
/
├── app/                          # Next.js App Router
│   ├── layout.tsx                # Root layout with fonts
│   ├── page.tsx                  # Landing page
│   └── globals.css               # Global styles + Tailwind
├── components/
│   ├── ui/                       # Reusable UI components
│   │   ├── star-button.tsx       # Primary CTA button
│   │   └── glowing-effect.tsx   # Card hover glow effect
│   ├── sections/                 # Page sections
│   │   ├── NavigationBar.tsx
│   │   ├── HeroSection.tsx
│   │   ├── TrustLogos.tsx
│   │   ├── FeaturesSection.tsx
│   │   ├── HowItWorks.tsx
│   │   ├── CoreCapabilities.tsx
│   │   ├── PricingSection.tsx
│   │   ├── Testimonials.tsx
│   │   ├── FAQ.tsx
│   │   └── Footer.tsx
│   └── hero/                     # Hero-specific components
│       └── GuardianModel.tsx     # Three.js 3D model
├── lib/
│   └── utils.ts                  # cn() utility function
├── public/
│   ├── fonts/                    # Satoshi font files
│   │   ├── Satoshi-Regular.woff2
│   │   ├── Satoshi-Medium.woff2
│   │   └── Satoshi-Bold.woff2
│   └── models/                   # 3D model files
│       └── Lucy100k.ply          # Guardian angel model
├── website-guidelines/            # Documentation
│   ├── product-brief.md
│   ├── STYLE_GUIDE.md
│   ├── PROJECT_REQUIREMENTS.md
│   └── tasks.md
└── website-sections/             # Section specifications
    └── [section files]
```

---

## 7. Responsive Requirements

| Breakpoint | Value | Target Device |
|------------|-------|---------------|
| `sm` | 640px | Large phones |
| `md` | 768px | Tablets |
| `lg` | 1024px | Laptops |
| `xl` | 1280px | Desktops |
| `2xl` | 1400px | Large screens |

**Container Max Width:** 1400px (2xl)

**Section Padding:**
- Vertical: 96px (py-24) on desktop
- Horizontal: 16px mobile, 32px tablet+

**Mobile-First Approach:** All layouts should be designed mobile-first with progressive enhancement for larger screens.

---

## Notes

- **Setup Steps:** See [tasks.md](./tasks.md) for implementation tasks and setup instructions.
- **Design Decisions:** Section-specific design notes are in individual section files. Reusable patterns are documented in STYLE_GUIDE.md.
- **Component Reuse:** StarButton and GlowingEffect components are shared across multiple sections.

