# AGENTS.md - Universal AI Agent Standards

This file is read by all AI agents (Claude, Codex, Cursor, etc.) working on any project
in the stevenoc-mac GitHub organisation. All projects inherit these rules.

Project-specific AGENTS.md files may add to these rules but must not contradict them.

---

## Core Principles

1. **Never push directly to main.** All changes go via pull request.
2. **Tests are not optional.** Every feature, API route, and utility must have tests.
3. **Type safety always.** No `any` in TypeScript. No untyped Python functions.
4. **Fail loudly.** Errors must be surfaced, logged, and handled - never silently swallowed.
5. **Small PRs.** One concern per PR. Easier to review, easier to revert.

---

## Stack Defaults (unless project AGENTS.md overrides)

- **Frontend:** Next.js (App Router), TypeScript, Tailwind CSS
- **Backend:** Next.js API routes or FastAPI (Python)
- **Database:** Neon (Postgres) via `@neondatabase/serverless`
- **Deployment:** Vercel
- **Auth:** Clerk (if auth needed)
- **ORM:** Drizzle ORM

---

## Testing Requirements

- **Unit tests:** Jest (TypeScript) or pytest (Python)
- **E2E tests:** Playwright
- **Coverage:** Minimum 80% on new code
- **Required:** All API routes must have at least one test
- **Required:** All utility functions must have unit tests
- CI must pass before merging any PR

---

## Repository Defaults

- Always create repos as **private** by default
- Only make public when explicitly requested

## Git Conventions

- Branch naming: `feat/description`, `fix/description`, `chore/description`
- Commit messages: imperative tense - "add feature" not "added feature"
- PR titles must describe the change, not the file edited
- No merge commits - rebase only
- Squash commits on merge to main

---

## Code Style

### TypeScript / JavaScript
- ESLint + Prettier enforced via CI
- No `console.log` in production code - use a logger
- No hardcoded secrets - use environment variables
- Prefer `const` over `let`, avoid `var`
- Use standard dash (-) not em dash in strings/copy

### Python
- Black formatter
- Type hints on all functions
- Docstrings on all public functions
- No bare `except` clauses

---

## Environment Variables

- Never commit `.env` files
- Every project must have `.env.example` with all required vars (no values)
- Document each var with a comment in `.env.example`
- Secret values go in Vercel environment settings or local keychain

---

## Project Structure (Next.js)

```
/app              - Next.js App Router pages and API routes
/components       - Reusable React components
/lib              - Shared utilities and helpers
/db               - Database schema (Drizzle) and migrations
/tests            - Test files mirror src structure
AGENTS.md         - Project-specific agent rules (inherits from standards)
.env.example      - Required environment variables
```

---

## CI/CD (GitHub Actions)

Every project must have these workflows:

- `ci.yml` - runs on PR: lint, typecheck, tests
- `deploy-preview.yml` - deploys preview to Vercel on PR
- `deploy-prod.yml` - deploys to Vercel on merge to main

Templates in `/ci-templates/` in this repo.

---

## AI Agent Behaviour

When working on any project:

1. Read this file and the project-level AGENTS.md before starting
2. Read recent memory files for context on what's been built
3. Always run tests before marking a task complete
4. Never delete files without explicit instruction
5. Create a PR - never push to main directly
6. Leave clear PR descriptions explaining what changed and why
7. If uncertain about a design decision, stop and ask rather than guess
8. Update project MEMORY.md with significant decisions made

---

## Security

- No secrets in code or commits - ever
- No `eval()` or dynamic code execution with user input
- Sanitise all user input before database queries
- Use parameterised queries - never string interpolation in SQL
- HTTPS only in production
