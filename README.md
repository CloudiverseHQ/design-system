# Design System

A monorepo for the design system and related tooling, managed with pnpm workspaces.

## Packages

| Package | Path | Description |
|---------|------|-------------|
| `@cloudiverse/design-system` | [packages/css](packages/css/README.md) | Modular token-based CSS design system |

## Getting Started

```bash
# Install all workspace dependencies
pnpm install
```

## Quick Start (CSS only)

```html
<!-- Fonts -->
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link href="https://fonts.googleapis.com/css2?family=Geist:wght@400;500;600;700&family=Roboto+Mono:wght@400;500&display=swap" rel="stylesheet" />

<!-- Design System -->
<link rel="stylesheet" href="packages/css/src/index.css" />
```

See [packages/css/README.md](packages/css/README.md) for full CSS design system documentation.
