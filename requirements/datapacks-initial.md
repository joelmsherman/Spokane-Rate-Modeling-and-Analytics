# Example Data Packages for each Phase 2 Task
Note: This should get refined as part of roadmap item "Bell & Associates Requirements Workshop".

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