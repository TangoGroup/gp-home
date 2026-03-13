# CLAUDE.md

This file provides guidance to Claude Code when working with code in this repository.

## Git Operations

**ALWAYS ask for explicit user confirmation before running any git commands that modify history or remote state**, including:
- `git commit`
- `git push`
- `git merge`
- `git rebase`
- `git reset`

## Commands

### Development
- `pnpm dev` - Start the development server
- `pnpm build` - Build for production
- `pnpm start` - Start production server

### Code Quality
- `pnpm lint` - Run ESLint checks
- `pnpm format` - Run Biome formatter
- `pnpm typecheck` - Run TypeScript type checking

### Testing
- `pnpm test` - Run all tests
- `pnpm test:watch` - Watch mode
- `pnpm test:coverage` - Coverage report

### Database
- `pnpm db:generate` - Generate migrations from schema
- `pnpm db:migrate` - Apply migrations
- `pnpm db:push` - Push schema to database
- `pnpm db:studio` - Open Drizzle Studio

## Architecture

### Project Overview
gp-home is a standalone Next.js application.

### Standalone Structure
```
gp-home/
├── app/                         # Pages, layouts, route handlers
├── components/                  # UI components and providers
├── lib/                         # Shared utilities, logging, analytics
├── db/                          # Drizzle schema and clients (if DB enabled)
├── __tests__/                   # Vitest test suites and helpers
├── .claude/                     # Claude Code settings and skills
├── .cursor/                     # Cursor settings and rules
└── HALOO_RECOMMENDATIONS.md     # Human-friendly AI usage guide
```

### Tech Stack
- **Framework**: Next.js 15 with App Router
- **UI**: React 19, shadcn/ui, Tailwind CSS v4
- **Database**: PostgreSQL, Drizzle ORM
- **Auth**: Simple cookie-based authentication
- **Testing**: Vitest
- **Linting**: ESLint
- **Formatting**: Biome
- **Analytics**: PostHog (optional)

## Key Conventions

- **Path aliases**: Use `@/*` for project-root imports.
- **Logging**: Use `@/lib/logger/server` or `@/lib/logger/client` instead of `console.log`.
- **Services Layer**: Keep database access in service modules instead of route handlers or UI components.
- **Formatting**: Use Biome formatting; do not mix with Prettier.

## Environment Variables

Required (stored in `.env.local`):
- No auth env vars required for simple auth
- `DATABASE_URL` - PostgreSQL connection string (required when database is enabled)
- `NEXT_PUBLIC_POSTHOG_KEY` - PostHog analytics (optional)

## Pull Request Workflow

Recommended flow:
1. Create a feature branch before making changes.
2. Use commits as small, meaningful save points.
3. Open a PR with a clear summary and test plan.

Commit prefixes:
- `feat:` New feature
- `fix:` Bug fix
- `chore:` Maintenance/refactor
- `docs:` Documentation update

## Recommended AI Setup

See `HALOO_RECOMMENDATIONS.md` for a plain-language guide on:
- How skills work
- How to ask the AI for common tasks
- Git and PR basics
- Browser testing workflow
- Optional MCP integrations
