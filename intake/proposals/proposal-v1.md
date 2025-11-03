# Spokane Solid Waste Rate Analytics Platform
## Project Proposal

**Prepared for:** Bell & Associates / City of Spokane Solid Waste Division
**Prepared by:** JMS Analytics
**Date:** October 31, 2025

## Background

The City of Spokane's Solid Waste Division faces significant financial challenges with two consecutive years of deficits and upcoming regulatory mandates (2027 carbon tax, 2030 organics requirements). Making informed decisions about rates, services, and investments requires timely access to accurate financial and operational data.

Currently, critical data is trapped in 8+ disconnected systems, forcing staff to spend weeks manually aggregating data before any analysis can begin. Consultants waste billable hours on data validation instead of strategic guidance. Management lacks real-time visibility into performance.

**This platform changes that.**

By centralizing all data in one place with automated validation, providing real-time dashboards for oversight, and enabling easy export for detailed analysis, this platform becomes the foundation for data-driven financial management. It doesn't replace your existing tools and workflows—it makes them dramatically more efficient.

The investment in this platform pays dividends through:
- **Time savings** that free up staff for strategic work instead of data wrangling
- **Better decisions** based on timely, accurate data instead of outdated spreadsheets
- **Consultant efficiency** that maximizes the value of external expertise
- **Financial sustainability** through informed rate setting and budget management
- **Regulatory readiness** for upcoming mandates that will require detailed tracking

## Objectives & Key Outcomes

### Primary Objective
Develop and deploy a cloud-based data integration and analytics platform that centralizes financial and operational data from multiple disconnected systems across the Spokane Solid Waste Division, enabling data-driven decision making, real-time operational visibility, and efficient rate modeling to address current financial deficits and prepare for regulatory changes.

### Key Outcomes

**1. Unified Data Integration**
- Eliminate manual data aggregation from disconnected source systems (General Ledger, Billing, Routing, Payroll, Collection Telemetrics, Scalehouse)
- Establish a single source of truth for all financial and operational analytics
- Reduce data preparation time from weeks to hours
- Enable real-time visibility into financial and operational performance

**2. Enhanced Financial Management Capabilities**
- Provide pre-built dashboards for executive oversight and detailed financial analysis
- Enable trend analysis and variance tracking for informed rate setting and budget management
- Support financial planning for regulatory changes (2027 carbon tax, 2030 organics mandate)
- Create comprehensive audit trails and data lineage tracking

**3. Flexible Data Export & Analysis**
- Export clean, validated datasets in multiple formats (Excel, CSV, JSON)
- Provide pre-built data packages for common analysis workflows
- Enable API access for advanced users working with Python/R
- Support existing financial modeling tools rather than replacing them

**4. Secure Multi-Stakeholder Access**
- Implement role-based access control for internal analysts, executives, and external consultants
- Ensure appropriate data visibility based on user roles
- Maintain data security and audit compliance
- Enable collaboration without compromising data governance

## Key Tasks

### Phase 1: Requirements Gathering & Analysis (3-4 weeks)
**Objective:** Thoroughly understand user needs, system integrations, data workflows, and business requirements

**Activities:**
- Conduct stakeholder interviews to understand data needs and workflows
- Document current data collection and analysis processes
- Analyze sample data files from all source systems (GL, Billing, Routing, Payroll, Telemetrics, Scalehouse)
- Map data fields and relationships across systems
- Define data validation rules and business logic for each data source
- Identify integration methods and data access patterns for each system
- Document dashboard metrics and KPI requirements for different user roles
- Define export requirements and data package specifications
- Create detailed functional requirements document
- Obtain stakeholder approval on requirements

**Key Questions to Answer:**
- What are the specific data formats and structures from each source system?
- What validation rules ensure data quality and consistency?
- What metrics and KPIs are most critical for each user role?
- What are the current pain points in data aggregation and analysis?
- What data elements are needed for rate modeling and financial projections?
- How should data be organized for export to support existing workflows?

**Deliverables:**
- Functional Requirements Document
- System Integration Specifications
- Data Dictionary and Validation Rules
- Dashboard & Metrics Requirements
- Export Package Specifications
- Stakeholder Sign-off

### Phase 2: UX Design & Prototyping (2-3 weeks)
**Objective:** Create intuitive user interfaces that meet the needs of analysts, executives, and external consultants

**Activities:**
- Create information architecture for the entire platform
- Design wireframes for all major user flows:
  - Data import and validation workflows
  - Dashboard navigation and filtering
  - Data export and custom query builder
  - User management and permissions
- Develop high-fidelity mockups of:
  - Executive dashboard (high-level metrics and KPIs)
  - Financial performance dashboard (detailed revenue/expense analysis)
  - Operational metrics dashboard (tonnage, efficiency, customer data)
  - Data health monitoring dashboard (data quality and freshness)
  - Data import interface (upload, validation, error handling)
  - Export interface (pre-built packages and custom exports)
  - Administrative interfaces (user management, system settings)
- Create interactive prototypes for key workflows
- Conduct design review sessions with representative users from each role
- Test navigation and usability with actual users
- Iterate designs based on feedback
- Finalize design system (colors, typography, components)

**Key Design Principles:**
- Clean, professional interface appropriate for municipal government
- Dashboard-first design for executives who need at-a-glance visibility
- Data table emphasis for analysts who need to explore details
- Export-focused UX for users who work in Excel and other tools
- Clear validation feedback for data import workflows
- Mobile-responsive for tablet access

**Deliverables:**
- High-Fidelity Design Mockups
- Design System Documentation
- Sitemap and User Flow Diagrams
- Design Review & Approval

### Phase 3: Foundation & Core Infrastructure (3-4 weeks)
**Objective:** Build the foundational system architecture and core capabilities

**Core Infrastructure**
- Set up Next.js frontend application framework with TypeScript
- Configure FastAPI backend application
- Implement PostgreSQL database schema for normalized financial and operational data
- Set up cloud file storage for uploads and exports
- Implement JWT-based authentication system
- Create role-based access control framework (Analyst, Executive, Consultant roles)
- Establish secure API communication between frontend and backend
- Set up development, staging, and production environments
- Configure automated database backups

**Data Management Foundation**
- Build database models with historical tracking and versioning
- Implement audit trail system for all data changes
- Create standardized data import interface (Excel/CSV upload)
- Build file validation and parsing framework
- Develop error handling and reporting system
- Create data validation engine framework

**Deliverables:**
- Deployed development environment
- Database schema and models
- Authentication and authorization system
- File upload infrastructure
- Core API endpoints
- Technical documentation

### Phase 4: Data Integration Development (5-6 weeks)
**Objective:** Implement end-to-end data pipelines for all source systems

**General Ledger Integration**
- Build GL data import workflow
- Implement account mapping and categorization logic
- Create validation rules (balance checks, account codes, date ranges)
- Build transformation logic for service line and cost type categorization
- Implement storage with full audit trail and versioning

**Billing System Integration**
- Build billing data import workflow
- Implement customer segmentation (residential, commercial, etc.)
- Create revenue validation rules (totals, customer counts, rate consistency)
- Build transformation logic for revenue by service type and customer class
- Implement historical revenue tracking

**Operational Data Integrations**
- **Routing System:** Route data, service schedules, customer assignments
- **Payroll System:** Labor costs, allocation by service line, overtime tracking
- **Collection Telemetrics:** Tonnage collected, route efficiency, truck productivity
- **Scalehouse System:** Disposal tonnage, material types, facility data

**For Each Integration:**
- Design import workflow specific to data source format
- Build validation rules appropriate to data type
- Create transformation logic to normalize data
- Implement storage with historical tracking
- Build data quality monitoring
- Create reconciliation reports

**Deliverables:**
- 6 complete data integration pipelines
- Validation rule sets for each source
- Data quality monitoring system
- Import history and audit trails
- Integration documentation

### Phase 5: Dashboard Development (4-5 weeks)
**Objective:** Build comprehensive dashboard suite for all user roles

**Executive Dashboard**
- High-level financial overview (budget vs actuals, variance analysis)
- Revenue trends by service line with YoY comparisons
- Expense trends by major category
- Reserve levels and financial sustainability metrics
- Key operational metrics (tonnage, customer counts)
- Period-over-period comparisons
- Drill-down capabilities to detailed views

**Financial Performance Dashboard**
- Detailed revenue analysis by service line and customer class
- Expense analysis by service line and cost category
- Budget variance tracking with trend analysis
- Cost allocation and overhead distribution
- Revenue per customer and cost per ton metrics
- Multi-year trending and forecasting support

**Operational Metrics Dashboard**
- Tonnage tracking by material type and facility
- Collection efficiency metrics (route performance, truck productivity)
- Customer data (counts by service type, growth trends)
- Diversion rates and recycling metrics
- Service level performance indicators
- Operational cost metrics (cost per ton, cost per household)

**Data Health Monitoring Dashboard**
- Data freshness indicators for all source systems
- Validation issue tracking and resolution
- Data coverage and completeness metrics
- Import history and success rates
- Data quality scoring
- Alert system for missing or problematic data

**Dashboard Features:**
- Interactive filtering (date ranges, service lines, facilities)
- Exportable charts and tables
- Customizable views
- Responsive design for tablet access
- Print-friendly layouts

**Deliverables:**
- 4 complete dashboards
- Interactive filtering and drill-down
- Export capabilities
- Mobile-responsive design
- User documentation

### Phase 6: Export & Reporting System (3-4 weeks)
**Objective:** Enable flexible data export to support existing analysis workflows

**Pre-Built Data Packages**
- **Financial Data Package:** Multi-year revenue and expense by service line and cost category, formatted for rate modeling
- **Operational Data Package:** Tonnage, routing, and efficiency data formatted for operational analysis
- **Customer Data Package:** Billing, service levels, and customer demographics
- Each package available in Excel (formatted) and CSV formats

**Custom Data Export Builder**
- User interface for selecting specific data elements
- Filtering capabilities (date ranges, categories, service lines)
- Format selection (Excel with formatting, CSV, JSON)
- Preview before export
- Save custom export configurations for reuse
- Download history tracking

**Basic Summary Reporting**
- Standardized monthly/quarterly summary reports
- Executive summary format (PDF)
- Compliance documentation templates
- Automated report generation option
- Report scheduling (optional)

**Deliverables:**
- 3 pre-built data packages
- Custom export builder interface
- Report generation system
- User guides for export features

### Phase 7: Testing & Quality Assurance (2-3 weeks)
**Objective:** Ensure system reliability, data accuracy, performance, and usability

**Functional Testing**
- Test all data import workflows with real data
- Verify validation rules catch errors correctly
- Test all dashboard calculations and visualizations
- Verify export outputs match expected formats
- Test user permissions and access control
- Verify audit trails and data lineage tracking

**Data Accuracy Testing**
- Reconcile imported data against source systems
- Verify calculations match manual analysis
- Test aggregation and summarization logic
- Validate financial calculations (budget variance, trends, etc.)
- Test data transformation logic

**Performance Testing**
- Test with expected data volumes (multi-year datasets)
- Verify dashboard load times meet targets
- Test concurrent user access
- Verify export generation times
- Test API response times

**Security Testing**
- Penetration testing of authentication system
- Test role-based access controls
- Verify data isolation between users
- Test API security and rate limiting
- Review code for security vulnerabilities

**User Acceptance Testing**
- Conduct UAT sessions with representatives from each user role
- Test real-world workflows end-to-end
- Gather usability feedback
- Test with actual source data files
- Verify system meets requirements document

**Issue Resolution**
- Document all identified issues
- Prioritize and fix critical and high-priority issues
- Retest after fixes
- Performance optimization based on testing results

**Deliverables:**
- Test Plans and Test Cases
- Test Results and Issue Reports
- Performance Benchmarks
- Security Assessment Report
- UAT Sign-off

### Phase 8: Deployment & Training (2-3 weeks)
**Objective:** Successfully launch the system and ensure user adoption

**Production Deployment**
- Deploy frontend to Vercel production environment
- Deploy backend to cloud hosting platform
- Configure production PostgreSQL database
- Set up cloud file storage
- Configure production security settings (HTTPS, CORS, etc.)
- Set up monitoring and error tracking (Sentry)
- Configure automated database backups
- Perform final production smoke tests

**User Training**
- Conduct role-specific training sessions:
  - **Analyst Training:** Data import workflows, validation, dashboard usage, export features (3 hours)
  - **Executive Training:** Dashboard navigation, metrics interpretation, basic exports (1.5 hours)
  - **Consultant Training:** Export capabilities, API access, data packages (2 hours)
- Provide hands-on practice with real scenarios
- Record training sessions for future reference

**Documentation & Support**
- Create comprehensive user documentation:
  - Quick start guides for each user role
  - Data import procedures and troubleshooting
  - Dashboard user guides with metric definitions
  - Export guide with examples
  - API documentation with code samples
- Create administrator documentation:
  - User management procedures
  - System monitoring and maintenance
  - Backup and recovery procedures
  - Troubleshooting guide
- Establish support procedures and contact information
- Monitor initial system usage and provide support

**Go-Live Support**
- Assist with first real data imports
- Monitor system performance closely
- Provide rapid response to any issues
- Gather user feedback for potential improvements

**Deliverables:**
- Production deployment
- Training sessions (recorded)
- Complete user documentation
- Administrator documentation
- Support procedures and contacts
- Go-live support (first 2 weeks)

## 3. Schedule and Cost Estimates

### Timeline
**Total Project Duration:** 24-30 weeks (6-7.5 months)

| Phase | Duration |
|-------|----------|
| Requirements Gathering & Analysis | 3-4 weeks |
| UX Design & Prototyping | 2-3 weeks |
| Foundation & Core Infrastructure | 3-4 weeks |
| Data Integration Development | 5-6 weeks |
| Dashboard Development | 4-5 weeks |
| Export & Reporting System | 3-4 weeks |
| Testing & Quality Assurance | 2-3 weeks |
| Deployment & Training | 2-3 weeks |
| *Buffer for revisions and adjustments* | *2-4 weeks* |

### Professional Services Costs (Time & Materials)

**Hourly Rate:** $150 per hour

| Phase | Estimated Hours | Cost Range |
|-------|----------------|------------|
| Requirements Gathering & Analysis | 120-150 hours | $18,000 - $22,500 |
| UX Design & Prototyping | 80-120 hours | $12,000 - $18,000 |
| Foundation & Core Infrastructure | 120-160 hours | $18,000 - $24,000 |
| Data Integration Development | 200-250 hours | $30,000 - $37,500 |
| Dashboard Development | 160-200 hours | $24,000 - $30,000 |
| Export & Reporting System | 120-160 hours | $18,000 - $24,000 |
| Testing & Quality Assurance | 80-120 hours | $12,000 - $18,000 |
| Deployment & Training | 60-80 hours | $9,000 - $12,000 |
| **Total Professional Services** | **940-1,240 hours** | **$141,000 - $186,000** |

### Infrastructure & Platform Costs

**Initial Setup (One-Time)**
- Cloud platform account setup and configuration: Included in professional services

**Monthly Ongoing Costs (Post-Launch)**
- PostgreSQL database hosting (managed cloud service) ~ $50-100/month
- Backend hosting (cloud compute with auto-scaling) ~ $50-100/month
- Frontend hosting (Vercel Pro plan) ~ $20/month
- Cloud file storage ~ $10-30/month
- Error tracking and monitoring (Sentry) ~ $25/month
- **Total: ~$155-275/month or ~$1,860-3,300/year**

*Note: Actual infrastructure costs will vary based on data volume, user activity, and selected cloud provider. Estimates assume moderate usage for a municipal operation with 5-15 active users.*

### Invoicing
- Professional services (pre-launch) invoiced monthly based on actual hours worked
- Ongoing infrastructure costs (post-launch) invoiced monthly

## 4. Assumptions

### Technical Assumptions
- Data will be provided in Excel or CSV format (or via API/database access if available)
- Source data systems (General Ledger, Billing, Routing, Payroll, Telemetrics, and Scalehouse systems) can provide data exports
- Data structures are reasonably consistent across time periods (or inconsistencies can be documented and handled)
- Historical data is available for at least 2-3 years for all major systems
- Data exports can be obtained at least monthly (more frequent is better)
- City can provide access to sample data files during requirements phase
- No direct system-to-system integration required (data will be imported via file upload)

### Platform & Infrastructure Assumptions
- Application will be hosted on cloud platforms (Vercel for frontend, cloud provider for backend/database)
- City of Spokane will be responsible for ongoing infrastructure costs after launch
- No on-premise installation or integration with City IT infrastructure required
- Internet connectivity is available for all end users
- Modern web browsers (Chrome, Firefox, Safari, Edge - recent versions) will be used
- Users have access to computers/tablets with sufficient performance for web applications

### Project Execution Assumptions
- City will designate a primary project manager and point of contact
- Subject matter experts (finance staff, division director, consultant) will be available for scheduled meetings
- Sample data from all source systems will be provided within first 2 weeks of project
- Feedback on deliverables will be provided within 5 business days
- One designated person from City has authority to approve deliverables and requirements
- Training will be conducted remotely via web conferencing (unless in-person is preferred and arranged)
- City can provide access to external consultant(s) for requirements and UAT sessions

### Data & Security Assumptions
- City of Spokane owns all data uploaded to and stored in the system
- Standard security practices will be implemented (HTTPS, encrypted passwords, JWT tokens, secure sessions)
- Role-based access control will appropriately segregate data access
- System will comply with general data protection best practices for municipal government
- No specific regulatory compliance requirements (HIPAA, SOX, etc.) apply beyond standard municipal data practices
- Regular automated backups will be configured through cloud database platform
- Data retention policies will be defined during requirements phase

### Support & Maintenance Assumptions
- Post-launch support and maintenance are not included in this proposal (can be scoped separately)
- Bug fixes and critical issues for the first 60 days after launch are included
- Minor adjustments to dashboards or exports during the first 60 days are included
- Future enhancements, new integrations, or significant modifications will be scoped separately
- Comprehensive documentation will be provided for system administration and ongoing operations
- City is responsible for obtaining data exports from source systems and importing to platform

### User Assumptions
- Approximately 3-5 finance analysts/staff users
- Approximately 1-3 executive/management users
- Approximately 1-3 external consultant users
- Users have intermediate computer skills and familiarity with Excel
- Users have experience working with financial and operational data
- Training can be conducted in focused sessions during business hours

### System Integration Assumptions
- Each source system (GL, Billing, Routing, Payroll, Telemetrics, Scalehouse) can export data in a consistent format
- Data exports can be scheduled (manually or automatically) at least monthly
- Data fields are reasonably well-documented or can be explained by subject matter experts
- Source system changes will be communicated so import processes can be updated if needed
- No real-time integration or live API connections to source systems are required
- Data imports will be managed by trained City staff after deployment

## 5. Out of Scope

The following items are explicitly **not included** in this proposal but could be added as separate phases or enhancements:

### Advanced Analytics
- Predictive modeling or forecasting algorithms
- Machine learning or AI-based recommendations
- Statistical analysis beyond basic trends and aggregations
- Rate modeling calculations (platform exports data for use in existing rate models)
- Financial projections or scenario planning tools

### Additional Integrations
- Direct API integrations to source systems (file-based imports only)
- Integration with GIS systems for spatial analysis
- Integration with asset management systems
- Integration with customer service/CRM systems
- Real-time data synchronization

### Extended Features
- Public-facing dashboards or citizen portals
- Mobile applications (iOS/Android native apps)
- Automated alerting and notification system
- Advanced workflow management
- Document management system
- Customer communication tools

### Data Migration & Historical Cleanup
- Extensive data cleaning or transformation of historical data
- Reconciliation of historical inconsistencies across systems
- Bulk import of 5+ years of historical data (initial scope covers recent 2-3 years)

---

## 7. Next Steps

1. **Review and discuss this proposal** with Division leadership and key stakeholders
2. **Address any questions or modifications needed** to scope, timeline, or costs
3. **Provide access to sample data** from all source systems for validation during requirements phase
4. **Identify project team members** (project manager, subject matter experts, IT contact)
5. **Finalize scope and budget approval** with City leadership
6. **Execute contract** and schedule project kickoff meeting
7. **Begin Phase 1: Requirements Gathering** with stakeholder interviews

We look forward to partnering with you and the City of Spokane to deliver a platform that transforms their data management capabilities and supports long-term financial sustainability for the Solid Waste Division.

---

**Contact Information:**
JMS Analytics
Joel Sherman
joel@jms-analytics.com
503-913-0478