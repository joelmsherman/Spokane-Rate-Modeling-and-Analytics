# Product Mission

## Pitch
The Spokane Solid Waste Rate Analytics Platform is a data infrastructure foundation that consolidates data from all City of Spokane Solid Waste Division systems into a centralized, validated database — enabling Bell & Associates to conduct cost-rate modeling with clean, reliable data while providing the City with a working data warehouse that makes their data accessible and trustworthy.

## Users

### Primary Customers
- **Bell & Associates**: Rate study consultants conducting Phase 2 cost-of-service analysis and rate modeling for the City of Spokane
- **City of Spokane Solid Waste Division**: Municipal department managing waste collection, disposal, and recycling services that needs centralized data infrastructure
- **Municipal Finance Departments**: City finance teams requiring clean, accessible data for rate modeling and financial projections

### User Personas

**Rate Study Consultant (Bell & Associates)**
- **Role:** External consultant conducting cost-of-service analysis and rate modeling
- **Context:** Hired to perform comprehensive Phase 2 rate study using data from multiple City systems
- **Pain Points:** Spending days aggregating and validating data from multiple disconnected systems; basic data quality issues consume billable hours; difficult to get data in formats that integrate with rate modeling workflows; lack of data lineage and validation documentation
- **Goals:** Receive clean, pre-validated data packages structured for rate modeling; minimize time on data preparation; trust that source data is accurate and complete; focus expertise on methodology and strategic recommendations rather than data wrangling

**City Data Administrator**
- **Role:** Solid Waste Division staff responsible for uploading and managing data
- **Context:** Responsible for collecting data from various source systems and ensuring it gets into the data warehouse
- **Pain Points:** No central location to upload data; unclear what validation errors mean; don't know if uploads succeeded; managing multiple file versions across systems
- **Goals:** Simple upload interface; clear error messages; see what data has been uploaded and when; manage user access; ensure data quality before consultants see it

**Finance Analyst**
- **Role:** Solid Waste Division financial analyst or budget manager
- **Context:** Responsible for annual budget preparation, rate setting, and financial monitoring for a complex utility operation
- **Pain Points:** Data scattered across 8+ disconnected systems; weeks spent aggregating data for rate studies; Excel models that break when data changes; can't easily export data in needed formats
- **Goals:** Get clean data fast; export datasets ready for financial modeling; spend time on analysis instead of data wrangling; provide Bell & Associates with reliable data for Phase 2 study

## The Problem

### Data Fragmentation Blocks Rate Study and Financial Management
The City of Spokane's Solid Waste Division needs to conduct a comprehensive Phase 2 cost-of-service study and rate modeling, but critical financial and operational data is scattered across many disconnected systems (General Ledger, Billing, Routing, Payroll, Collection Telemetrics, Scalehouse, etc.). City staff spend weeks manually aggregating data from these systems before any analysis can begin. Bell & Associates consultants waste billable hours validating basic data quality instead of providing strategic rate modeling guidance. There is no centralized location to upload, validate, and store data with proper version control and audit trails.

**Our Solution (Phase 1):** A working data infrastructure foundation that consolidates data from all source systems into a centralized, validated database. This includes: upload capabilities with data validation, user authentication with role-based access, complete database schema with historical tracking and audit trails, and a Phase 2-ready export system that delivers analysis-ready datasets structured specifically for Bell & Associates' cost-of-service work. Not a polished analytics platform, but solid infrastructure that makes data accessible and trustworthy.

## Differentiators

### Purpose-Built for Solid Waste Rate Studies
Unlike generic data platforms, we understand solid waste utility financial structures, cost allocation methodologies, and rate modeling requirements. Database schema and export packages are designed specifically for municipal solid waste operations, eliminating weeks of custom data preparation work for Phase 2 cost-of-service analysis.

### Infrastructure-First, Not Dashboard-First
Unlike typical analytics platforms that start with dashboards, we focus on building reliable data infrastructure foundation first. Clean, validated data with proper version control and audit trails is more valuable than polished visualizations. Advanced dashboards can be added later when budget allows.

### Export-Ready for Rate Modeling Workflows
Unlike platforms that force all analysis into proprietary tools, we deliver pre-built export packages structured specifically for Bell & Associates' rate modeling workflows. Data packages integrate seamlessly with existing cost-of-service methodologies, allocation logic, and rate calculation models.

### Data Quality and Lineage
Unlike simple file storage, we provide comprehensive validation rules for each data source, clear error reporting, data lineage documentation (source system mapping, transformation logic, business rules), and complete audit trails. Users know exactly where every number came from and can trust the data quality.

## Key Features (Phase 1 Scope)

### Database Infrastructure
- **Cloud PostgreSQL Database:** Normalized schema for all source systems (General Ledger, Billing, Routing, Payroll, Collection Telemetrics, Scalehouse, Truck/Asset Maintenance) with historical data tracking, audit trail system, automated backups, and performance-optimized indices
- **Complete Data Dictionary:** Comprehensive documentation with field definitions, validation rules, and business logic for every data element

### Data Upload System
- **File Upload Interface:** Simple web form for uploading Excel/CSV files for each data source with basic authentication, file history tracking, and upload status visibility
- **Data Validation Engine:** Automated validation rules for each data source with line-by-line error reporting, clear error messages, and exception handling
- **Data Transformation & Loading:** Parse uploaded files into standardized format, apply business rules and categorizations, load validated data into database, and generate import summary reports

### User Management
- **Role-Based Access Control:** Secure authentication system supporting three roles (Admin with full access to upload/export/user management; Analyst with upload and export access; Viewer with export-only access for consultants)
- **Simple Administrative Interface:** User management, data import history viewing, and basic system health monitoring

### Phase 2-Ready Export System
- **Pre-Built Data Packages:** Three export packages structured for rate modeling: Cost-of-Service Analysis Package (multi-year revenue/expense, cost allocation bases), Operational Metrics Package (collection operations, disposal operations, asset & labor data), and Rate Modeling Input Package (current state baseline, projection inputs, scenario variables)
- **Custom Export Builder:** Web interface for building custom data exports with ability to select specific data elements, combine data across sources, apply filters and date ranges, and export in Excel or CSV formats
- **Export Documentation:** Comprehensive guide to all export packages, field-level data dictionaries, usage instructions, and data lineage documentation showing source system mapping and transformation logic
