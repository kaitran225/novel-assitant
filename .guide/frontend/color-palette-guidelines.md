# Color Palette Guidelines

This document describes the color palette and theme usage for the frontend of the application.

## Color Variables - Custom Palette

```css
:root {
  /* Primary Colors - 85% Black Dominance */
  --color-black-primary: #0E0E0E;
  --color-black-secondary: #191919;
  --color-black-tertiary: #333333;
  --color-gray-dark: #606060;
  /* Purple Accent - 10% Usage */
  --color-purple-primary: #6933FF;
  --color-purple-secondary: #7C4CFF;
  --color-purple-light: #8F66FF;
  --color-purple-accent: #A280FF;
  /* Green Accent - 5% Usage */
  --color-green-primary: #47D068;
  --color-green-secondary: #1C1C1C;
  --color-green-light: #66E1A8;
  --color-green-accent: #80E1B0;
}
```

## Theme Usage

- **Dark Theme (Default):**
  - Text: White, off-white, muted gray, purple accent
  - Background: Black, dark gray, blurred overlays
  - Shadows: Soft, medium, strong, glow, hover (purple tint)
- **Light Theme:**
  - Text: Black, dark gray, muted gray, purple accent
  - Background: White, light gray, blurred overlays
  - Shadows: Softer, lighter purple tint

## Best Practices
- Use variables for all colors in CSS/JSX.
- Maintain 85% black/gray dominance, 10% purple, 5% green.
- Use accent colors for highlights, buttons, and links.
- Ensure sufficient contrast for accessibility.
