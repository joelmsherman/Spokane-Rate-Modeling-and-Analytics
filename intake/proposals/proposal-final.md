# Spokane Solid Waste Rate Analytics - Phase 1 Revised Scope
## Data Infrastructure Foundation

**Prepared for:** Bell & Associates / City of Spokane Solid Waste Division
**Prepared by:** JMS Analytics
**Date:** November 2, 2025

---

## Executive Summary

This Phase 1 scope delivers a **working data infrastructure** that consolidates data from all City of Spokane Solid Waste Division systems into a centralized, validated database. This foundation enables Bell & Associates to conduct the Phase 2 cost-rate modeling and cost-of-service study with clean, reliable data.

**What you get:** A functional data warehouse with upload capabilities, data validation, and export tools—not a polished analytics platform, but a solid infrastructure that makes your data accessible and trustworthy.

**What's deferred:** Advanced dashboards, sophisticated UI/UX, and visualization tools can be added in a future phase when budget allows.

## Deliverables Overview

| Task | Description | Investment |
|------|-------------|-----------|
| **Task 1 and 2** | Data Discovery & Requirements | $8,000 - $10,000 |
| **Task 3** | Data Infrastructure Implementation | $20,000 - $22,000 |
| **Task 4** | Phase 2-Ready Data Export System | $10,000 - $8,000 |
| **Total** | | **$38,000 - $40,000** |

## Task 1: Data Request / Stakeholder Discovery

**Duration:** 3 weeks
**Investment:** $3,000 - $4,000

Upon receipt of the notice to proceed, we will provide a detailed list of information necessary to initiate the project. The data request will itemize our needs for understanding service delivery and the data generated from the various systems used to manage Department operations.

### Activities
- Develop comprehensive data request covering all source systems and analyze sample data:
  - General Ledger structure and account codes
  - Billing system data formats and customer segmentation
  - Routing system schedules and assignments
  - Truck/Asset maintenance system
  - Payroll hours by function
  - Collection telemetrics and tonnage data
  - Scalehouse operations and material tracking
- Identify key contacts for each data source
- Plan and schedule data stakeholder interviews to understand data workflows, including:
  - current data collection and analysis processes
  - data quality issues and validation requirements
  - data dependencies and relationships across systems

## Task 2: Kick-Off Meeting / Review of Department / Inventory of Systems and Data

**Duration:** 1 week
**Investment:** $5,000 - $6,000

Once we have received the requested data from Task 1, we will schedule meetings with Department staff. The kick-off meeting will serve as a forum to discuss preliminary findings from our research, document current workflows, continue data collection, and identify project issues, goals, roles, and responsibilities.

### Activities
- Conduct kick-off meeting with City staff and Bell & Associates team
- Tour facilities
- Interview data stakeholders
- Document data workflows per plan from meeting transcipts

## Task 3: Data Infrastructure Implementation

**Duration:** 4 weeks
**Investment:** $20,000 - $22,000

Build the core data infrastructure that consolidates all source systems into a centralized, validated database. This is a **functional system, not a polished platform**—the focus is on reliability and data integrity, not visual design.

### 3.1 Database Design & Implementation

**Cloud PostgreSQL Database**
- Design normalized schema for all source systems
- Implement historical data tracking (maintain all versions)
- Create audit trail system (who changed what, when)
- Set up automated backups
- Configure appropriate indices for performance

**Data Models for source systems, including but not limited to:**
- General Ledger (accounts, transactions, cost allocations)
- Billing (customers, services, revenue)
- Routing (routes, schedules, service areas)
- Payroll (labor costs, function allocation)
- Collection Telemetrics (tonnage, truck data, efficiency metrics)
- Scalehouse (disposal tonnage, material types)
- Truck/Asset Maintenance (equipment costs, downtime)

### 3.2 Data Import System

**File Upload Interface**
- Simple web form for uploading Excel/CSV files for each data source
- Basic authentication (username/password)
- File history tracking (who uploaded what, when)

**Data Validation Engine**
- Automated validation rules for each data source
- Error reporting with specific line-by-line feedback

**Data Transformation & Loading**
- Parse uploaded files into standardized format
- Apply business rules and categorizations
- Load validated data into database
- Generate import summary reports

### 3.3 Basic Web Interface

**User Authentication & Authorization**
- Secure login system (username/password with encryption)
- Role-based access control:
  - **Admin:** Full access to upload, export, user management
  - **Analyst:** Upload and export data
  - **Viewer:** Export data only (for consultants)
- Session management with secure tokens

**Simple Administrative Interface**
- User management (add, remove, change roles)
- View data import history
- Basic system health monitoring

### 3.4 Infrastructure & Deployment

- Deploy PostgreSQL database on managed cloud service (Supabase)
- Deploy backend API on cloud platform
- Deploy frontend on Vercel
- Configure HTTPS and security settings

### Task 3 Deliverables
- **Working Database** with complete schema for all source systems
- **Data Upload Interface** (functional web application)
- **Data Validation System** with automated quality checks
- **User Authentication System** with role-based access
- **Deployed Cloud Infrastructure**
- **Database Schema Documentation**
- **Complete Data Dictionary** with field definitions and validation rules
- **Import Process Documentation** for each data source
- **Administrator Guide** for user management

## Task 4: Phase 2-Ready Data Export System

**Duration:** 3 weeks
**Investment:** $8,000 - $10,000

Design and implement a comprehensive data export system that provides Bell & Associates with analysis-ready datasets specifically structured for Phase 2 cost-of-service study and rate modeling work. The focus is on delivering clean, validated data in formats that integrate seamlessly with existing rate modeling workflows.

### 4.1 Bell & Associates Workshop

Conduct a detailed review session with Bell & Associates team to understand:
- Existing rate model structure and data requirements
- Current data preparation workflows
- Pain points with existing data sources
- Preferred file formats and layouts
- Calculation methodologies and allocation logic

### 4.2 Phase 2 Rate Modeling Data Packages

Based on the requirements workshop, we will design two analysis-ready data packages implemented as **materialized views** in the database. These views provide pre-aggregated, validated datasets that can be exported directly to Excel for use in Bell & Associates' existing spreadsheet-based rate models.

The packages align directly with Phase 2 tasks:

---

**Package 1: Cost-Rate Model Dataset** *(supports Task 5)*

*Provides the financial and operational inputs needed to calculate costs by line of business and cost component in Bell's interactive cost-rate model.*

This materialized view aggregates data to support expense allocation by:
- **Line of Business:** Disposal, Cart Collection, Container Collection, Roll-Off Service
- **Cost Component:** Disposal/Processing, Labor, Collection/Truck, Carts/Containers, Facility, Administrative, Taxes/Fees

| Data Element | Source System | Granularity |
|-------------|---------------|-------------|
| **Expense Data** | | |
| Disposal/Processing costs | GL, Scalehouse | By material type (garbage, recycling, organic) |
| Collection labor costs | Payroll, GL | By service line and material type |
| Truck/Collection costs | Fleet/Asset, GL | By service type |
| Cart/Container costs | Asset, GL | By container type and service |
| Facility costs | GL | Allocated by service line |
| Administrative overhead | GL | Allocated to garbage only (per B&A methodology) |
| Taxes and fees | GL | Allocated to garbage only |
| **Operational Allocation Bases** | | |
| Tonnage by material type | Scalehouse, Telemetrics | By service line |
| Customer counts | Billing | By service type and class |
| Route hours | Routing, Payroll | By service line |
| Truck counts and utilization | Fleet/Asset | By service type |

**Output Format:** Single Excel export with:
- Summary tab matching B&A cost-rate model input structure
- Expense detail tab by GL account and allocation
- Operational metrics tab with allocation bases
- Monthly and annual aggregation options

---

**Package 2: Cost of Service Study Dataset** *(supports Task 6)*

*Provides the revenue requirement, cost allocation, and rate comparison data needed for the annual cost-of-service study and rate design recommendations.*

This materialized view supports the Task 6 sub-components:

| Task 6 Component | Data Elements | Source Systems |
|-----------------|---------------|----------------|
| **6.1 Revenue Requirement** | | |
| Budgeted expenses by line of business | GL, Budget | By service (garbage, recycling, organics) |
| Actual expenses (YTD) | GL | By department and cost center |
| Interfund transfers | GL | As recorded |
| Fund balances | GL | Current and target levels |
| Asset reserves | GL, Asset | Landfill closure, equipment replacement |
| **6.2 Cost of Service** | | |
| Disposal costs per ton | GL, Scalehouse | By material type |
| Collection costs per customer | GL, Billing, Payroll | By service type |
| Unit costs by service | Calculated | Cost per customer per month |
| **6.3 Rate Design Inputs** | | |
| Current rate schedules | Billing | By service type and class |
| Customer counts by class | Billing | Residential, commercial, roll-off |
| Revenue by service type | Billing | Multi-year trend |
| **6.4 Revenue Projection** | | |
| Historical growth rates | Billing | Customers, tonnage, revenue |
| Expense escalation factors | GL | By cost category |
| Regulatory cost impacts | Manual input | State mandates, carbon costs |

**Output Format:** Excel workbook with tabs for:
- Revenue requirement summary (matching B&A memo format)
- Expense detail by function and service
- Cost of service calculations by line of business
- Current vs. cost-of-service rate comparison
- Revenue projection scenarios (current rates vs. proposed)
- Multi-year trend analysis

---

**Implementation Notes:**

- Both packages are implemented as **PostgreSQL materialized views** that refresh on demand or on a scheduled basis
- Views include data validation flags to highlight any quality issues
- Export interface allows date range selection and year-over-year comparisons
- Field mappings documented to trace every output back to source system records

### 4.3 Custom Export Builder

**Web-Based Interface**
- Intuitive interface for building custom data exports
- Select specific data elements from any source system
- Combine data across multiple sources
- Apply filters and date ranges
- Preview data before exporting

**Flexible Output Options**
- Excel
- CSV

### 4.4 Documentation & Future Development Specifications

**Export System Documentation**
- Comprehensive guide to all pre-built export packages
- Field-level data dictionary for each export
- Instructions for using custom export builder
- Examples and common use cases
- Troubleshooting guide

**Data Lineage Documentation**
- Source system mapping for each data element
- Transformation logic applied to raw data
- Business rules and assumptions
- Validation rules for each field
- Known data quality issues and workarounds

### Task 4 Deliverables
- **2 Analysis-Ready Data Packages** as materialized database views:
  - Cost-Rate Model Dataset (Task 5 support)
  - Cost of Service Study Dataset (Task 6 support)
- **Custom Data Export Builder** (web interface)
- **Export System User Guide** with step-by-step instructions