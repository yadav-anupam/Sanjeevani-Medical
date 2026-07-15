---
name: Sanjeevani Medical System
colors:
  surface: '#f8f9ff'
  surface-dim: '#cbdbf5'
  surface-bright: '#f8f9ff'
  surface-container-lowest: '#ffffff'
  surface-container-low: '#eff4ff'
  surface-container: '#e5eeff'
  surface-container-high: '#dce9ff'
  surface-container-highest: '#d3e4fe'
  on-surface: '#0b1c30'
  on-surface-variant: '#3e4850'
  inverse-surface: '#213145'
  inverse-on-surface: '#eaf1ff'
  outline: '#6e7881'
  outline-variant: '#bec8d2'
  surface-tint: '#006591'
  primary: '#006591'
  on-primary: '#ffffff'
  primary-container: '#0ea5e9'
  on-primary-container: '#003751'
  inverse-primary: '#89ceff'
  secondary: '#006c49'
  on-secondary: '#ffffff'
  secondary-container: '#6cf8bb'
  on-secondary-container: '#00714d'
  tertiary: '#855300'
  on-tertiary: '#ffffff'
  tertiary-container: '#d88a00'
  on-tertiary-container: '#4a2c00'
  error: '#ba1a1a'
  on-error: '#ffffff'
  error-container: '#ffdad6'
  on-error-container: '#93000a'
  primary-fixed: '#c9e6ff'
  primary-fixed-dim: '#89ceff'
  on-primary-fixed: '#001e2f'
  on-primary-fixed-variant: '#004c6e'
  secondary-fixed: '#6ffbbe'
  secondary-fixed-dim: '#4edea3'
  on-secondary-fixed: '#002113'
  on-secondary-fixed-variant: '#005236'
  tertiary-fixed: '#ffddb8'
  tertiary-fixed-dim: '#ffb95f'
  on-tertiary-fixed: '#2a1700'
  on-tertiary-fixed-variant: '#653e00'
  background: '#f8f9ff'
  on-background: '#0b1c30'
  surface-variant: '#d3e4fe'
typography:
  display:
    fontFamily: Geist
    fontSize: 48px
    fontWeight: '700'
    lineHeight: '1.1'
    letterSpacing: -0.02em
  headline-lg:
    fontFamily: Geist
    fontSize: 32px
    fontWeight: '600'
    lineHeight: 40px
    letterSpacing: -0.01em
  headline-lg-mobile:
    fontFamily: Geist
    fontSize: 24px
    fontWeight: '600'
    lineHeight: 32px
  headline-md:
    fontFamily: Geist
    fontSize: 24px
    fontWeight: '600'
    lineHeight: 32px
  title-lg:
    fontFamily: Inter
    fontSize: 18px
    fontWeight: '600'
    lineHeight: 28px
  body-lg:
    fontFamily: Inter
    fontSize: 16px
    fontWeight: '400'
    lineHeight: 24px
  body-md:
    fontFamily: Inter
    fontSize: 14px
    fontWeight: '400'
    lineHeight: 20px
  label-md:
    fontFamily: Geist
    fontSize: 12px
    fontWeight: '500'
    lineHeight: 16px
    letterSpacing: 0.05em
  mono-sm:
    fontFamily: Geist
    fontSize: 13px
    fontWeight: '400'
    lineHeight: 18px
rounded:
  sm: 0.25rem
  DEFAULT: 0.5rem
  md: 0.75rem
  lg: 1rem
  xl: 1.5rem
  full: 9999px
spacing:
  base: 4px
  xs: 4px
  sm: 8px
  md: 16px
  lg: 24px
  xl: 32px
  2xl: 48px
  3xl: 64px
  gutter: 24px
  margin: 32px
  max_width: 1440px
---

## Brand & Style
The design system for this pharmaceutical platform is built on the pillars of **Precision, Vitality, and Trust**. The aesthetic merges **Corporate Modernism** with a high-utility **SaaS** approach to ensure that pharmacists and administrators can manage complex inventories and prescriptions without cognitive fatigue.

The visual direction prioritizes clarity through generous whitespace, a structured information hierarchy, and a refined "medical-tech" feel. It balances the sterile reliability of healthcare with the fluid efficiency of modern enterprise software. The experience should feel responsive, dependable, and meticulously organized.

## Colors
The palette is rooted in functional color theory to assist in rapid data scanning. 

- **Primary (Medical Blue):** Used for primary actions, branding, and focused states. It signals competence and technological sophistication.
- **Secondary (Healing Green):** Dedicated to positive statuses, successful transactions, and "in-stock" indicators.
- **Accent (Soft Amber):** Reserved for warnings, pending actions, and near-expiry alerts.
- **Neutral (Slate/Zinc):** A sophisticated range of cool greys used for text, borders, and structural surfaces.

In **Dark Mode**, the system shifts to a deep Slate palette (`#0F172A`) to reduce eye strain during night shifts, utilizing elevated surface colors (`#1E293B`) to maintain depth and hierarchy.

## Typography
The system employs a dual-font strategy. **Geist** is used for headings and UI labels to provide a precise, technical character and excellent legibility in uppercase formats. **Inter** handles all body copy and data-heavy content, chosen for its neutral tone and exceptional performance in dense interfaces.

For tabular data and SKU numbers, use the `mono-sm` token to ensure character alignment. All headings utilize a tighter letter-spacing to maintain a "premium" feel.

## Layout & Spacing
The layout relies on a **12-column fluid grid** for desktop, optimized for a maximum width of 1440px. 

- **Desktop:** 12 columns | 24px gutter | 32px side margins.
- **Tablet:** 8 columns | 16px gutter | 24px side margins.
- **Mobile:** 4 columns | 12px gutter | 16px side margins.

A strict 4px/8px baseline grid is enforced for all internal component padding and margins. Dashboard layouts should utilize a "Sidebar + Header + Content" structure, where the sidebar remains fixed at 280px on desktop.

## Elevation & Depth
This design system uses **Tonal Layers** supplemented by **Ambient Shadows** to define the z-axis. 

- **Level 0 (Background):** Slate-50 (#F8FAFC).
- **Level 1 (Cards/Sidebar):** Pure White (#FFFFFF) with a thin 1px border (Slate-200).
- **Level 2 (Dropdowns/Modals):** Pure White with a multi-layered shadow: `0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1)`.
- **Level 3 (Active Overlays):** Soft backdrop blur (8px) on modal overlays to maintain context while focusing the user.

Shadows should be "tinted" with a hint of the Primary Blue in Light Mode to maintain brand cohesion.

## Shapes
A **Rounded** shape language is standard. This creates a modern, approachable feel while remaining professional.

- **Standard Elements:** 8px (0.5rem) for buttons, input fields, and cards.
- **Small Elements:** 4px (0.25rem) for checkboxes and tags.
- **Large Elements:** 16px (1rem) for containers and main dashboard panels.
- **Full Rounded:** Used exclusively for status badges and search bars (Pill-style).

## Components

### Navbar & Sidebar
- **Sidebar:** Fixed width (280px). Active states use a "subtle pill" background (Primary Blue at 10% opacity) with a 4px vertical primary accent bar on the left.
- **Header:** Height 64px. Contains breadcrumbs, global search, and notification profile. Uses a bottom border (Slate-100) instead of a shadow.

### Stats Cards
- Background: Level 1 elevation.
- Content: Icon (Primary color on 10% bg), Label (Grey-500), Value (Headline-md), and Trend indicator (Green/Red small text).

### Data Tables
- Header: Light Slate background, Geist SemiBold text, all-caps.
- Rows: Hover state uses Slate-50. Cells have 16px vertical padding.
- **Status Badges:** Small, uppercase labels. 
  - *In Stock:* Healing Green text on Light Green background.
  - *Low Stock:* Soft Amber text on Light Amber background.
  - *Out of Stock:* Red-600 text on Red-50 background.

### POS Inputs
- **Search Bar:** Pill-shaped with a search icon and shortcut hint (e.g., CMD+K).
- **Input Fields:** 8px radius, Slate-300 border. Focus state: Primary Blue 1px border with a 3px soft blue glow (Ring).
- **Primary Button:** Solid Medical Blue, White text. Subtle lift on hover.