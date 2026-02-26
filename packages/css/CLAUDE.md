# @tale-ui/core

A modular, token-based CSS design system. Framework-agnostic, no build tools required for development.

## Project Structure

```
src/
├── index.css         # Entry point — tokens → foundations → layout → utilities → themes
├── tokens/           # CSS custom properties (spacing, typography, colors, neutrals, effects)
├── foundations/      # Typography classes and base element defaults
├── layout/           # Gap, grid, flex, centering (all with responsive variants)
├── utilities/        # Display, visual, position, sizing, border, spacing
└── themes/           # Neutral families, color families, dark mode
```

## Documentation

| File | What it covers |
|------|----------------|
| [docs/architecture.md](docs/architecture.md) | Module structure, import order, specificity patterns, adding new utilities |
| [docs/naming-conventions.md](docs/naming-conventions.md) | Utility class syntax, responsive variants, theme classes, BEM |
| [docs/design-tokens.md](docs/design-tokens.md) | Spacing, typography, color system, neutral system, effects, dark mode |
| [docs/building-components.md](docs/building-components.md) | Component patterns, BEM usage, import methods, required fonts |
| [docs/ai-reference.md](docs/ai-reference.md) | Complete class/token enumeration, valid shade numbers, responsive coverage matrix |
| [docs/framework-integration.md](docs/framework-integration.md) | Tailwind, shadcn/ui, Next.js, Vite, PostCSS setup — including the `62.5%` font-size issue |
