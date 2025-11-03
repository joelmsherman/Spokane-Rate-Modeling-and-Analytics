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
- Develop comprehensive data request covering all source systems
- Schedule stakeholder interviews to understand data workflows
- Identify key contacts for each data source
- Analyze sample data from all source systems, including:
  - General Ledger structure and account codes
  - Billing system data formats and customer segmentation
  - Routing system schedules and assignments
  - Truck/Asset maintenance system
  - Payroll hours by function
  - Collection telemetrics and tonnage data
  - Scalehouse operations and material tracking

## Task 2: Kick-Off Meeting / Review of Department / Inventory of Systems and Data

**Duration:** 1 week
**Investment:** $5,000 - $6,000

Once we have received the requested data from Task 1, we will schedule meetings with Department staff. The kick-off meeting will serve as a forum to discuss preliminary findings from our research, document current workflows, continue data collection, and identify project issues, goals, roles, and responsibilities.

### Activities
- Conduct kick-off meeting with City staff and Bell & Associates team
- Tour facilities
- Interview stakeholders
- Document current data collection and analysis processes
- Map data dependencies and relationships across systems
- Identify data quality issues and validation requirements

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
- **Administrator Guide** for user management and system maintenance

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

Based on the requirements workshop, we will design pre-built export packages that provide exactly the data needed for the Phase 2 cost-of-service analysis. Each package will be structured to minimize data preparation work and integrate directly into rate modeling processes.

While the exact packages are dependent on the workshop, **some examples** include: 

**Cost-of-Service Analysis Package**
*Structured for revenue requirement and cost allocation analysis*

- **Revenue Data:**
  - Multi-year revenue by service line (residential, commercial)
  - Revenue by service type (garbage, recycling, organics, roll-off)
  - Customer counts and revenue per customer by class
  - Rate schedules and billing volumes
  - Fund balances and reserve levels

- **Expense Data:**
  - Multi-year expenses by department and cost center
  - Expenses allocated by function (collection, disposal, administration)
  - Cost component breakdown (labor, equipment, disposal, overhead)
  - Budget vs. actual with variance analysis
  - Capital expenditures and debt service

- **Cost Allocation Bases:**
  - Tonnage by material type and service line
  - Customer counts by service type and class
  - Route hours and truck counts by service
  - Labor hours by function
  - Facility utilization metrics

**Operational Metrics Package**
*Structured for operational efficiency and unit cost analysis*

- **Collection Operations:**
  - Tonnage collected by route, service type, and material
  - Collection labor hours and costs by service line
  - Truck utilization and maintenance costs
  - Routes serviced and frequency
  - Efficiency metrics (tons per hour, cost per ton)

- **Disposal Operations:**
  - Tonnage by material type and disposal method
  - Disposal costs and tipping fees
  - Scalehouse transaction data
  - Material recovery and diversion rates
  - Processing costs by material stream

- **Asset & Labor Data:**
  - Truck fleet costs (purchase, maintenance, fuel)
  - Equipment utilization and replacement schedules
  - Payroll costs by function and allocation method
  - Overtime and supplemental labor costs

**Rate Modeling Input Package**
*Structured to feed directly into rate calculation models*

- **Current State Baseline:**
  - Existing rates by service type and customer class
  - Current customer counts and service volumes
  - Existing cost allocations by service line
  - Historical growth rates (customers, tonnage, costs)

- **Projection Inputs:**
  - Multi-year expense trends by category
  - Revenue projections at current rates
  - Anticipated regulatory costs (carbon tax, organics mandate)
  - Capital investment requirements
  - Reserve level requirements

- **Scenario Variables:**
  - Variable costs by service type
  - Fixed cost allocations
  - Volume sensitivity factors
  - Alternative service configurations

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
- **3 Pre-Built Phase 2 Data Packages** (Cost-of-Service, Operational Metrics, Rate Modeling Inputs)
- **Custom Data Export Builder** (web interface)
- **Export System User Guide** with step-by-step instructions