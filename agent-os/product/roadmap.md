# Product Roadmap

## Data Infrastructure Foundation ($38,000 - $40,000 / 11 weeks)
*Goal: Working data infrastructure for Phase 2 rate study with Bell & Associates*

### Data Request / Stakeholder Discovery (3 weeks / $3,000 - $4,000)

1. [ ] **Data Request Development** - Create comprehensive data request document covering all source systems (General Ledger, Billing, Routing, Payroll, Collection Telemetrics, Scalehouse, Truck/Asset Maintenance) with specific fields, formats, and time periods needed. `S`

2. [ ] **Sample Data Analysis** - Analyze sample data from all source systems to understand data SMEs for each system, data structures, data quality issues, and relationships across systems `M`

3. [ ] **Stakeholder Interview Planning** - Plan, schedule and conduct (Task 2) stakeholder interviews to understand data workflows, including current data collection and analysis processes; data quality issues and validation requirements; and data dependencies and relationships across systems `M`

### Kick-Off Meeting / System Inventory (1 week / $5,000 - $6,000)

4. [ ] **Kick-Off Meeting & Facility Tour** - Conduct kick-off meeting with City staff and Bell & Associates team, tour facilities `S`

5. [ ] **Stakeholder Data Interviews** - Conduct and record stakeholder data interviews with data source SMEs per plan

6. [ ] **Data Workflow Documentation** — Document current data collection and analysis processes, data quality issues and validation requirements,and dependencies and relationships across systems per interview transcripts; send to stakeholders for validation. `S`

### Data Infrastructure Implementation (4 weeks / $20,000 - $22,000)

> Note: Database schemas and data models are built incrementally with each source system implementation below, not upfront.

7. [ ] **Cloud Infrastructure & Deployment** — Deploy PostgreSQL database on Supabase (with default automated backups), deploy backend API on cloud platform, deploy frontend on Vercel, and configure HTTPS and security settings. `M`

8. [ ] **Authentication System & Administrative Interface** — Implement secure login system with role-based access control (Admin, Analyst, Viewer roles) with appropriate permissions for upload, export, and user management; create web interface for user management. `M`

9. [ ] **Source Data Integrations** (Vertical Slices per dataset) — For each source data set, build a complete data integration. Each source has unique schemas, so dashboards are source-specific rather than unified. `L - for each source`

    **Dashboard per source:** Paginated data table (server-side, 50 rows default) with sortable/filterable columns; row-level Edit and Delete actions; upload history and data coverage metrics.

    **Upload flow (3-step modal):**
    - Step 1: File selection with drag-drop, downloadable CSV template, schema summary
    - Step 2: Field mapping with auto-match, required field indicators, 5-row preview
    - Step 3: Validation results—errors block import, duplicates rejected by natural key, success confirms import

    **Record-level CRUD:** Edit via modal form; soft delete for reference data (lines of business, ledger mappings, etc. TBD), hard delete for transactional data (expenses, tonnage, etc. TBD); all records track `created_by/at`, `updated_by/at`, `upload_batch_id`.

    **Sources (these are examples - TBD):**
    - General Ledger/Financial
    - Billing
    - Routing
    - Payroll
    - Collection
    - Scalehouse
    - Truck Maintenance

10. [ ] **Documentation** — Create documentation for the database schema including a complete data dictionary with field definitions and validation rules; Create documentation for the import processes; Create an administrator guide for managing users `M`

### Data Export System (3 weeks / $8,000 - $10,000)

11. [ ] **Bell & Associates Requirements Workshop** — Conduct detailed review session with Bell & Associates to determine which datasets are needed for Phase 2 Cost-Rate Model and Annual Cost of Service Study packages. The focus is on delivering clean, validated data in formats that integrate with Bell's existing spreadsheet models. `S`

12. [ ] **Build Analysis-ready Data Packages** - Based on the requirements workshop, design two analysis-ready data packages implemented as **materialized views** in the database. These views provide pre-aggregated, validated datasets that can be exported directly to Excel for use in Bell & Associates' existing spreadsheet-based rate models. The packages align directly with Phase 2 tasks. Initial ideas for each package are available @/requirements/datapacks-initial.md `XL`

13. [ ] **Export Interface** — Build web interface allowing users to access pre-built data packages AND to build custom data queries to select specific data elements from any source system, combine data across sources, apply filters and date ranges, preview data, and export in Excel or CSV formats. `XL`

14. [ ] **Export Documentation** — Create an export interface user guide with usage instructions, examples, and troubleshooting information `M`

> Notes
> - Phase 1 total: 14 items across 4 tasks / 11 weeks / $38,000 - $40,000
> - Phase 1 deliverables: Working database with incremental schema development, source-specific dashboards with upload interfaces and downloadable schemas, validation and ETL pipelines per source, user authentication, deployed cloud infrastructure, complete data dictionary, Phase 2-ready export system with custom export builder, and comprehensive documentation
> - Effort estimates: S (2-3 days), M (1 week), L (2 weeks), XL (3-4 weeks)
> - Phase 1 philosophy: Build functional infrastructure that makes data accessible and trustworthy, not a polished platform; deliver working vertical slices per source system