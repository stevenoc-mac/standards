# AGENTS.md - [Project Name]

Inherits all rules from: https://github.com/stevenoc-mac/standards/blob/main/AGENTS.md

## Project Overview

[Describe what this project does in 2-3 sentences]

## Stack

- Frontend: Next.js 14 (App Router), TypeScript, Tailwind CSS
- Database: Neon (Postgres) via Drizzle ORM
- Deployment: Vercel
- Auth: [Clerk / none]

## Project Structure

```
/app/api          - API routes
/app/(app)        - Authenticated app pages
/app/(marketing)  - Public marketing pages
/components/ui    - shadcn/ui components
/components/app   - App-specific components
/db               - Drizzle schema and migrations
/lib              - Utilities and helpers
/tests            - Tests
```

## Key Files

- `db/schema.ts` - Database schema
- `lib/db.ts` - Database client
- `lib/auth.ts` - Auth helpers

## Environment Variables

See `.env.example` for required variables.

## Running Locally

```bash
npm install
cp .env.example .env.local
# fill in .env.local values
npm run db:migrate
npm run dev
```

## Testing

```bash
npm test           # unit tests
npm run test:e2e   # playwright e2e tests
```

## Deployment

Vercel. PRs get preview deployments automatically. Merging to main deploys to production.
