# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Development Commands

```bash
# Start full development environment (frontend + backend)
npm run dev

# Run frontend only
npm run dev:frontend

# Run backend only (Convex dev server)
npm run dev:backend

# Build for production
npm run build

# Type-check and lint
npm run lint
```

## Architecture

This is a Convex + React template with authentication pre-configured.

### Tech Stack
- **Frontend**: React 19, Vite, Tailwind CSS
- **Backend**: Convex (serverless database and functions)
- **Auth**: @convex-dev/auth with Password and Anonymous providers

### Project Structure

**`convex/`** - Backend code (runs on Convex servers)
- `schema.ts` - Database schema definition (extends authTables)
- `auth.ts` - Authentication configuration and `loggedInUser` query
- `router.ts` - HTTP router for custom endpoints
- `http.ts` - Main HTTP entry point (adds auth routes to router)
- `_generated/` - Auto-generated Convex types and API (do not edit)

**`src/`** - Frontend React application
- `main.tsx` - App entry point with ConvexAuthProvider
- `App.tsx` - Main component with auth-aware UI

### Key Patterns

- Use `api` from `convex/_generated/api` to call Convex functions
- Use `Authenticated`/`Unauthenticated` components for conditional rendering
- Use `getAuthUserId(ctx)` in backend functions to get current user
- Define new tables in `applicationTables` object in `schema.ts`
- Add custom HTTP routes in `router.ts`

### Environment Variables
- `VITE_CONVEX_URL` - Convex deployment URL (set automatically by `convex dev`)
