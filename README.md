# Shopify Liquid Theme - Block-Based Architecture

A modern, component-driven Shopify theme built from scratch using theme blocks. This theme leverages Shopify's block system to create highly flexible, reusable, and customizable components for building rich e-commerce experiences.

## 🎯 Project Approach

This theme is developed using a **block-first architecture**, where every component is built as an independent, reusable block. This approach provides:

- **Modularity**: Each block (text, image, group, button, badge, icon) is self-contained with its own settings and logic
- **Flexibility**: Merchants can combine blocks to create custom layouts without touching code
- **Maintainability**: Changes to a block automatically propagate across all instances
- **Scalability**: New blocks can be added without affecting existing functionality

## ✨ Key Features

### 🖼️ Image Blocks with Overflow Capabilities

The image block includes a powerful **"leak" feature** that allows images to overflow their container boundaries:

- Control overflow on all four sides (top, bottom, left, right)
- Separate configurations for desktop and mobile viewports
- Perfect for creating dynamic, overlapping layouts
- Advanced `object-fit` options: cover, contain, fill, and **leak mode**

Example leak configuration from the blocks:
- Desktop: `image_leak_left_desktop: 41%` - image extends 41% beyond its left boundary
- Mobile: `image_leak_bottom_mobile: 76%` - image extends 76% below its container

This enables creative hero sections where images dramatically break out of traditional grid constraints.

### 📝 Fully Customizable Text Blocks

Text blocks offer extensive styling options for typography and appearance:

**Typography Controls:**
- Font family selection (Helvetica Neue, Product Sans)
- HTML tag selection (p, h1-h6)
- Custom font sizes for desktop and mobile
- Font weight control (100-900)
- Text styles: italic, normal
- Text decorations: underline, overline, line-through
- Text transforms: uppercase, lowercase, capitalize
- Line height and letter spacing adjustments

**Color & Effects:**
- Predefined color schemes (heading primary/secondary, body colors, accent colors)
- Custom color support
- **Gradient text effects** on bold text
- Separate color settings for mobile devices
- Color inheritance from parent containers

**Layout:**
- Text alignment options for desktop and mobile
- Responsive font sizes
- Mobile-specific styling overrides

### 📦 Totally Responsive Group Blocks

Group blocks function as powerful layout containers with full responsive control:

**Flexbox Layout:**
- Direction control: row, column, row-reverse, column-reverse
- Separate direction settings for desktop and mobile
- Alignment options: start, center, end, stretch
- Justify content: start, center, end, between, around, evenly
- Configurable gap between child elements

**Visual Styling:**
- Background colors and gradients
- Border colors and gradient borders
- Border radius (separate for desktop/mobile)
- Border width control

**Spacing System:**
- Responsive padding (inline and block)
- Independent left/right padding control
- Independent top/bottom padding control
- Fluid spacing using CSS clamp functions

**Responsive Width:**
- Preset widths: 100%, fit-content, container width
- Custom percentage widths
- Separate width settings for mobile
- Nested groups for complex layouts

**Adaptive Design:**
- Mobile-first approach
- Smooth transitions between breakpoints
- Automatic content reflow on smaller screens

## 📁 Project Structure

```
/
├── assets/                      # Static assets
│   ├── *.css                   # Component-specific CSS
│   ├── *.svg                   # SVG icons and graphics
│   └── *.otf, *.ttf           # Custom fonts (Helvetica Neue, Product Sans)
│
├── blocks/                      # Reusable theme blocks
│   ├── badge.liquid            # Badge component
│   ├── button.liquid           # Button component
│   ├── group.liquid            # Container/layout block
│   ├── icon.liquid             # Icon component
│   ├── image.liquid            # Image block with overflow features
│   └── text.liquid             # Text block with extensive styling
│
├── config/                      # Theme configuration
│   ├── settings_data.json      # Theme settings values
│   └── settings_schema.json    # Settings UI definition
│
├── layout/                      # Theme layout templates
│   └── theme.liquid            # Main theme wrapper
│
├── locales/                     # Internationalization
│   ├── en.default.json         # Translation strings
│   └── en.default.schema.json  # Schema translations
│
├── sections/                    # Section templates
│   ├── custom-section.liquid   # Main custom section with presets
│   ├── footer-group.json       # Footer section
│   └── header-group.json       # Header section
│
├── snippets/                    # Reusable code snippets
│   ├── button.liquid           # Button rendering logic
│   ├── design.*.liquid         # Design system utilities
│   ├── group.liquid            # Group rendering logic
│   ├── icon.liquid             # Icon rendering logic
│   ├── text.liquid             # Text rendering logic
│   ├── sourceset.liquid        # Responsive image sourceset generator
│   └── variables-*.liquid      # CSS variable generators
│
└── templates/                   # Page templates
    ├── *.json                  # JSON-based page templates
    └── customers/              # Customer account templates
```

## 🧩 Block System Architecture

### Core Blocks

1. **Group Block** (`blocks/group.liquid`)
   - Container for other blocks
   - Flexbox-based layout system
   - Full responsive control
   - Color schemes and backgrounds
   - Borders and spacing

2. **Text Block** (`blocks/text.liquid`)
   - Rich text rendering
   - Extensive typography options
   - Gradient text effects
   - Mobile-specific overrides

3. **Image Block** (`blocks/image.liquid`)
   - Responsive images with srcset
   - Mobile-specific image variants
   - **Overflow/leak functionality**
   - Multiple object-fit modes

4. **Button Block** (`blocks/button.liquid`)
   - Multiple button styles (primary, secondary, tertiary)
   - Customizable sizing
   - Link support

5. **Badge Block** (`blocks/badge.liquid`)
   - Icon badges
   - Decorative elements

6. **Icon Block** (`blocks/icon.liquid`)
   - SVG and image icons
   - Responsive sizing

### Block Composition

Blocks can be nested to create complex layouts. Example from the hero preset:

```
Section (custom-section)
└── Group (full-width container)
    ├── Group (content area - 38% width)
    │   └── Group (text content)
    │       ├── Badge
    │       ├── Text (heading with gradient)
    │       └── Group (CTA buttons)
    └── Group (image area - 62% width)
        └── Image (with 41% left overflow)
```

## 🎨 Design System

### Typography
- **Helvetica Neue**: Display and heading font
- **Product Sans**: Body and UI text font

### Color System
- CSS custom properties for consistent theming
- Color schemes: `scheme-1`, `scheme-2`, etc.
- Semantic color names:
  - Text: `--color-text-heading-primary`, `--color-text-body-primary`
  - Backgrounds: `--color-background-primary`, `--color-background-secondary`
  - Accents: `--color-accent-primary`, `--color-accent-secondary`

### Gradients
- `--gradient-primary`
- `--gradient-secondary`
- `--gradient-mute`

### Responsive Breakpoints
- Mobile: < 768px
- Desktop: ≥ 768px

### Fluid Typography
Uses CSS clamp functions (`design.clamp.liquid`) for smooth font scaling between viewport sizes.

## 🚀 Getting Started

### Prerequisites
- Shopify CLI installed
- Shopify Partner account and development store

### Development

1. Clone the repository:
```bash
git clone <repository-url>
cd dev-case-shopify-liquid-theme
```

2. Login to Shopify:
```bash
shopify login
```

3. Connect to your development store:
```bash
shopify theme dev
```

4. The theme will be served locally with hot reloading

### Deployment

```bash
shopify theme push
```

## 🔧 Customization

### Adding a New Block

1. Create a new `.liquid` file in `/blocks/`
2. Define the block schema with settings
3. Add rendering logic
4. The block automatically becomes available in sections

### Creating Section Presets

Section presets are pre-configured layouts stored in the section schema. See `custom-section.liquid` for examples of `hero` and `image_with_text` presets.

### Modifying Styles

Component-specific styles are in `/assets/`:
- `base.css` - Global styles and CSS variables
- `button.css` - Button styles
- `badge.css` - Badge styles
- `icon.css` - Icon styles

---

Built with ❤️ by Vinícius Bueno using Shopify Liquid and modern block architecture principles.

