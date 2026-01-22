# Guardian AI Landing Page - Tasks

Always mark with done when a task is done

## Phase 1: Project Setup

- [x] **setup-project** — Initialize Next.js 14 + TypeScript + Tailwind + shadcn/ui + dependencies
- [x] **setup-design-system** — Configure fonts, CSS variables, and Tailwind theme from STYLE_GUIDE.md

## Phase 2: Build Sections (with design instructions)

- [x] **build-navbar** — Navigation section
- [x] **build-hero** — Hero section with Three.js angel
- [x] **build-trust-logos** — Trust Logos marquee
- [x] **build-features** — Features bento grid with 7 cards

## Phase 4: Build Sections (design instructions TBD)

- [ ] **build-how-it-works** — ⏸️ Waiting for design instructions
- [ ] **build-capabilities** — ⏸️ Waiting for design instructions
- [ ] **build-pricing** — ⏸️ Waiting for design instructions
- [ ] **build-testimonials** — ⏸️ Waiting for design instructions
- [ ] **build-faq** — ⏸️ Waiting for design instructions
- [ ] **build-footer** — ⏸️ Waiting for design instructions

---

## Reference Files

| Section | Content Source |
|---------|---------------|
| Design System | `website-guidelines/STYLE_GUIDE.md` |
| Navigation | `website-sections/1.navigation-bar.md` |
| Hero | `website-sections/2.hero-section.md` |
| Trust Logos | `website-sections/3.trust-logos-section.md` |
| Features | `website-sections/4.features-section.md` |
| How It Works | `website-sections/5.how-it-works-section.md` |
| Capabilities | `website-sections/6.core-capabilities-section.md` |
| Pricing | `website-sections/7.pricing-section.md` |
| Testimonials | `website-sections/8.testimonials-section.md` |
| FAQ | `website-sections/9.faq-section.md` |
| Footer | `website-sections/10.footer-section.md` |

## Component Adaptation Notes

When implementing components from section files:
1. Replace non-brand gradient colors with cyan (#01FFFF)
2. Set `disabled = false` on GlowingEffect by default
3. Use STYLE_GUIDE.md as the canonical reference for adapted components

