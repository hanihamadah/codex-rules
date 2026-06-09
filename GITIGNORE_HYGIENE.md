# Gitignore Hygiene

Last updated: 2026-06-09

The intended workspace `.gitignore` hygiene update is blocked by macOS/iCloud
permissions on the existing `.gitignore` file.

Observed blocker:

```text
Operation not permitted
```

Metadata inspection showed:

```text
.gitignore has the hidden file flag and com.apple.provenance attribute
```

Attempts to update the file, remove the hidden flag, and remove the provenance
attribute were all blocked. The `.env.local` file was not opened.

## Intended `.gitignore`

```gitignore
# macOS
.DS_Store

# Local secrets and environment files
.env
.env.*
!.env.example
!.env.sample
.dev.vars
.dev.vars.*

# Dependencies
node_modules/

# Build and generated app output
dist/
build/
.next/
.nuxt/
.svelte-kit/
.vite/
.vite-temp/

# Test and coverage output
test-results/
playwright-report/
coverage/
.nyc_output/

# TypeScript and tooling caches
*.tsbuildinfo
.tscache/
.cache/
.turbo/

# Cloud and deployment tool state
.wrangler/
.mf/
.vercel/
.netlify/

# Logs
*.log
npm-debug.log*
yarn-debug.log*
yarn-error.log*
pnpm-debug.log*

# Python caches
__pycache__/
*.py[cod]
.pytest_cache/

# Editor and local machine state
.idea/
.vscode/
*.swp
*.swo
```

## Why These Patterns

- Protects `.env.local` and related secret-bearing environment files.
- Prevents `node_modules/` from appearing as commit noise.
- Hides build output such as `dist/`, `build/`, and framework caches.
- Hides Playwright/test/coverage output.
- Hides TypeScript incremental build cache files.
- Hides deployment tool state from Cloudflare, Vercel, and Netlify.
- Keeps teaching deliverables, PDFs, DOCX files, Markdown files, and project
  source folders visible unless a project-specific decision says otherwise.

## Resolution Needed

When macOS/iCloud permissions allow edits to `.gitignore`, replace the current
single-line `.DS_Store` file with the intended content above.
