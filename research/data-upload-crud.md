# Data Upload Feature - Record-Level CRUD Plan

## Requirements Summary

**Core Need:** City staff need to maintain data over time, including corrections to historical records, without re-uploading entire batches.

**Key Requirements:**
- Record-level CRUD on all data (not just recent uploads)
- Edit tracking: `updated_by`, `updated_at` on every record
- Upload flow: Dashboard table → Upload modal (3 steps) → Validation results
- Single-record operations only (no bulk select/delete)
- Reject duplicates on upload (no upsert)
- Fresh field mapping each upload (no saved mappings)

**Delete Strategy:**
- **Soft delete** for parent/reference datasets (Assets, Routes, Accounts, etc.) - other records may reference them
- **Hard delete** for transactional/child datasets (monthly expenses, tonnage entries, etc.)

---

## Upload Flow

### Starting Point: Dataset Dashboard
- Paginated table of all records (server-side pagination, 50 rows default)
- Sortable columns, filterable by key fields
- Row actions: Edit (opens modal), Delete (confirmation dialog)
- "Upload Data" button in header

### Upload Modal - 3 Steps

**Step 1: File Selection**
- Drag-drop zone or file picker for CSV
- Download template link (pre-filled with column headers)
- Brief schema summary showing required vs optional fields

**Step 2: Field Mapping**
- Two-column layout: CSV columns (left) ↔ Database fields (right)
- Auto-match by exact name match, user adjusts as needed
- Required fields marked with asterisk
- "Unmapped" indicator for CSV columns that won't be imported
- Preview table showing first 5 rows with mapping applied
- Back button to re-select file, Next button to validate

**Step 3: Validation Results**
- **If errors exist:**
  - Error summary: "X of Y rows have errors"
  - Scrollable table: Row #, Field, Error Message, Value
  - "Download Error Report" button (CSV)
  - "Back" to re-upload corrected file
  - No "Import Anyway" option - must fix errors
- **If duplicates found:**
  - Error message listing duplicate natural keys
  - Must resolve before import
- **If all valid:**
  - Success summary: "X records ready to import"
  - "Confirm Import" button
  - After import: success toast, modal closes, table refreshes

---

## Dataset Classification

**Parent/Reference Datasets (Soft Delete):**
- Assets/Equipment - trucks, carts referenced by maintenance records
- Routes - referenced by route operations data
- Accounts/Cost Centers - referenced by expenses

**Transactional/Child Datasets (Hard Delete):**
- Expenses - monthly/annual entries
- Revenue/Billing - monthly entries
- Tonnage - monthly entries
- Labor/Payroll - periodic entries
- Truck Maintenance - monthly entries per vehicle
- Route Operations - monthly entries per route
- Customer Counts - point-in-time snapshots

---

## Technical Implementation

### Database Schema Pattern

**Parent dataset tables (soft delete):**
```sql
id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
-- ... dataset-specific fields ...
upload_batch_id UUID REFERENCES upload_batches(id),
created_at TIMESTAMPTZ DEFAULT now(),
created_by UUID REFERENCES auth.users(id),
updated_at TIMESTAMPTZ DEFAULT now(),
updated_by UUID REFERENCES auth.users(id),
deleted_at TIMESTAMPTZ,  -- soft delete marker
deleted_by UUID REFERENCES auth.users(id)
```

**Child dataset tables (hard delete):**
```sql
id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
-- ... dataset-specific fields ...
upload_batch_id UUID REFERENCES upload_batches(id),
created_at TIMESTAMPTZ DEFAULT now(),
created_by UUID REFERENCES auth.users(id),
updated_at TIMESTAMPTZ DEFAULT now(),
updated_by UUID REFERENCES auth.users(id)
-- no deleted_at/deleted_by - hard delete
```

**Upload tracking table:**
```sql
CREATE TABLE upload_batches (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  dataset_type TEXT NOT NULL,
  file_name TEXT NOT NULL,
  record_count INTEGER NOT NULL,
  uploaded_at TIMESTAMPTZ DEFAULT now(),
  uploaded_by UUID REFERENCES auth.users(id)
);
```

### Natural Keys for Duplicate Detection
Each dataset needs a composite key defined:
- **Expenses:** fiscal_year + account_code + cost_center
- **Revenue:** period_month + service_type + rate_class
- **Tonnage:** period_month + material_type + source
- **Customer Counts:** snapshot_date + service_level
- **Assets:** asset_id (or asset_tag)
- **Routes:** route_id
- *(Define for remaining datasets during implementation)*

### Tech Stack (from existing standards)
- **CSV Parsing:** papaparse (client-side for preview, Edge Function for validation)
- **Validation:** Zod schemas per dataset
- **Table:** TanStack Table with server-side pagination
- **Forms:** React Hook Form + Zod for edit modals
- **API:** Supabase client SDK + Edge Functions

---

## File Structure

```
src/
├── components/
│   ├── data-upload/
│   │   ├── UploadModal.tsx        # 3-step wizard shell
│   │   ├── FileSelectStep.tsx     # Step 1: file picker
│   │   ├── FieldMappingStep.tsx   # Step 2: column mapping
│   │   └── ValidationStep.tsx     # Step 3: results/confirm
│   └── data-table/
│       ├── DataTable.tsx          # Reusable paginated table
│       ├── EditRecordModal.tsx    # Single record edit form
│       └── DeleteConfirmDialog.tsx
├── app/
│   └── (dashboard)/
│       └── data/
│           └── [dataset]/
│               └── page.tsx       # Dataset dashboard page
├── lib/
│   ├── schemas/                   # Zod schemas per dataset
│   ├── queries/                   # Supabase query functions
│   └── utils/
│       └── csv-parser.ts          # papaparse wrapper
└── supabase/
    ├── migrations/                # Table schemas
    └── functions/
        └── validate-upload/       # CSV validation Edge Function
```

---

## Implementation Order

1. **Database migrations** - Create tables with metadata fields, upload_batches table
2. **DataTable component** - Reusable paginated table with edit/delete actions
3. **Edit/Delete modals** - Single record CRUD UI
4. **Upload modal shell** - 3-step wizard navigation
5. **Step 1: File select** - Drag-drop, template download
6. **Step 2: Field mapping** - Column matching UI with preview
7. **Step 3: Validation** - Edge Function + results display
8. **First dataset end-to-end** - Pick one (e.g., Expenses) and complete full flow
9. **Remaining datasets** - Replicate pattern for other 6 datasets
