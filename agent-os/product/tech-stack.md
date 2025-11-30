# Tech Stack

## Framework & Runtime

### Application Framework
- **Framework:** Next.js (latest stable, App Router)
- **Language/Runtime:** TypeScript with Node.js 22 LTS
- **Package Manager:** npm

### Frontend
- **JavaScript Framework:** React (via Next.js)
- **CSS Framework:** Tailwind CSS
- **UI Components:** shadcn/ui
- **Charts & Visualization:** Recharts
- **Icons:** Lucide React
- **Build Tool:** Next.js built-in (Turbopack/Webpack)

### Data Management (Frontend)
- **State Management:** React Context API / Zustand (if needed)
- **Form Handling:** React Hook Form with Zod validation
- **Data Tables:** TanStack Table (React Table v8)

## Database & Backend Services (Supabase)

### Database
- **Database:** Supabase PostgreSQL
- **ORM/Query Builder:** Supabase Client SDK
- **Migrations:** Supabase CLI migrations
- **Real-time:** Supabase Realtime subscriptions (for upload status, etc.)

### Authentication & Authorization
- **Authentication:** Supabase Auth
- **Authorization:** Supabase Row Level Security (RLS) policies
- **Role-Based Access:** Custom roles via Supabase

### Storage
- **File Storage:** Supabase Storage (for uploaded Excel/CSV files and generated exports)
- **Storage Policies:** Supabase Storage RLS policies for access control

### Backend Logic
- **API Routes:** Next.js API Routes (for complex operations)
- **Edge Functions:** Supabase Edge Functions (Deno) for:
  - Data validation logic
  - File processing triggers
  - Export generation
- **Database Functions:** PostgreSQL functions for complex queries and aggregations

## Data Processing (Project-Specific)

### File Processing Strategy
For this data infrastructure project, file processing is handled via:
- **Supabase Edge Functions:** Primary processing for Excel/CSV parsing and validation
- **Next.js API Routes:** Alternative for heavier processing if needed
- **Libraries:**
  - `xlsx` (SheetJS) for Excel parsing in Edge Functions/API Routes
  - `papaparse` for CSV parsing
  - `zod` for data validation schemas

### Export Generation
- **Excel Export:** `xlsx` (SheetJS) for generating formatted Excel files with multiple sheets
- **CSV Export:** Native JavaScript/`papaparse`
- **PDF Reports:** `@react-pdf/renderer` or html-to-pdf via Edge Function

### Data Validation
- **Schema Validation:** Zod schemas matching database structure
- **Business Rules:** Custom validation functions in Edge Functions
- **Error Reporting:** Structured validation error objects stored in database

## Testing & Quality

### Testing
- **Test Framework:** Jest / Vitest
- **Component Testing:** React Testing Library
- **E2E Testing:** Playwright (for critical upload/export workflows)
- **API Testing:** Vitest with Supabase local development

### Code Quality
- **Linting:** ESLint with TypeScript support
- **Formatting:** Prettier
- **Type Checking:** TypeScript strict mode
- **Database Types:** Supabase CLI generated types

## Deployment & Infrastructure

### Hosting
- **Application Hosting:** Vercel
- **Backend Services:** Supabase (managed)
- **Edge Functions:** Supabase Edge Functions (Deno Deploy)

### CI/CD
- **Deployments:** Vercel automatic deployments (GitHub integration)
- **Preview Deployments:** Automatic on pull requests
- **Database Migrations:** Supabase CLI in CI pipeline

### Monitoring & Observability
- **Frontend Analytics:** Vercel Analytics
- **Error Tracking:** Sentry
- **Database Monitoring:** Supabase Dashboard
- **Logs:** Supabase Edge Function logs, Vercel logs

## Development Environment

### Required Tools
- **Node.js:** v22 LTS
- **Supabase CLI:** Latest stable
- **Git:** Latest stable

### Local Development
- **Database:** Supabase local development (`supabase start`)
- **Environment Variables:** .env.local (never committed)

### Recommended IDE Setup
- **Editor:** VS Code
- **Extensions:** ESLint, Prettier, Tailwind CSS IntelliSense
- **Code Formatting:** Format on save enabled

## Third-Party Services

### Core Services
- **Backend as a Service:** Supabase
- **Hosting:** Vercel
- **Email:** Supabase Auth (transactional) or Resend
- **Monitoring:** Vercel Analytics / Sentry

## Notes on Tech Stack Choices

### Supabase-First Architecture
This project uses Supabase as the unified backend platform:
- **No separate backend server** - Supabase handles database, auth, storage, and serverless functions
- **Row Level Security** - Authorization logic lives in the database, not application code
- **Real-time capabilities** - Built-in for upload status updates and data refresh
- **Type safety** - Auto-generated TypeScript types from database schema

### Data Processing Approach
While Supabase handles core backend services, this project has significant data processing needs:
- **Edge Functions** handle file parsing, validation, and transformation
- **SheetJS (xlsx)** replaces Python Pandas for Excel processing - runs in Edge Functions
- **Validation schemas** in Zod mirror database constraints for client-side and server-side validation
- Processing happens on upload, with results stored in normalized database tables

### Export-First Design
The platform prioritizes data export for Bell & Associates' rate modeling:
- **Pre-built export packages** generated via database views and Edge Functions
- **Multiple formats** (Excel, CSV) supported via SheetJS
- **Custom export builder** uses Supabase queries with dynamic filters

### Infrastructure-First, Dashboard-Second
Aligns with mission - solid data infrastructure before visualization:
- **Database schema** designed for solid waste rate study data structures
- **Audit trails** via Supabase's built-in `created_at`/`updated_at` and custom history tables
- **Data lineage** documented in database and application code
- Dashboards added incrementally as budget allows
