# @tale-ui/core

[![Publish design system](https://github.com/Tale-UI/core/actions/workflows/publish.yml/badge.svg)](https://github.com/Tale-UI/core/actions/workflows/publish.yml)

The foundational CSS layer of the Tale UI Design System — design tokens, layout utilities, and theming primitives. Framework-agnostic, no build tools required.

> **Scope:** This package provides the *foundations* — tokens, layout, utilities, and theming. It does **not** include UI components (buttons, modals, forms, etc.). Component libraries are separate packages that depend on this one.

## Features

- **Fluid design tokens** — Spacing and typography scale smoothly with `clamp()`
- **Modular CSS** — 20+ focused modules composed via `@import`
- **16 colour families** with 11 shades each, plus 6 neutral tone families
- **Dark mode** — Auto-inverting neutral scale via `data-color-mode` attribute
- **Responsive** — 4 breakpoints (480, 768, 992, 1600px) with utility variants
- **No build tools required** — CSS `@import` works natively in modern browsers

---

## Installation

```bash
npm install @tale-ui/core
```

### Bundler (Next.js, Vite, webpack)

```css
@import '@tale-ui/core';
```

### Plain HTML

```html
<link rel="stylesheet" href="node_modules/@tale-ui/core/dist/style.css">
```

> **Framework note:** This design system sets `html { font-size: 62.5% }` (1rem = 10px). If using Tailwind, shadcn/ui, or Bootstrap, add `html { font-size: 100%; }` after the import to restore their default rem scale. See the [Framework Integration Guide](packages/css/docs/framework-integration.md) for details.

---

## Quick Start

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <!-- Fonts -->
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Geist:wght@400;500;600;700&family=Roboto+Mono:wght@400;500&display=swap" rel="stylesheet" />

  <!-- Design System -->
  <link rel="stylesheet" href="node_modules/@tale-ui/core/dist/style.css" />
</head>
<body>

  <!-- Responsive grid -->
  <div class="grid--3 grid--l-2 grid--m-1 gap--l gap--m-m">
    <div>Item 1</div>
    <div>Item 2</div>
    <div>Item 3</div>
  </div>

  <!-- Themed section -->
  <section class="color-purple neutral-cool padding--l">
    <h1 class="text--display-l">Hello</h1>
    <p class="text--body-l">Welcome to the design system.</p>
  </section>

</body>
</html>
```

### Dark Mode

```html
<html data-color-mode="dark">
```

---

## Documentation

| Resource | Description |
|----------|-------------|
| [Changelog](CHANGELOG.md) | Versioned release notes and commit summaries |
| [AI Reference](packages/css/docs/ai-reference.md) | Every valid class, token, and value — read this before generating code |
| [Framework Integration](packages/css/docs/framework-integration.md) | Using alongside Tailwind, shadcn/ui, Next.js, Vite, etc. |
| [Visual Docs](packages/css/docs/documentation.html) | Interactive component demos (open locally in browser) |
| [Contributor Guide](packages/css/CLAUDE.md) | Architecture, conventions, and how to extend the system |

---

## Packages

| Package | Path | Description |
|---------|------|-------------|
| `@tale-ui/core` | [packages/css](packages/css) | Modular token-based CSS design system |

## Release Workflow (npm + GitHub in sync)

Use the root release script so package version, git tag, and GitHub release always match.

CI is configured in `.github/workflows/publish.yml` to publish when a semver tag is pushed (`vX.Y.Z`).
The workflow verifies `packages/css/package.json` version equals the tag version before publishing.

### One-time setup

Add repository secret `NPM_TOKEN` in GitHub settings.

### Standard patch release

```bash
pnpm release:css:patch
```

### Minor / major release

```bash
pnpm release:css:minor
pnpm release:css:major
```

### Explicit version release

```bash
pnpm release:css -- --version 1.0.2
```

### Preview only (no changes)

```bash
pnpm release:css:dry-run
```

## License

MIT
