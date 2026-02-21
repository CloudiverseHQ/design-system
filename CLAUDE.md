# Design System — Monorepo

Monorepo managed with **pnpm workspaces**.

## Packages

| Path | Package | Description |
|------|---------|-------------|
| [packages/css](packages/css/CLAUDE.md) | `@design-system/css` | Modular token-based CSS design system |

## Directory Conventions

| Directory | Purpose | Published to npm? |
|-----------|---------|-------------------|
| `packages/` | Shared, reusable libraries (CSS, component libs, utilities) | Yes |
| `apps/` | End-user applications (web apps, demo sites, docs) | No |
| `tools/` | Build scripts, generators, CLI tools for the monorepo | No |

## Creating a New Package from Scratch

1. Create the directory: `packages/<name>/`, `apps/<name>/`, or `tools/<name>/`
2. Add a `package.json` with `"name": "@design-system/<name>"`
3. Add a `CLAUDE.md` documenting conventions for that package
4. Run `pnpm install` from the root to link workspaces

## Importing an External Project

To bring an existing external project into the monorepo:

1. **Copy the project** into the appropriate subdirectory:
   ```bash
   cp -r /path/to/external-project apps/<name>
   # or for a package:
   cp -r /path/to/external-project packages/<name>
   ```

2. **Update its `package.json`** name to follow the workspace convention:
   ```json
   { "name": "@design-system/<name>" }
   ```

3. **Add a `CLAUDE.md`** to the package documenting its conventions (if it doesn't have one)

4. **Run `pnpm install`** from the monorepo root to link the new workspace:
   ```bash
   pnpm install
   ```

5. **Verify** the package is recognized:
   ```bash
   pnpm --filter @design-system/<name> <cmd>
   ```

> **Git submodules:** If the external project must keep its own independent git history, use a submodule instead:
> `git submodule add <repo-url> packages/<name>`

## Cross-Package Dependencies

To use one workspace package from another (e.g., an app consuming the CSS package):

```json
// apps/my-app/package.json
{
  "dependencies": {
    "@design-system/css": "workspace:*"
  }
}
```

Then run `pnpm install` from root. pnpm will symlink the local package instead of fetching from npm.

From the CLI:
```bash
pnpm --filter @design-system/my-app add @design-system/css --workspace
```

## Using the Design System in External Projects

To consume `@design-system/css` from a separate project without copying files:

### Method 1: `pnpm link --global` (recommended — for projects with npm/pnpm)

**Prerequisites:** Run `pnpm setup` once and open a new terminal so `PNPM_HOME` is in PATH.

**One-time setup — run from inside `packages/css/`:**
```bash
cd packages/css
pnpm link --global
```

**In each consumer project** (run from the consumer project root):
```bash
pnpm link --global @design-system/css
```

This creates a symlink at `node_modules/@design-system/css` → `packages/css/` here. Changes in the design system are immediately reflected — no reinstall needed.

Import in HTML:
```html
<link rel="stylesheet" href="node_modules/@design-system/css/src/index.css">
```

Or via a bundler (Vite, webpack, etc.):
```js
import '@design-system/css/src/index.css'
```

To remove the link from a consumer: `pnpm unlink --global @design-system/css`

### Method 2: Direct path reference (for HTML-only projects, no npm)

Reference the CSS file by relative path — no tooling required:
```html
<link rel="stylesheet" href="../design-system/packages/css/src/index.css">
```

Adjust the path to match the actual directory relationship between the two projects.

### Consumer project CLAUDE.md snippet

Add this to the consumer project's `CLAUDE.md` so Claude Code knows the design system is in use:

```markdown
## Design System

This project uses `@design-system/css` linked from the local design system monorepo.

- **CSS import:** `<link rel="stylesheet" href="node_modules/@design-system/css/src/index.css">`
- **AI reference:** `C:/Users/ADMIN-USER/Documents/GitHub/design-system/packages/css/docs/ai-reference.md`
- **Contributor guide:** `C:/Users/ADMIN-USER/Documents/GitHub/design-system/packages/css/CLAUDE.md`

Read the AI reference before generating any HTML/CSS that uses design system classes or tokens.
```

## Workspace Commands

```bash
pnpm install                                   # Install all workspace deps
pnpm --filter @design-system/css <cmd>         # Run command in a specific package
pnpm -r <cmd>                                  # Run command in all packages
pnpm --filter @design-system/my-app add pkg    # Add a dep to a specific package
```

## Workspace Structure

```
design-system/
├── package.json           # Workspace root (private)
├── pnpm-workspace.yaml    # Declares packages/*, apps/*, tools/*
├── packages/              # Publishable packages
│   └── css/               # @design-system/css — see packages/css/CLAUDE.md
├── apps/                  # Applications (internal, not published)
└── tools/                 # Build tools, scripts, generators
```
