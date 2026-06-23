# Ready Education Design System

A comprehensive design reference for readyeducation.com, extracted for building new pages in the same visual style.

---

## 1. Typography

### Font Family

| Role                   | Font        | Fallback     |
| ---------------------- | ----------- | ------------ |
| **Primary (all text)** | **Figtree** | `sans-serif` |

**Google Fonts import:**

```css
@import url('https://fonts.googleapis.com/css2?family=Figtree:wght@300;400;500;600;700;800;900&display=swap');
```

### Font Weights

| Weight | Name       | Usage                            |
| ------ | ---------- | -------------------------------- |
| 300    | Light      | Decorative/large display text    |
| 400    | Regular    | Body text, paragraphs            |
| 500    | Medium     | Subtitles, secondary headings    |
| 600    | Semibold   | Buttons, labels, emphasis        |
| 700    | Bold       | Headings (h1–h4), card titles    |
| 800    | Extra Bold | Hero headings, key statistics    |
| 900    | Black      | Rarely used, high-impact display |

### Font Sizes (Design Tokens)

| Token           | Size | Usage                           |
| --------------- | ---- | ------------------------------- |
| `--font-small`  | 13px | Captions, fine print, metadata  |
| `--font-body`   | 16px | Body text (browser default)     |
| `--font-medium` | 20px | Lead paragraphs, subtitles      |
| `--font-large`  | 36px | Section headings (h2)           |
| `--font-xlarge` | 42px | Page titles, hero headings (h1) |

### Heading Styles

| Element | Size | Weight  | Transform | Line Height |
| ------- | ---- | ------- | --------- | ----------- |
| h1      | 42px | 700–800 | None      | 1.2         |
| h2      | 36px | 700     | None      | 1.3         |
| h3      | 24px | 700     | Uppercase | 1.3         |
| h4      | 20px | 600–700 | Uppercase | 1.4         |
| h5      | 16px | 600     | Uppercase | 1.5         |
| h6      | 13px | 600     | Uppercase | 1.5         |

### Body Text

- Font size: 16px
- Line height: 1.6
- Color: dark gray/black (see Color section)
- Max width for readability: ~800px (content container)

---

## 2. Color Palette

### Core Brand Colors

| Name              | Hex       | RGB           | Usage                                           |
| ----------------- | --------- | ------------- | ----------------------------------------------- |
| **White**         | `#FFFFFF` | 255, 255, 255 | Page backgrounds, card backgrounds, button text |
| **Black**         | `#000000` | 0, 0, 0       | Primary text, headings                          |
| **Dark Charcoal** | `#32373C` | 50, 55, 60    | Default button background, footer background    |

### Accent Colors

| Name                      | Hex       | RGB           | Usage                                       |
| ------------------------- | --------- | ------------- | ------------------------------------------- |
| **Vivid Cyan Blue**       | `#0693E3` | 6, 147, 227   | Links, primary accent, interactive elements |
| **Vivid Green Cyan**      | `#00D084` | 0, 208, 132   | Success states, highlights, badges          |
| **Light Green Cyan**      | `#7BDCB5` | 123, 220, 181 | Softer accent, backgrounds, hover states    |
| **Vivid Purple**          | `#9B51E0` | 155, 81, 224  | Accent highlights, gradient endpoints       |
| **Luminous Vivid Orange** | `#FF6900` | 255, 105, 0   | Attention, warnings, CTAs                   |
| **Luminous Vivid Amber**  | `#FCB900` | 252, 185, 0   | Highlights, badges, secondary accent        |
| **Vivid Red**             | `#CF2E2E` | 207, 46, 46   | Error states, critical alerts               |

### Neutral Colors

| Name                 | Hex       | RGB           | Usage                          |
| -------------------- | --------- | ------------- | ------------------------------ |
| **Cyan Bluish Gray** | `#ABB8C3` | 171, 184, 195 | Borders, dividers, muted text  |
| **Pale Pink**        | `#F78DA7` | 247, 141, 167 | Decorative accent (light use)  |
| **Pale Cyan Blue**   | `#8ED1FC` | 142, 209, 252 | Light accent backgrounds, tags |

### Gradients

| Name                      | CSS                                                 | Usage                         |
| ------------------------- | --------------------------------------------------- | ----------------------------- |
| **Cyan-to-Purple**        | `linear-gradient(135deg, #0693E3 0%, #9B51E0 100%)` | Hero accents, CTA backgrounds |
| **Cool-to-Warm Spectrum** | `linear-gradient(135deg, #0693E3 0%, #FF6900 100%)` | Decorative backgrounds        |
| **Luminous Dusk**         | `linear-gradient(135deg, #FF6900 0%, #9B51E0 100%)` | Feature highlights            |

### Color Usage Rules

1. **Backgrounds**: White (`#FFFFFF`) for main content; `#32373C` for dark sections (footer, dark CTAs)
2. **Text on light backgrounds**: `#000000` for headings, dark gray for body
3. **Text on dark backgrounds**: `#FFFFFF` for all text
4. **Links**: `#0693E3` (underlined by default)
5. **Buttons**: `#32373C` background + `#FFFFFF` text (primary); accent colors for secondary
6. **Icons**: Match heading color or use accent color (`#0693E3`, `#00D084`)

---

## 3. Spacing System

### Spacing Scale (CSS Custom Properties)

| Token          | Value   | Pixels (approx) | Usage                                  |
| -------------- | ------- | --------------- | -------------------------------------- |
| `--spacing-20` | 0.44rem | ~7px            | Tight gaps, icon padding               |
| `--spacing-30` | 0.67rem | ~11px           | Small internal padding                 |
| `--spacing-40` | 1rem    | 16px            | Default element spacing                |
| `--spacing-50` | 1.5rem  | 24px            | Section internal padding, card padding |
| `--spacing-60` | 2.25rem | 36px            | Between content blocks                 |
| `--spacing-70` | 3.38rem | ~54px           | Section separators                     |
| `--spacing-80` | 5.06rem | ~81px           | Large section padding (top/bottom)     |

### Block Gap

- Default gap between blocks/elements: **24px**
- Card grid gap: **24px**
- Navigation item gap: **16px–24px**

### Section Padding Pattern

```
Top/Bottom padding:  80px (5.06rem) on desktop
                     40px (2.5rem) on tablet
                     24px (1.5rem) on mobile
Left/Right padding:  24px–40px (within content container)
```

---

## 4. Layout & Grid

### Container Widths

| Container      | Max Width | Usage                                         |
| -------------- | --------- | --------------------------------------------- |
| **Content**    | 800px     | Text-heavy sections, articles, body copy      |
| **Wide**       | 1200px    | Feature sections, cards, multi-column layouts |
| **Full Width** | 100%      | Hero sections, full-bleed backgrounds         |

### Grid System

- Uses CSS Flexbox and CSS Grid (via Elementor)
- Typical column layouts: **2-column** (text + image), **3-column** (feature cards), **4-column** (stats/metrics)
- Alternating image/text sections: image alternates left/right per section

### Content Layout Patterns

```
┌─────────────────────────────────────────────────────────┐
│                    HERO (full-width)                     │
│              Background image + overlay                  │
│           Animated headline + 2 CTA buttons              │
├─────────────────────────────────────────────────────────┤
│                STATS BAR (wide container)                │
│         [Stat 1]     [Stat 2]     [Stat 3]              │
├─────────────────────────────────────────────────────────┤
│            FEATURE SECTION (wide container)              │
│    ┌──────────────┐  ┌──────────────────────┐           │
│    │    Text +     │  │                      │           │
│    │   CTA link    │  │      Image           │           │
│    └──────────────┘  └──────────────────────┘           │
├─────────────────────────────────────────────────────────┤
│         FEATURE SECTION (alternating layout)             │
│    ┌──────────────────────┐  ┌──────────────┐           │
│    │                      │  │    Text +     │           │
│    │      Image           │  │   CTA link    │           │
│    └──────────────────────┘  └──────────────┘           │
├─────────────────────────────────────────────────────────┤
│              TESTIMONIAL (content container)             │
│         Quote + Attribution + Metric highlight           │
├─────────────────────────────────────────────────────────┤
│              CTA SECTION (wide container)                │
│            Heading + Button + Contact info               │
├─────────────────────────────────────────────────────────┤
│                 FOOTER (full-width, dark)                │
│       [Col 1]   [Col 2]   [Col 3]   [Social]           │
└─────────────────────────────────────────────────────────┘
```

---

## 5. Responsive Breakpoints

| Name             | Min Width | Max Width | Usage                  |
| ---------------- | --------- | --------- | ---------------------- |
| **XS**           | 0px       | 479px     | Small phones           |
| **SM**           | 480px     | 767px     | Large phones           |
| **MD (Tablet)**  | 768px     | 1024px    | Tablets, small laptops |
| **LG (Desktop)** | 1025px    | 1439px    | Standard desktop       |
| **XL**           | 1440px    | 1599px    | Large desktop          |
| **XXL**          | 1600px    | —         | Ultra-wide             |

### Responsive Behavior

- **Mobile (< 768px)**: Single column, stacked sections, reduced padding, hamburger nav
- **Tablet (768–1024px)**: 2-column where possible, reduced hero size
- **Desktop (1025px+)**: Full multi-column layout, full hero with animations

---

## 6. Component Styles

### Buttons

#### Primary Button

```css
.button-primary {
	font-family: 'Figtree', sans-serif;
	font-size: 16px;
	font-weight: 600;
	background-color: #32373c;
	color: #ffffff;
	padding: calc(0.667em + 2px) calc(1.333em + 2px); /* ~13px 23px */
	border: none;
	border-radius: 4px;
	text-decoration: none;
	cursor: pointer;
	transition: background-color 0.2s ease;
}
.button-primary:hover {
	background-color: #1d2024; /* darker shade */
}
```

#### Secondary Button / Link Button

```css
.button-secondary {
	font-family: 'Figtree', sans-serif;
	font-size: 16px;
	font-weight: 600;
	background: transparent;
	color: #0693e3;
	padding: calc(0.667em + 2px) calc(1.333em + 2px);
	border: 2px solid #0693e3;
	border-radius: 4px;
	text-decoration: none;
	cursor: pointer;
}
```

#### Text Link / CTA Link

```css
.cta-link {
	font-family: 'Figtree', sans-serif;
	font-weight: 600;
	color: #0693e3;
	text-decoration: underline;
}
```

### Cards

#### Success Story Card

```css
.card {
	border-radius: 5px;
	padding: 40px;
	background-size: cover;
	background-position: center;
	overflow: hidden;
	position: relative;
}
.card-overlay {
	background: rgba(0, 0, 0, 0.6);
	position: absolute;
	inset: 0;
}
.card-content {
	position: relative;
	z-index: 1;
	color: #ffffff;
}
```

#### Feature Card (minimal)

```css
.feature-card {
	padding: 24px;
	background: #ffffff;
	border-radius: 5px;
	box-shadow: none; /* clean, flat style */
}
```

### Navigation Bar

```
┌──────────────────────────────────────────────────────────────┐
│  [Logo]   Product  Solutions▾  Success  Resources▾  About▾  │
│                                              [Request Demo]  │
└──────────────────────────────────────────────────────────────┘
```

- **Height**: ~64–80px
- **Logo**: 191×20px horizontal wordmark
- **Font size**: 14–16px, weight 500–600
- **Nav link color**: `#000000` (or `#FFFFFF` on dark headers)
- **CTA button**: Dark charcoal `#32373C`, stands out from nav links
- **Dropdown**: White background, subtle shadow, 8px border-radius
- **Sticky**: Yes, fixed to top on scroll

### Footer

- **Background**: `#32373C` (dark charcoal)
- **Text color**: `#FFFFFF`
- **Link color**: `#FFFFFF`, opacity 0.8 on hover
- **Layout**: 3–4 columns + social icons row
- **Social icons**: Facebook, Twitter/X, LinkedIn (white, ~20px)
- **Padding**: 60–80px top/bottom
- **Copyright**: Centered, smaller text (13px)

---

## 7. Shadows

| Name         | CSS                                                           | Usage                        |
| ------------ | ------------------------------------------------------------- | ---------------------------- |
| **Natural**  | `6px 6px 9px rgba(0, 0, 0, 0.2)`                              | Cards, elevated elements     |
| **Deep**     | `12px 12px 50px rgba(0, 0, 0, 0.4)`                           | Modals, overlays             |
| **Sharp**    | `6px 6px 0px rgba(0, 0, 0, 0.2)`                              | Graphic/editorial elements   |
| **Outlined** | `6px 6px 0px -3px rgba(255,255,255,1), 6px 6px rgba(0,0,0,1)` | Borders with depth           |
| **Crisp**    | `6px 6px 0px rgba(0, 0, 0, 1)`                                | High-contrast, bold elements |

**Default approach**: The site leans toward **flat/minimal shadows** — most cards and sections use no shadow, relying on whitespace and color contrast for visual hierarchy.

---

## 8. Animations & Transitions

### Page Transitions

```css
transition: all 0.3s ease; /* default for most interactive elements */
```

### Hero Text Rotation

- **Pause duration**: 3000ms (3s per word/phrase)
- **Wipe transition**: 300ms
- **Hidden pause**: 500ms between transitions
- **Icon animation**: Synced with text rotation

### Waterfall / Stagger Effect (cards, list items)

```css
@keyframes fadeInUp {
	0% {
		opacity: 0;
		transform: translateY(20px);
	}
	100% {
		opacity: 1;
		transform: translateY(0);
	}
}
.stagger-item {
	animation: fadeInUp 200ms ease forwards;
	animation-delay: calc(var(--index) * 60ms);
}
```

### Lazy Load Intersection

- Background images use `IntersectionObserver` with `200px` root margin
- Ensures off-screen images load just before entering viewport

---

## 9. Imagery & Media

### Image Format

- **Primary format**: `.webp` (modern, compressed)
- **Fallback**: `.jpg` / `.png`

### Image Patterns

- **Hero**: Full-width background image with dark overlay (opacity 0.4–0.6)
- **Feature sections**: Product screenshots, mockups (right-aligned or left-aligned)
- **Success stories**: Background images with 60% dark overlay + white text
- **Icons**: SVG format, inline or as sprites

### Aspect Ratios

- Hero: ~16:9 or wider (full viewport width)
- Feature images: Free-form, contained within column
- Card thumbnails: ~16:9 or 4:3

---

## 10. Iconography

- **Style**: Outlined/stroke icons (not filled)
- **Size**: 20–24px for inline, 40–48px for feature highlights
- **Color**: Matches text color or uses accent color
- **Source**: SVG, either inline or as icon font

---

## 11. Testimonial / Quote Style

```css
.testimonial {
	font-family: 'Figtree', sans-serif;
	font-size: 20px;
	font-weight: 400;
	font-style: italic;
	line-height: 1.6;
	color: #000000;
	max-width: 800px;
	margin: 0 auto;
	text-align: center;
}
.testimonial-attribution {
	font-size: 14px;
	font-weight: 600;
	margin-top: 16px;
	color: #32373c;
}
.testimonial-metric {
	font-size: 36px;
	font-weight: 800;
	color: #0693e3; /* accent color for standout metrics */
}
```

---

## 12. Statistics / Metrics Display

```css
.stat-number {
	font-family: 'Figtree', sans-serif;
	font-size: 48px; /* or larger */
	font-weight: 800;
	color: #000000;
	line-height: 1.1;
}
.stat-label {
	font-size: 16px;
	font-weight: 500;
	color: #32373c;
	text-transform: uppercase;
	letter-spacing: 0.5px;
}
```

Format pattern: `7K+`, `2M+`, `5M+` (number + unit + plus sign)

---

## 13. Quick Reference: CSS Custom Properties

```css
:root {
	/* Typography */
	--font-family: 'Figtree', sans-serif;
	--font-size-small: 13px;
	--font-size-body: 16px;
	--font-size-medium: 20px;
	--font-size-large: 36px;
	--font-size-xlarge: 42px;

	/* Colors */
	--color-white: #ffffff;
	--color-black: #000000;
	--color-charcoal: #32373c;
	--color-blue: #0693e3;
	--color-teal: #00d084;
	--color-teal-light: #7bdcb5;
	--color-purple: #9b51e0;
	--color-orange: #ff6900;
	--color-amber: #fcb900;
	--color-red: #cf2e2e;
	--color-gray: #abb8c3;
	--color-pink: #f78da7;
	--color-blue-light: #8ed1fc;

	/* Spacing */
	--spacing-xs: 0.44rem; /*  ~7px */
	--spacing-sm: 0.67rem; /* ~11px */
	--spacing-md: 1rem; /*  16px */
	--spacing-lg: 1.5rem; /*  24px */
	--spacing-xl: 2.25rem; /*  36px */
	--spacing-2xl: 3.38rem; /* ~54px */
	--spacing-3xl: 5.06rem; /* ~81px */

	/* Layout */
	--content-width: 800px;
	--wide-width: 1200px;
	--block-gap: 24px;

	/* Shadows */
	--shadow-natural: 6px 6px 9px rgba(0, 0, 0, 0.2);
	--shadow-deep: 12px 12px 50px rgba(0, 0, 0, 0.4);
	--shadow-sharp: 6px 6px 0px rgba(0, 0, 0, 0.2);

	/* Border Radius */
	--radius-small: 4px;
	--radius-card: 5px;
	--radius-medium: 8px;
	--radius-pill: 9999px;
}
```

---

## 14. Do's and Don'ts

### Do

- Use **Figtree** for all text — headings and body
- Keep layouts **clean and spacious** — generous whitespace
- Use **flat design** — minimal shadows, no heavy gradients on UI elements
- Alternate image/text layout direction between sections
- Use **uppercase** for h3–h6 subheadings
- Keep CTA buttons in **dark charcoal** (`#32373C`) for consistency
- Use **#0693E3** as the primary interactive/link color

### Don't

- Don't use more than 2 accent colors per page
- Don't use heavy drop shadows — the design is intentionally flat
- Don't use fonts other than Figtree
- Don't exceed 1200px for content sections (except full-bleed heroes)
- Don't use colored backgrounds on text sections — keep them white
- Don't undersize spacing — the design breathes with generous padding (80px between sections)
