# Tale UI Core — Monorepo

Monorepo managed with **pnpm workspaces**. This repository is the single source of truth for the Tale UI Design System and its supporting tooling.

## Packages

| Path | Package | Description |
|------|---------|-------------|
| [packages/css](packages/css/CLAUDE.md) | `@tale-ui/core` | Modular token-based CSS design system |

## Documentation

| File | What it covers |
|------|----------------|
| [docs/workspace-structure.md](docs/workspace-structure.md) | Directory layout, conventions, and workspace CLI commands |
| [docs/managing-packages.md](docs/managing-packages.md) | Creating new packages and importing external projects |
| [docs/package-dependencies.md](docs/package-dependencies.md) | Cross-package `workspace:*` dependencies |
| [docs/consuming-design-system.md](docs/consuming-design-system.md) | Installing in external projects (npm, pnpm link, direct path) + consumer `CLAUDE.md` snippet |
