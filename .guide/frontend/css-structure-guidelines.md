# CSS Structure Guidelines

## File Organization
- Place all global styles in `App.css`.
- Use component-level CSS modules or styled-components for local styles.
- Keep variables and theme definitions at the top of CSS files.

## Reset & Base Styles
- Use universal selector `*` for box-sizing, margin, and padding reset.
- Set base font, background, and color on `body`.
- Hide scrollbars but ensure scrolling works.

## Responsive Design
- Use media queries for breakpoints at 1200px, 768px, and 480px.
- Use `.container` and `.section-padding` utility classes for layout.

## Animations
- Use `fadeIn` and `slideInUp` keyframes for entry animations.
- Apply `.fade-in` and `.slide-in-up` classes as needed.

## Best Practices
- Use CSS variables for all colors and spacing.
- Keep CSS DRY and modular.
- Comment sections for clarity.
