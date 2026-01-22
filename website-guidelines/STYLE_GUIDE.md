# Guardian AI - Comprehensive Style Guide

> The single source of truth for all visual design decisions. Reference this document to maintain consistency across the landing page.

---

## Table of Contents

1. [Design Philosophy](#1-design-philosophy)
2. [Color System](#2-color-system)
3. [Typography](#3-typography)
4. [Spacing & Layout](#4-spacing--layout)
5. [Component Patterns](#5-component-patterns)
6. [Visual Effects](#6-visual-effects)
7. [Animation & Motion](#7-animation--motion)
8. [Iconography](#8-iconography)
9. [Section Patterns](#9-section-patterns)
10. [Code Reference](#10-code-reference)

---

## 1. Design Philosophy

### Brand Identity

Guardian AI is a security-focused SaaS platform. The visual design must communicate:

- **Trust** — Clean, professional aesthetic that instills confidence
- **Technical credibility** — Modern UI patterns familiar to developers
- **Premium quality** — Polished details and sophisticated effects
- **Clarity** — Information hierarchy that guides users naturally

### Aesthetic Keywords

```
dark • premium • technical • minimal
```

### Target Audience

- Developers and engineering teams
- DevOps & SRE professionals
- Security engineers and compliance teams
- Tech founders and CTOs
- Mid-to-large organizations

### Visual Principles

| Principle | Application |
|-----------|-------------|
| Dark-first | Deep black backgrounds create focus and premium feel |
| High contrast | White text on dark, cyan accents for emphasis |
| Subtle depth | Layered cards, soft glows, and frosted glass |
| Purposeful motion | Animations that guide attention, not distract |

---

## 2. Color System

### Core Palette

```css
:root {
  /* ═══════════════════════════════════════════════════
     PRIMARY BRAND COLOR
     ═══════════════════════════════════════════════════ */
  --primary-cyan: #01FFFF;
  
  /* ═══════════════════════════════════════════════════
     ACCENT COLOR (glows/highlights ONLY, never for text)
     ═══════════════════════════════════════════════════ */
  --accent-orange: #ffa260;
  
  /* ═══════════════════════════════════════════════════
     BACKGROUNDS
     ═══════════════════════════════════════════════════ */
  --bg-dark: #0a0a0a;
  --bg-card: #111111;
  --bg-elevated: #1a1a1a;
  
  /* ═══════════════════════════════════════════════════
     TEXT COLORS
     ═══════════════════════════════════════════════════ */
  --text-primary: #ffffff;
  --text-secondary: #a1a1aa;
  --text-tertiary: #71717a;
  --text-accent: #01FFFF;
  
  /* ═══════════════════════════════════════════════════
     BORDERS & DIVIDERS
     ═══════════════════════════════════════════════════ */
  --border-subtle: rgba(255, 255, 255, 0.1);
  --border-medium: rgba(255, 255, 255, 0.15);
  --border-strong: rgba(255, 255, 255, 0.2);
  
  /* ═══════════════════════════════════════════════════
     SEMANTIC COLORS
     ═══════════════════════════════════════════════════ */
  --color-success: #22c55e;
  --color-warning: #ffa260;
  --color-error: #ef4444;
  --color-info: #01FFFF;
}
```

### Color Usage Guidelines

| Token | When to Use | When NOT to Use |
|-------|-------------|-----------------|
| `--primary-cyan` | Accent text (italic words), glows, hover states, primary buttons, links | Large text blocks, backgrounds |
| `--accent-orange` | Subtle glows, highlights, status indicators | Text of any kind, primary UI elements |
| `--bg-dark` | Page background, section backgrounds | Card backgrounds |
| `--bg-card` | Cards, modals, elevated surfaces | Page background |
| `--text-primary` | Headlines, important labels | Descriptions, secondary info |
| `--text-secondary` | Body text, descriptions, subheadlines | Headlines, buttons |

### Do's and Don'ts

```
✅ DO: Use cyan (#01FFFF) for accent words in italic
✅ DO: Use orange (#ffa260) only for glow effects and subtle highlights
✅ DO: Keep body text in off-white/gray for readability

❌ DON'T: Use orange for text content
❌ DON'T: Use cyan for large blocks of text
❌ DON'T: Mix multiple bright colors in close proximity
```

---

## 3. Typography

### Font Families

| Font | Weight | Usage | CSS Variable |
|------|--------|-------|--------------|
| **Satoshi** | Bold (700) | Headlines, H1-H3 | `--font-headline` |
| **Instrument Serif** | Regular Italic | Accent words in cyan | `--font-accent` |
| **Satoshi** | Regular (400) | Body text, descriptions | `--font-body` |
| **Satoshi** | Medium (500) | Buttons, labels, tags | `--font-label` |

### Font Loading

```tsx
// next/font configuration
import { Instrument_Serif } from 'next/font/google';
import localFont from 'next/font/local';

const satoshi = localFont({
  src: [
    { path: './fonts/Satoshi-Regular.woff2', weight: '400' },
    { path: './fonts/Satoshi-Medium.woff2', weight: '500' },
    { path: './fonts/Satoshi-Bold.woff2', weight: '700' },
  ],
  variable: '--font-satoshi',
});

const instrumentSerif = Instrument_Serif({
  weight: '400',
  style: 'italic',
  subsets: ['latin'],
  variable: '--font-instrument',
});
```

### Type Scale

```css
:root {
  /* Headlines */
  --text-6xl: 3.75rem;    /* 60px - Hero headline */
  --text-5xl: 3rem;       /* 48px - Section titles */
  --text-4xl: 2.25rem;    /* 36px - Large headings */
  --text-3xl: 1.875rem;   /* 30px - Medium headings */
  --text-2xl: 1.5rem;     /* 24px - Small headings */
  --text-xl: 1.25rem;     /* 20px - Large body */
  
  /* Body */
  --text-lg: 1.125rem;    /* 18px - Lead paragraphs */
  --text-base: 1rem;      /* 16px - Body text */
  --text-sm: 0.875rem;    /* 14px - Small text, captions */
  --text-xs: 0.75rem;     /* 12px - Tags, badges */
  
  /* Line Heights */
  --leading-tight: 1.1;
  --leading-snug: 1.25;
  --leading-normal: 1.5;
  --leading-relaxed: 1.625;
}
```

### Typography Patterns

#### Section Header Pattern

Every section follows this hierarchy:

```
[TAG] ← Small uppercase, cyan or gray, Satoshi Medium
[HEADLINE] ← Large, white, Satoshi Bold + Instrument Serif Italic accent
[DESCRIPTION] ← Medium, gray, Satoshi Regular
```

**Example Implementation:**

```tsx
<div className="text-center">
  {/* Tag */}
  <span className="text-xs uppercase tracking-wider text-cyan-400 font-medium">
    Platform Features
  </span>
  
  {/* Headline with accent word */}
  <h2 className="mt-4 text-5xl font-bold text-white">
    Security <em className="font-instrument text-cyan-400 not-italic">Orchestration.</em>
  </h2>
  
  {/* Description */}
  <p className="mt-6 text-lg text-zinc-400 max-w-2xl mx-auto">
    Connect every element of your security posture to build a dynamic defense system.
  </p>
</div>
```

#### Accent Word Pattern

Accent words use **Instrument Serif Italic** in **cyan (#01FFFF)**:

```tsx
// Pattern: Main text + italic accent
<h1 className="font-satoshi font-bold text-white">
  Your infrastructure's{' '}
  <em className="font-instrument italic text-[#01FFFF]">silent guardian.</em>
</h1>
```

---

## 4. Spacing & Layout

### Spacing Scale (8px base)

```css
:root {
  --space-0: 0;
  --space-1: 0.25rem;   /* 4px */
  --space-2: 0.5rem;    /* 8px */
  --space-3: 0.75rem;   /* 12px */
  --space-4: 1rem;      /* 16px */
  --space-5: 1.25rem;   /* 20px */
  --space-6: 1.5rem;    /* 24px */
  --space-8: 2rem;      /* 32px */
  --space-10: 2.5rem;   /* 40px */
  --space-12: 3rem;     /* 48px */
  --space-16: 4rem;     /* 64px */
  --space-20: 5rem;     /* 80px */
  --space-24: 6rem;     /* 96px */
  --space-32: 8rem;     /* 128px */
}
```

### Container Widths

```css
:root {
  --container-sm: 640px;
  --container-md: 768px;
  --container-lg: 1024px;
  --container-xl: 1280px;
  --container-2xl: 1400px;
}
```

### Section Padding

```css
/* Vertical padding between sections */
.section {
  padding-top: var(--space-24);    /* 96px */
  padding-bottom: var(--space-24); /* 96px */
}

/* Horizontal padding (container) */
.container {
  padding-left: var(--space-4);    /* 16px mobile */
  padding-right: var(--space-4);
}

@media (min-width: 768px) {
  .container {
    padding-left: var(--space-8);  /* 32px tablet+ */
    padding-right: var(--space-8);
  }
}
```

### Responsive Breakpoints

| Breakpoint | Value | Target |
|------------|-------|--------|
| `sm` | 640px | Large phones |
| `md` | 768px | Tablets |
| `lg` | 1024px | Laptops |
| `xl` | 1280px | Desktops |
| `2xl` | 1400px | Large screens |

### Grid Systems

#### Bento Grid (Features Section)

```tsx
// 7-card asymmetric bento layout
<div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
  <div className="lg:col-span-2">Card 1 - Wide</div>
  <div>Card 2</div>
  <div>Card 3</div>
  <div className="lg:col-span-2">Card 4 - Wide</div>
  <div className="md:col-span-2 lg:col-span-1">Card 5</div>
  <div>Card 6</div>
  <div>Card 7</div>
</div>
```

#### Standard Grid (Capabilities, Pricing)

```tsx
// 3-column grid
<div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
  {items.map(item => <Card key={item.id} {...item} />)}
</div>
```

---

## 5. Component Patterns

### Buttons

#### Primary Button (StarButton)

Animated glow button for primary CTAs. Use the provided `StarButton` component.

```tsx
// Usage
<StarButton 
  lightColor="#01FFFF"
  backgroundColor="#0a0a0a"
  className="px-6"
>
  Get Started
</StarButton>
```

**Specifications:**
- Shape: Pill (rounded-3xl)
- Height: 40px (h-10)
- Padding: 16px horizontal (px-4)
- Font: Satoshi Medium, 14px
- Animation: Orbiting glow effect

#### Secondary Button (Frosted Glass)

```tsx
<button className="
  h-10 px-6
  rounded-full
  bg-white/5
  backdrop-blur-md
  border border-white/10
  text-white text-sm font-medium
  hover:bg-white/10
  transition-all duration-200
  flex items-center gap-2
">
  View Docs
  <ArrowRight className="w-4 h-4" />
</button>
```

**Specifications:**
- Background: `bg-white/5` with `backdrop-blur-md`
- Border: `border-white/10`
- Hover: `bg-white/10`

### Cards

#### Base Card

```tsx
<div className="
  relative
  rounded-2xl
  bg-[#111111]
  border border-white/10
  p-6
  overflow-hidden
">
  {/* GlowingEffect for hover */}
  <GlowingEffect disabled={false} />
  
  {/* Card content */}
</div>
```

**Specifications:**
- Background: `#111111`
- Border: `rgba(255, 255, 255, 0.1)`
- Border radius: `1rem` (rounded-2xl)
- Padding: `1.5rem` (p-6)

#### Feature Card with Mini UI Mock

Each feature card should contain a visual mock representing the feature:

```tsx
<div className="relative rounded-2xl bg-[#111111] border border-white/10 p-6 overflow-hidden">
  <GlowingEffect />
  
  {/* Mini UI Mock Area */}
  <div className="h-40 mb-4 rounded-lg bg-black/50 p-4">
    {/* Feature-specific UI visualization */}
  </div>
  
  {/* Text Content */}
  <h3 className="text-lg font-semibold text-white">Threat Score</h3>
  <p className="mt-2 text-sm text-zinc-400">Real-time risk assessment.</p>
</div>
```

### Navigation

```tsx
<nav className="
  fixed top-0 left-0 right-0 z-50
  h-16
  bg-black/50
  backdrop-blur-xl
  border-b border-white/5
">
  <div className="container mx-auto h-full flex items-center justify-between">
    {/* Logo */}
    <span className="text-xl font-bold text-white">Guardian AI</span>
    
    {/* Links */}
    <div className="hidden md:flex items-center gap-8">
      <a href="#features" className="text-sm text-zinc-400 hover:text-white transition-colors">
        Features
      </a>
      {/* More links... */}
    </div>
    
    {/* CTA */}
    <StarButton>Sign Up</StarButton>
  </div>
</nav>
```

### Tags / Badges

```tsx
// Section tag
<span className="
  inline-flex items-center gap-2
  px-3 py-1
  rounded-full
  bg-white/5
  border border-white/10
  text-xs font-medium uppercase tracking-wider
  text-cyan-400
">
  <Icon className="w-3 h-3" />
  Platform Features
</span>
```

### Pricing Card

```tsx
<div className={cn(
  "relative rounded-2xl p-8",
  isPopular 
    ? "bg-gradient-to-b from-cyan-500/10 to-transparent border-cyan-500/30" 
    : "bg-[#111111] border-white/10",
  "border"
)}>
  {isPopular && (
    <span className="absolute -top-3 left-1/2 -translate-x-1/2 px-3 py-1 bg-cyan-500 text-black text-xs font-bold rounded-full">
      Most Popular
    </span>
  )}
  
  <h3 className="text-xl font-semibold text-white">{tier}</h3>
  <div className="mt-4">
    <span className="text-4xl font-bold text-white">{price}</span>
    <span className="text-zinc-400">/month</span>
  </div>
  
  <ul className="mt-8 space-y-4">
    {features.map(feature => (
      <li key={feature} className="flex items-center gap-3 text-sm text-zinc-300">
        <Check className="w-4 h-4 text-cyan-400" />
        {feature}
      </li>
    ))}
  </ul>
  
  <Button className="mt-8 w-full">{cta}</Button>
</div>
```

---

## 6. Visual Effects

### Glow Effects

#### Cyan Glow (Primary)

```css
/* Card hover glow */
.glow-cyan {
  box-shadow: 
    0 0 20px rgba(1, 255, 255, 0.1),
    0 0 40px rgba(1, 255, 255, 0.05);
}

/* Button glow */
.glow-cyan-strong {
  box-shadow: 
    0 0 20px rgba(1, 255, 255, 0.3),
    0 0 40px rgba(1, 255, 255, 0.2),
    0 0 60px rgba(1, 255, 255, 0.1);
}

/* Text glow */
.text-glow-cyan {
  text-shadow: 0 0 20px rgba(1, 255, 255, 0.5);
}
```

#### Orange Glow (Accent - Subtle Use Only)

```css
.glow-orange {
  box-shadow: 
    0 0 30px rgba(255, 162, 96, 0.1),
    0 0 60px rgba(255, 162, 96, 0.05);
}
```

### Frosted Glass

```css
.frosted-glass {
  background: rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  border: 1px solid rgba(255, 255, 255, 0.1);
}

.frosted-glass-strong {
  background: rgba(0, 0, 0, 0.5);
  backdrop-filter: blur(24px);
  -webkit-backdrop-filter: blur(24px);
}
```

### Noise Texture

```css
/* Apply to body or section backgrounds */
.noise-texture {
  position: relative;
}

.noise-texture::before {
  content: '';
  position: absolute;
  inset: 0;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.65' numOctaves='3' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)'/%3E%3C/svg%3E");
  opacity: 0.03;
  pointer-events: none;
}
```

### Gradient Backgrounds

```css
/* Hero section gradient */
.hero-gradient {
  background: 
    radial-gradient(ellipse at 50% 0%, rgba(1, 255, 255, 0.1) 0%, transparent 50%),
    radial-gradient(ellipse at 80% 50%, rgba(255, 162, 96, 0.05) 0%, transparent 40%),
    #0a0a0a;
}

/* Card gradient (subtle) */
.card-gradient {
  background: linear-gradient(
    180deg,
    rgba(255, 255, 255, 0.03) 0%,
    transparent 100%
  );
}
```

### Border Glow (GlowingEffect Component)

The `GlowingEffect` component creates an animated border glow on hover. See full implementation in [Code Reference](#10-code-reference).

---

## 7. Animation & Motion

### Timing Functions

```css
:root {
  --ease-out-expo: cubic-bezier(0.16, 1, 0.3, 1);
  --ease-out-quad: cubic-bezier(0.25, 0.46, 0.45, 0.94);
  --ease-in-out: cubic-bezier(0.4, 0, 0.2, 1);
  --ease-spring: cubic-bezier(0.34, 1.56, 0.64, 1);
}
```

### Duration Scale

| Duration | Use Case |
|----------|----------|
| `150ms` | Micro-interactions (hover states) |
| `200ms` | Button state changes |
| `300ms` | Card transitions, fade effects |
| `500ms` | Modal/overlay transitions |
| `1000ms+` | Page load animations, complex sequences |

### Hover Transitions

```css
/* Standard hover transition */
.transition-standard {
  transition: all 200ms var(--ease-out-quad);
}

/* Color transitions */
.transition-colors {
  transition: color 150ms ease, background-color 150ms ease;
}

/* Transform transitions */
.transition-transform {
  transition: transform 300ms var(--ease-out-expo);
}
```

### Entrance Animations (Framer Motion)

```tsx
// Fade up animation
const fadeUp = {
  initial: { opacity: 0, y: 20 },
  animate: { opacity: 1, y: 0 },
  transition: { duration: 0.5, ease: [0.16, 1, 0.3, 1] }
};

// Staggered children
const staggerContainer = {
  animate: {
    transition: {
      staggerChildren: 0.1
    }
  }
};

// Scale in
const scaleIn = {
  initial: { opacity: 0, scale: 0.95 },
  animate: { opacity: 1, scale: 1 },
  transition: { duration: 0.4 }
};
```

### Marquee Animation (Trust Logos)

```css
@keyframes marquee {
  0% { transform: translateX(0); }
  100% { transform: translateX(-50%); }
}

.marquee {
  animation: marquee 30s linear infinite;
}

.marquee:hover {
  animation-play-state: paused;
}
```

### StarButton Animation

```css
@keyframes star-btn {
  0% { offset-distance: 0%; }
  100% { offset-distance: 100%; }
}

.animate-star-btn {
  animation: star-btn calc(var(--duration) * 1s) linear infinite;
}
```

---

## 8. Iconography

### Icon Library

Use **Lucide React** for all icons.

```bash
npm install lucide-react
```

### Icon Sizing

| Size | Value | Use Case |
|------|-------|----------|
| `xs` | 12px | Inline badges, tiny indicators |
| `sm` | 16px | Buttons, list items |
| `md` | 20px | Default size, navigation |
| `lg` | 24px | Feature icons, cards |
| `xl` | 32px | Hero elements |

### Icon Usage

```tsx
import { Shield, Zap, Lock, Activity, Users, Settings } from 'lucide-react';

// Standard usage
<Shield className="w-5 h-5 text-cyan-400" />

// With text
<div className="flex items-center gap-2">
  <Zap className="w-4 h-4 text-zinc-400" />
  <span className="text-sm text-zinc-400">Real-time detection</span>
</div>
```

### Recommended Icons per Feature

| Feature | Icon |
|---------|------|
| Real-time detection | `Activity`, `Radar` |
| Automated response | `Zap`, `Bot` |
| Multi-cloud | `Cloud`, `Server` |
| Integration | `Plug`, `GitBranch` |
| Monitoring | `Eye`, `Monitor` |
| Custom rules | `Settings`, `Sliders` |
| Security | `Shield`, `Lock` |
| Analytics | `BarChart`, `TrendingUp` |

---

## 9. Section Patterns

### Navigation Bar

- **Position:** Fixed, top
- **Height:** 64px
- **Background:** `bg-black/50 backdrop-blur-xl`
- **Border:** `border-b border-white/5`
- **Content:** Logo (left), Links (center), CTA button (right)

### Hero Section

- **Layout:** Centered text over 3D visual
- **Background:** Gradient with noise + Three.js canvas
- **Content Stack:**
  1. Tag badge (optional)
  2. Headline (60px, multi-line with accent word)
  3. Subheadline (18px, max-width 600px)
  4. Button group (Primary + Secondary)
- **3D Visual:** Lucy100k.ply model with spotlight animation

### Trust Logos

- **Layout:** Full-width marquee
- **Headline:** Centered above
- **Logo treatment:** Monochrome (white/gray), 40% opacity
- **Animation:** Continuous scroll, pause on hover
- **Fade:** Gradient masks on left/right edges

### Features (Bento Grid)

- **Layout:** Asymmetric 7-card bento grid
- **Card content:** Icon + Mini UI mock + Title + Description
- **Effect:** GlowingEffect on hover
- **Gap:** 16px

### How It Works

- **Layout:** 3 horizontal cards or vertical timeline
- **Content per step:** Number + Title + Description + Icon
- **Visual:** Connecting line or arrows between steps

### Core Capabilities

- **Layout:** 2x3 or 3x2 grid
- **Card content:** Icon + Title + Description
- **Style:** Minimal, icon-forward

### Pricing

- **Layout:** 3 cards, center card highlighted
- **Highlight:** "Most Popular" badge, cyan border glow
- **Content:** Tier name, Price, Feature list, CTA button

### Testimonials

- **Layout:** Large quote + Author info + Highlight pills + Stats bar
- **Quote styling:** Large italic text
- **Stats:** 4-column grid below

### FAQ

- **Layout:** Accordion
- **Style:** Collapsible items with + icon
- **Animation:** Height transition on expand

### Footer

- **Layout:** Multi-column grid
- **Content:** Logo, Nav links, Social icons, Copyright
- **Background:** Slightly darker than page

---

## 10. Code Reference

### Tailwind Configuration

```js
// tailwind.config.js
module.exports = {
  theme: {
    extend: {
      colors: {
        cyan: {
          400: '#01FFFF',
          500: '#00E5E5',
        },
        orange: {
          400: '#ffa260',
        },
      },
      fontFamily: {
        satoshi: ['var(--font-satoshi)', 'sans-serif'],
        instrument: ['var(--font-instrument)', 'serif'],
      },
      animation: {
        'star-btn': 'star-btn calc(var(--duration)*1s) linear infinite',
        'marquee': 'marquee 30s linear infinite',
      },
      keyframes: {
        'star-btn': {
          '0%': { offsetDistance: '0%' },
          '100%': { offsetDistance: '100%' },
        },
        marquee: {
          '0%': { transform: 'translateX(0)' },
          '100%': { transform: 'translateX(-50%)' },
        },
      },
    },
  },
};
```

### CSS Custom Properties (globals.css)

```css
@tailwind base;
@tailwind components;
@tailwind utilities;

@layer base {
  :root {
    /* Colors */
    --primary-cyan: #01FFFF;
    --accent-orange: #ffa260;
    --bg-dark: #0a0a0a;
    --bg-card: #111111;
    --text-primary: #ffffff;
    --text-secondary: #a1a1aa;
    --border-subtle: rgba(255, 255, 255, 0.1);
    
    /* Typography */
    --font-satoshi: 'Satoshi', sans-serif;
    --font-instrument: 'Instrument Serif', serif;
  }
  
  body {
    background-color: var(--bg-dark);
    color: var(--text-secondary);
    font-family: var(--font-satoshi);
  }
}
```

### StarButton Component

```tsx
// components/ui/star-button.tsx
"use client";

import React, { useRef, useEffect, ReactNode, CSSProperties } from "react";
import { cn } from "@/lib/utils";

interface StarButtonProps {
  children: ReactNode;
  lightWidth?: number;
  duration?: number;
  lightColor?: string;
  backgroundColor?: string;
  borderWidth?: number;
  className?: string;
}

export function StarButton({
  children,
  lightWidth = 110,
  duration = 3,
  lightColor = "#01FFFF", // Cyan glow
  backgroundColor = "#0a0a0a",
  borderWidth = 2,
  className,
  ...props
}: StarButtonProps) {
  const pathRef = useRef<HTMLButtonElement>(null);

  useEffect(() => {
    if (pathRef.current) {
      const div = pathRef.current;
      div.style.setProperty(
        "--path",
        `path('M 0 0 H ${div.offsetWidth} V ${div.offsetHeight} H 0 V 0')`,
      );
    }
  }, []);

  return (
    <button
      style={
        {
          "--duration": duration,
          "--light-width": `${lightWidth}px`,
          "--light-color": lightColor,
          "--border-width": `${borderWidth}px`,
          isolation: "isolate",
        } as CSSProperties
      }
      ref={pathRef}
      className={cn(
        "relative z-[3] overflow-hidden h-10 px-4 py-2",
        "inline-flex items-center justify-center gap-2",
        "whitespace-nowrap rounded-3xl text-sm font-medium",
        "transition-colors disabled:pointer-events-none disabled:opacity-50",
        className,
      )}
      {...props}
    >
      <div
        className="absolute aspect-square inset-0 animate-star-btn bg-[radial-gradient(ellipse_at_center,var(--light-color),transparent,transparent)]"
        style={{
          offsetPath: "var(--path)",
          offsetDistance: "0%",
          width: "var(--light-width)",
        } as CSSProperties}
      />
      <div
        className="absolute inset-0 border-white/15 z-[4] overflow-hidden rounded-[inherit] text-black"
        style={{ borderWidth: "var(--border-width)" }}
        aria-hidden="true"
      >
        {/* StarBackground SVG goes here - see full code in 1.navigation-bar.md */}
      </div>
      <span className="z-10 relative text-white">
        {children}
      </span>
    </button>
  );
}
```

### GlowingEffect Component

```tsx
// components/ui/glowing-effect.tsx
"use client";

import { memo, useCallback, useEffect, useRef } from "react";
import { cn } from "@/lib/utils";
import { animate } from "motion/react";

interface GlowingEffectProps {
  blur?: number;
  inactiveZone?: number;
  proximity?: number;
  spread?: number;
  variant?: "default" | "white";
  glow?: boolean;
  className?: string;
  disabled?: boolean;
  movementDuration?: number;
  borderWidth?: number;
}

const GlowingEffect = memo(({
  blur = 0,
  inactiveZone = 0.7,
  proximity = 0,
  spread = 20,
  variant = "default",
  glow = false,
  className,
  movementDuration = 2,
  borderWidth = 1,
  disabled = false,
}: GlowingEffectProps) => {
  const containerRef = useRef<HTMLDivElement>(null);
  const lastPosition = useRef({ x: 0, y: 0 });
  const animationFrameRef = useRef<number>(0);

  const handleMove = useCallback(
    (e?: MouseEvent | { x: number; y: number }) => {
      if (!containerRef.current) return;

      if (animationFrameRef.current) {
        cancelAnimationFrame(animationFrameRef.current);
      }

      animationFrameRef.current = requestAnimationFrame(() => {
        const element = containerRef.current;
        if (!element) return;

        const { left, top, width, height } = element.getBoundingClientRect();
        const mouseX = e?.x ?? lastPosition.current.x;
        const mouseY = e?.y ?? lastPosition.current.y;

        if (e) {
          lastPosition.current = { x: mouseX, y: mouseY };
        }

        const center = [left + width * 0.5, top + height * 0.5];
        const distanceFromCenter = Math.hypot(
          mouseX - center[0],
          mouseY - center[1]
        );
        const inactiveRadius = 0.5 * Math.min(width, height) * inactiveZone;

        if (distanceFromCenter < inactiveRadius) {
          element.style.setProperty("--active", "0");
          return;
        }

        const isActive =
          mouseX > left - proximity &&
          mouseX < left + width + proximity &&
          mouseY > top - proximity &&
          mouseY < top + height + proximity;

        element.style.setProperty("--active", isActive ? "1" : "0");

        if (!isActive) return;

        const currentAngle =
          parseFloat(element.style.getPropertyValue("--start")) || 0;
        let targetAngle =
          (180 * Math.atan2(mouseY - center[1], mouseX - center[0])) / Math.PI + 90;

        const angleDiff = ((targetAngle - currentAngle + 180) % 360) - 180;
        const newAngle = currentAngle + angleDiff;

        animate(currentAngle, newAngle, {
          duration: movementDuration,
          ease: [0.16, 1, 0.3, 1],
          onUpdate: (value) => {
            element.style.setProperty("--start", String(value));
          },
        });
      });
    },
    [inactiveZone, proximity, movementDuration]
  );

  useEffect(() => {
    if (disabled) return;

    const handleScroll = () => handleMove();
    const handlePointerMove = (e: PointerEvent) => handleMove(e);

    window.addEventListener("scroll", handleScroll, { passive: true });
    document.body.addEventListener("pointermove", handlePointerMove, {
      passive: true,
    });

    return () => {
      if (animationFrameRef.current) {
        cancelAnimationFrame(animationFrameRef.current);
      }
      window.removeEventListener("scroll", handleScroll);
      document.body.removeEventListener("pointermove", handlePointerMove);
    };
  }, [handleMove, disabled]);

  return (
    <>
      <div
        className={cn(
          "pointer-events-none absolute -inset-px hidden rounded-[inherit] border opacity-0 transition-opacity",
          glow && "opacity-100",
          variant === "white" && "border-white",
          disabled && "!block"
        )}
      />
      <div
        ref={containerRef}
        style={{
          "--blur": `${blur}px`,
          "--spread": spread,
          "--start": "0",
          "--active": "0",
          "--glowingeffect-border-width": `${borderWidth}px`,
          "--repeating-conic-gradient-times": "5",
          "--gradient": `radial-gradient(circle, #01FFFF 10%, transparent 20%),
            repeating-conic-gradient(
              from 236.84deg at 50% 50%,
              #01FFFF 0%,
              #00E5E5 calc(25% / var(--repeating-conic-gradient-times)),
              #01FFFF calc(50% / var(--repeating-conic-gradient-times))
            )`,
        } as React.CSSProperties}
        className={cn(
          "pointer-events-none absolute inset-0 rounded-[inherit] opacity-100 transition-opacity",
          glow && "opacity-100",
          blur > 0 && "blur-[var(--blur)]",
          className,
          disabled && "!hidden"
        )}
      >
        <div
          className={cn(
            "glow rounded-[inherit]",
            'after:content-[""] after:rounded-[inherit] after:absolute after:inset-[calc(-1*var(--glowingeffect-border-width))]',
            "after:[border:var(--glowingeffect-border-width)_solid_transparent]",
            "after:[background:var(--gradient)] after:[background-attachment:fixed]",
            "after:opacity-[var(--active)] after:transition-opacity after:duration-300",
            "after:[mask-clip:padding-box,border-box]",
            "after:[mask-composite:intersect]",
            "after:[mask-image:linear-gradient(#0000,#0000),conic-gradient(from_calc((var(--start)-var(--spread))*1deg),#00000000_0deg,#fff,#00000000_calc(var(--spread)*2deg))]"
          )}
        />
      </div>
    </>
  );
});

GlowingEffect.displayName = "GlowingEffect";

export { GlowingEffect };
```

### Utility Function

```tsx
// lib/utils.ts
import { clsx, type ClassValue } from "clsx";
import { twMerge } from "tailwind-merge";

export function cn(...inputs: ClassValue[]) {
  return twMerge(clsx(inputs));
}
```

---

## Quick Reference Card

```
┌─────────────────────────────────────────────────────────────┐
│  GUARDIAN AI STYLE QUICK REFERENCE                          │
├─────────────────────────────────────────────────────────────┤
│  COLORS                                                     │
│  Primary Cyan:     #01FFFF (accent text, glows)             │
│  Accent Orange:    #ffa260 (glows only, NEVER text)         │
│  Background:       #0a0a0a (page) / #111111 (cards)         │
│  Text:             #ffffff (headlines) / #a1a1aa (body)     │
├─────────────────────────────────────────────────────────────┤
│  TYPOGRAPHY                                                 │
│  Headlines:        Satoshi Bold 700                         │
│  Accent Words:     Instrument Serif Italic + Cyan           │
│  Body:             Satoshi Regular 400                      │
│  Buttons:          Satoshi Medium 500                       │
├─────────────────────────────────────────────────────────────┤
│  KEY COMPONENTS                                             │
│  Primary CTA:      StarButton (cyan glow)                   │
│  Secondary CTA:    Frosted glass button                     │
│  Cards:            #111111 bg + GlowingEffect hover         │
│  Nav:              Fixed + backdrop-blur-xl                 │
├─────────────────────────────────────────────────────────────┤
│  SPACING                                                    │
│  Section padding:  96px (py-24)                             │
│  Card gap:         16px (gap-4)                             │
│  Container max:    1400px                                   │
└─────────────────────────────────────────────────────────────┘
```

---

