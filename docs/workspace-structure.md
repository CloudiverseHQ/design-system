# Workspace Structure

This monorepo is managed with **pnpm workspaces**.

## Directory Conventions

| Directory | Purpose | Published to npm? |
|-----------|---------|-------------------|
| `packages/` | Shared, reusable libraries (CSS, component libs, utilities) | Yes |
| `apps/` | End-user applications (web apps, demo sites, docs) | No |
| `tools/` | Build scripts, generators, CLI tools for the monorepo | No |

## Directory Layout

```
core/
├── package.json           # Workspace root (private)
├── pnpm-workspace.yaml    # Declares packages/*, apps/*, tools/*
├── packages/              # Publishable packages
│   └── css/               # @tale-ui/core — see packages/css/CLAUDE.md
├── apps/                  # Applications (internal, not published)
└── tools/                 # Build tools, scripts, generators
```

## Workspace CLI Commands

```bash
pnpm install                                    # Install all workspace deps
pnpm --filter @tale-ui/core <cmd>              # Run command in a specific package
pnpm -r <cmd>                                   # Run command in all packages
pnpm --filter @tale-ui/my-app add pkg          # Add a dep to a specific package
```
