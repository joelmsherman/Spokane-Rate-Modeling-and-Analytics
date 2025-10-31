# Tech Stack

## Framework & Runtime

### Frontend
- **JavaScript Framework:** React 18+
- **Application Framework:** Next.js 14+ (App Router)
- **Language/Runtime:** TypeScript with Node.js 22 LTS
- **Package Manager:** npm

### Backend
- **API Framework:** Python 3.11+ with FastAPI
- **Language/Runtime:** Python 3.11+
- **Package Manager:** pip with requirements.txt (or poetry)
- **ASGI Server:** Uvicorn

## Frontend Stack

### UI & Styling
- **CSS Framework:** Tailwind CSS
- **UI Component Library:** shadcn/ui
- **Charts & Visualization:** Recharts (primary choice for dashboards)
- **Icons:** Lucide React
- **Build Tool:** Next.js built-in (Turbopack/Webpack)

### Data Management
- **API Client:** Fetch API / Axios
- **State Management:** React Context API / Zustand (if needed)
- **Form Handling:** React Hook Form with Zod validation
- **Data Tables:** TanStack Table (React Table v8)

## Backend Stack

### API & Business Logic
- **API Framework:** FastAPI
- **Validation:** Pydantic models
- **Async Runtime:** asyncio
- **API Documentation:** FastAPI automatic OpenAPI/Swagger

### Data Processing
- **Data Transformation:** Pandas for ETL, data cleaning, and transformations
- **Excel/CSV Processing:** Pandas read_excel/read_csv with openpyxl/xlrd engines
- **Excel/CSV Export:** Pandas to_excel/to_csv with xlsxwriter for formatted Excel exports
- **JSON Processing:** Python standard library json module
- **Data Validation:** Pandas validation + custom validation logic
- **Date/Time Handling:** Python datetime and pandas datetime utilities

### File & Report Generation
- **PDF Generation:** ReportLab (for simple reports) or WeasyPrint (for HTML-to-PDF)
- **Excel Export:** xlsxwriter (via Pandas) for formatted Excel files with multiple sheets

## Database & Storage

### Database
- **Primary Database:** PostgreSQL 15+ (cloud-hosted)
- **ORM:** SQLAlchemy 2.0+ with async support
- **Migration Tool:** Alembic
- **Connection Pooling:** SQLAlchemy built-in pool or pgbouncer

### Storage
- **File Storage:** Cloud storage (AWS S3, Azure Blob, or GCP Cloud Storage) for uploaded files and generated exports
- **Local Storage (Development):** Local filesystem for development/testing

## Authentication & Security

### Authentication
- **Authentication Strategy:** JWT tokens or session-based auth
- **Password Hashing:** bcrypt or passlib
- **Authorization:** Role-based access control (RBAC) with custom middleware

### Security
- **HTTPS:** Required in production
- **CORS:** FastAPI CORS middleware
- **Input Validation:** Pydantic models on all endpoints
- **SQL Injection Prevention:** SQLAlchemy ORM parameterized queries
- **File Upload Security:** File type validation, size limits, virus scanning (optional)

## Testing & Quality

### Frontend Testing
- **Test Framework:** Jest / Vitest
- **Component Testing:** React Testing Library
- **E2E Testing:** Playwright (optional for critical data export workflows)

### Backend Testing
- **Test Framework:** pytest
- **API Testing:** pytest with httpx for async testing
- **Test Coverage:** pytest-cov
- **Database Testing:** pytest fixtures with test database

### Code Quality
- **Frontend Linting:** ESLint with TypeScript support
- **Frontend Formatting:** Prettier
- **Backend Linting:** Ruff or Flake8
- **Backend Formatting:** Black
- **Type Checking:** TypeScript (frontend), mypy (backend)

## Deployment & Infrastructure

### Hosting
- **Frontend Hosting:** Vercel
- **Backend Hosting:** Cloud platform (AWS ECS, Azure App Service, GCP Cloud Run, or similar)
- **Database Hosting:** Managed PostgreSQL (AWS RDS, Azure Database, GCP Cloud SQL, or similar)

### CI/CD
- **Frontend:** Vercel automatic deployments (GitHub integration)
- **Backend:** GitHub Actions or cloud platform CI/CD
- **Preview Deployments:** Automatic on pull requests

### Monitoring & Observability
- **Frontend Analytics:** Vercel Analytics
- **Error Tracking:** Sentry (frontend and backend)
- **Logging:** Python logging with structured logs
- **Performance Monitoring:** APM tool (optional: New Relic, Datadog, or cloud-native)

## Development Tools

### Environment Management
- **Environment Variables:** .env files (never committed)
- **Frontend Config:** Vercel environment variables
- **Backend Config:** python-dotenv for local, cloud config for production

### API Development
- **API Documentation:** FastAPI auto-generated Swagger UI
- **API Testing:** FastAPI TestClient or httpx
- **Schema Validation:** Pydantic models

### Version Control
- **VCS:** Git with GitHub
- **Branching Strategy:** Feature branches with pull requests
- **Commit Standards:** Conventional commits (optional but recommended)

## Third-Party Services

### Essential Services
- **Email (Optional):** SendGrid, AWS SES, or Resend for notifications
- **File Storage:** Cloud storage provider (AWS S3, Azure Blob, GCP Cloud Storage)

### Analytics & Monitoring
- **Application Monitoring:** Sentry
- **Performance Metrics:** Cloud provider metrics or dedicated APM

## Development Environment

### Required Tools
- **Node.js:** v22 LTS
- **Python:** 3.11+
- **PostgreSQL:** 15+ (local via Docker recommended)
- **Git:** Latest stable

### Recommended IDE Setup
- **Editor:** VS Code
- **Extensions:** ESLint, Prettier, Python, Pylance
- **Code Formatting:** Format on save enabled

## Notes on Tech Stack Choices

### Data Processing Focus
This tech stack emphasizes data integration and transformation rather than complex analytics:
- **Pandas** is used for ETL, data cleaning, and basic aggregations (not advanced statistical modeling)
- **No NumPy** required - removed since we're not doing complex numerical computations or financial projections
- **No specialized analytics libraries** - users will use their own tools (Excel, R, Python notebooks) for advanced analysis

### Export-First Architecture
The backend is optimized for preparing clean, well-structured exports:
- **xlsxwriter** (via Pandas) for professional Excel exports with formatting and multiple sheets
- **Multiple export formats** (Excel, CSV, JSON) to support different downstream tools
- **API access** for programmatic data extraction by power users

### Dashboard Simplicity
Dashboards focus on visualization rather than complex calculations:
- **Recharts** provides clean, interactive charts without heavy dependencies
- **TanStack Table** handles data tables with sorting/filtering
- All complex calculations happen in the backend and are pre-computed
