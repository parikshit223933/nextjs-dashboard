# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

**Development:**
```bash
npm run dev      # Run development server with Turbopack
npm run build    # Build for production
npm run start    # Run production server
```

## Architecture

This is a Next.js 15+ dashboard application using the App Router pattern with PostgreSQL database.

**Key Architectural Patterns:**

1. **App Router Structure**: Uses Next.js App Router with `(overview)` route groups for organizing dashboard pages. Routes are located in `app/` directory.

2. **Data Fetching**: Server components fetch data directly using the `postgres` library in `app/lib/data.ts`. Database queries use PostgreSQL with environment variable `POSTGRES_URL` for connection.

3. **Suspense & Loading States**: Components use React Suspense boundaries with skeleton loaders (`app/ui/skeletons.tsx`) for async data fetching. Example pattern visible in `app/dashboard/(overview)/page.tsx`.

4. **Component Organization**:
   - UI components: `app/ui/` - Reusable UI components organized by feature (dashboard, invoices, customers)
   - Data layer: `app/lib/` - Database queries, type definitions, and utilities
   - Fonts: Custom fonts loaded via `app/ui/fonts.ts` using Next.js font optimization

5. **Styling**: Tailwind CSS with custom configuration, using `@tailwindcss/forms` plugin for form styling.

6. **TypeScript Configuration**: Strict mode enabled, using path alias `@/*` for imports from root directory.

## Database Schema

The application works with these main entities:
- **Revenue**: Monthly revenue data for charts
- **Invoices**: Invoice records linked to customers
- **Customers**: Customer information with associated invoices

## Important Notes

- Database includes artificial delays in some queries for demo purposes (see `fetchRevenue()` in `app/lib/data.ts`)
- Project uses the `postgres` npm package for database connections
- Authentication setup available via `next-auth` (beta version)