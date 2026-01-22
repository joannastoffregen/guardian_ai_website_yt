# Guardian AI Website Boilerplate

> **Complete documentation and design system for building a modern, premium SaaS landing page**

This repository contains all the documentation, design guidelines, and specifications needed to build a stunning landing page for Guardian AI (or adapt it for your own project). Perfect for following along with the YouTube tutorial or using as a reference for your own website builds.

## 📺 YouTube Tutorial

**[Watch the full tutorial here](https://youtube.com)** *(Link to be added)*

Follow along step-by-step as we build a modern, dark-themed SaaS landing page with:
- Next.js 14 + TypeScript
- Tailwind CSS
- Three.js 3D graphics
- Framer Motion animations
- Premium design system

## 🎯 What's Included

This boilerplate provides everything you need to build the website:

### 📋 Documentation Structure

```
├── website-guidelines/          # Core design system & requirements
│   ├── STYLE_GUIDE.md          # Complete design system (colors, typography, components)
│   ├── PROJECT_REQUIREMENTS.md # Tech stack, dependencies, architecture
│   ├── product-brief.md        # Product overview and goals
│   └── tasks.md                # Implementation checklist
│
├── website-sections/            # Detailed section specifications
│   ├── 0.design-general-vibe.md    # Overall aesthetic & inspiration
│   ├── 1.navigation-bar.md         # Navigation component specs
│   ├── 2.hero-section.md           # Hero with 3D model specs
│   ├── 3.trust-logos-section.md    # Trust logos marquee
│   ├── 4.features-section.md       # Features bento grid
│   ├── 5.how-it-works-section.md   # How it works section
│   ├── 6.core-capabilities-section.md
│   ├── 7.pricing-section.md
│   ├── 8.testimonials-section.md
│   ├── 9.faq-section.md
│   ├── 10.footer-section.md
│   └── inspo-images/               # Design inspiration images
│
└── .cursor/rules/              # AI assistant rules for development
    └── style-guide-governance.mdc
```

## 🚀 How to Use This Boilerplate

### Option 1: Follow Along with the Tutorial

1. **Watch the YouTube video** to see the implementation process
2. **Reference the documentation** as you build:
   - Start with `website-guidelines/PROJECT_REQUIREMENTS.md` for setup
   - Use `website-guidelines/STYLE_GUIDE.md` for design system reference
   - Follow `website-sections/[N].section-name.md` for each section's specs
3. **Check off tasks** in `website-guidelines/tasks.md` as you complete them

### Option 2: Use as a Standalone Reference

1. **Read the product brief** (`website-guidelines/product-brief.md`) to understand the project
2. **Review the style guide** (`website-guidelines/STYLE_GUIDE.md`) for design patterns
3. **Implement sections** using the detailed specifications in `website-sections/`
4. **Adapt the design** for your own project by modifying colors, content, and components

### Option 3: Clone and Customize

1. **Fork or clone** this repository
2. **Set up your Next.js project** following `PROJECT_REQUIREMENTS.md`
3. **Replace Guardian AI branding** with your own
4. **Customize colors** (currently uses #01FFFF cyan as primary)
5. **Build sections** one by one using the provided specifications

## 🎨 Design System Overview

### Colors
- **Primary**: `#01FFFF` (Cyan) - Main brand color
- **Accent**: `#ffa260` (Orange) - For glows and highlights only
- **Background**: Dark theme with subtle noise and particles

### Typography
- **Primary Font**: Satoshi (Clean, modern)
- **Accent Font**: Instrument Serif Regular Italic (Calligraphic contrast)

### Key Features
- Dark, premium aesthetic
- Fully responsive (desktop, tablet, mobile)
- Blazing fast performance
- 3D hero section with Three.js
- Smooth animations with Framer Motion

## 📚 Key Documentation Files

| File | Purpose |
|------|---------|
| `STYLE_GUIDE.md` | **Start here** - Complete design system, component patterns, and styling guidelines |
| `PROJECT_REQUIREMENTS.md` | Tech stack, dependencies, and project architecture |
| `product-brief.md` | Product overview, target users, and goals |
| `tasks.md` | Implementation checklist and progress tracking |
| `website-sections/[N].*.md` | Detailed specs for each website section |

## 🛠️ Tech Stack

- **Framework**: Next.js 14 (App Router)
- **Language**: TypeScript
- **Styling**: Tailwind CSS
- **3D Graphics**: Three.js + React Three Fiber
- **Animations**: Framer Motion
- **Icons**: Lucide React
- **UI Components**: shadcn/ui

## 📖 Getting Started

1. **Initialize your Next.js project**:
   ```bash
   npx create-next-app@latest my-website --typescript --tailwind --app
   ```

2. **Install dependencies** (see `PROJECT_REQUIREMENTS.md` for full list):
   ```bash
   npm install three @react-three/fiber @react-three/drei
   npm install framer-motion lucide-react
   ```

3. **Set up your design system**:
   - Configure Tailwind with colors from `STYLE_GUIDE.md`
   - Add custom fonts (Satoshi + Instrument Serif)
   - Set up CSS variables for theming

4. **Build sections sequentially**:
   - Follow the numbered order in `website-sections/`
   - Reference each section's markdown file for detailed specs
   - Use `STYLE_GUIDE.md` for component patterns

## 💡 Tips for Success

- **Read the style guide first** - It's the single source of truth for design decisions
- **Follow the section order** - Sections build on each other
- **Check the inspiration images** - Visual references are included in `inspo-images/`
- **Use the tasks checklist** - Track your progress in `tasks.md`
- **Adapt components** - Replace Guardian AI branding with your own

## 🔄 Component Adaptation

When adapting components from this boilerplate:

1. Replace non-brand gradient colors with your primary color
2. Update text content and branding
3. Modify the 3D model in the hero section (if needed)
4. Adjust spacing and sizing to match your brand
5. Keep the design system structure but customize values

## 📝 Notes

- This is a **documentation/boilerplate repository** - it doesn't contain the actual code implementation
- The actual code is built in the tutorial video
- Use this as a reference guide while coding
- All design decisions are documented in `STYLE_GUIDE.md`

## 🤝 Contributing

This is a tutorial/educational repository. Feel free to:
- Fork it for your own projects
- Adapt the design system for your needs
- Share improvements or variations

## 📄 License

This boilerplate is provided as-is for educational purposes. Feel free to use it in your own projects!

---

**Happy Building! 🚀**

For questions or issues, refer to the YouTube tutorial or open an issue in this repository.
