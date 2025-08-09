# Theme Usage Guidelines

## Dark Theme (Default)
- **Text Colors:**
  - Primary: #FFFFFF
  - Secondary: #F8F5FF
  - Muted: #B3B3B3
  - Accent: #C7B3FF
- **Background Colors:**
  - Primary: #0E0E0E
  - Secondary: #191919
  - Tertiary: #333333
  - Blur: rgba(0, 0, 0, 0.1)
- **Borders & Shadows:**
  - Border: rgba(255, 255, 255, 0.1)
  - Shadows: purple-tinted, soft to strong

## Light Theme
- **Text Colors:**
  - Primary: #1a1a1a
  - Secondary: #2d2d2d
  - Muted: #666666
  - Accent: #6933FF
- **Background Colors:**
  - Primary: #ffffff
  - Secondary: #f8f9fa
  - Tertiary: #e9ecef
  - Blur: rgba(255, 255, 255, 0.8)
- **Borders & Shadows:**
  - Border: rgba(0, 0, 0, 0.1)
  - Shadows: lighter purple-tinted

## Implementation
- Use `[data-theme="dark"]` and `[data-theme="light"]` selectors in CSS.
- Switch themes by toggling the `data-theme` attribute on the root element.
- All color variables should be referenced via `var(--color-name)`.

## Accessibility
- Ensure text/background contrast meets WCAG AA.
- Test both themes for readability and clarity.
