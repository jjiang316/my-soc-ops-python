---
description: CSS utility classes and styling practices for this Python/Jinja2 project.
---

# CSS Styling Practices

## Overview
This project uses custom CSS utility classes defined in `app/static/css/app.css` with a "Ghost Protocol" dark theme — near-black void palette with CSS variables, CRT scanline overlay, and ghost animations. Font: Share Tech Mono (Google Fonts).

## CSS Variables (`:root`)
```css
/* Void palette */
--void: #080808;   --surface: #0c0c0c;   --elevated: #111111;   --hairline: #1a1a1a;
/* Ghost text — barely visible, brightens on interaction */
--text-ghost: #1a1a1a;  --text-dim: #2a2a2a;  --text-vis: #3a3a3a;  --text-bright: #4a4a4a;
/* Phosphor cyan accents */
--cyan-deep: #062222;  --cyan-mark: #0d3b3b;  --cyan-glow: #0a5a5a;  --cyan-bright: #0e7a7a;
/* Winning amber — kept dark */
--win-bg: #1a1400;  --win-border: #2a2200;  --win-text: #3d3300;  --win-glow: #4a3d00;
```

## Available Utilities

### Layout
```css
.flex, .flex-col, .flex-1
.grid, .grid-cols-5
.items-center, .justify-center, .justify-between
```

### Spacing
```css
/* Padding */
.p-1, .p-3, .p-4, .p-6
.px-3, .px-4, .px-6, .px-8
.py-1\.5, .py-2, .py-3, .py-4
/* Margin */
.mb-2, .mb-3, .mb-4, .mb-6, .mb-8, .mx-auto
/* Gap */
.gap-1, .space-y-2
```

### Sizing
```css
.h-full, .w-full, .w-16, .min-h-full
.max-w-xs, .max-w-sm, .max-w-md
.aspect-square
.min-h-[60px]
```

### Colors (Ghost Protocol — all mapped to CSS variables)
```css
/* Backgrounds */
.bg-white (var(--surface))
.bg-gray-50 (var(--void))
.bg-gray-100 (var(--elevated))
.bg-amber-100, .bg-amber-200 (var(--win-bg))
.bg-accent (var(--cyan-deep), hover: var(--cyan-mark))
.bg-marked (var(--cyan-deep))
.bg-void-overlay (rgba(0,0,0,0.92))
/* Text */
.text-white (var(--text-dim))
.text-gray-500, .text-gray-600 (var(--text-ghost))
.text-gray-700, .text-gray-800 (var(--text-dim))
.text-gray-900 (var(--text-vis))
.text-green-600 (var(--cyan-glow)), .text-green-800 (var(--cyan-mark))
.text-amber-500 (var(--win-glow)), .text-amber-800, .text-amber-900 (var(--win-text))
```

### Typography
```css
.text-xs, .text-sm, .text-lg, .text-3xl, .text-4xl, .text-5xl
.font-semibold, .font-bold
.text-center, .text-left
.leading-tight
.uppercase, .tracking-widest, .tracking-wide
```

### Borders & Shadows
```css
.border, .border-b
.border-gray-200, .border-gray-300 (var(--hairline))
.border-amber-400 (var(--win-border))
.border-marked-border (var(--cyan-deep))
.rounded, .rounded-lg, .rounded-xl
.shadow-sm, .shadow-xl (cyan-tinted glows)
.shadow-glow, .shadow-glow-win
.glow-marked (cyan box-shadow + border)
```

### Positioning
```css
.fixed, .absolute, .relative
.inset-0
.top-0\.5, .right-0\.5
.z-50
```

### Interactivity
```css
.select-none
.wrap-break-word
.hyphens-auto
.hover-brighten (brightens text + adds text-shadow on hover)
```

### Animation
```css
.transition-all, .transition-colors (300ms)
.animate-ghost-pulse (winning squares breathe)
.animate-fade-from-void (modal entrance)
.animate-grid-reveal (board squares appear)
.delay-0 through .delay-24 (staggered grid reveal, 30ms increments)
```

## Best Practices

1. **Compose utilities**: Combine classes for complex layouts
2. **Add new utilities to app.css**: When needed, follow existing patterns
3. **Use CSS variables**: All colors reference `:root` variables — override there for theming
4. **Keep specificity low**: Utility classes should be single-purpose
5. **Add `hover-brighten`** to text elements that should reveal on hover

## Example Component Styling
```html
<div class="flex flex-col items-center justify-center min-h-full bg-gray-50">
    <button class="px-6 py-3 bg-accent text-white rounded-lg font-semibold uppercase tracking-wide hover-brighten">
        Initiate
    </button>
</div>
```