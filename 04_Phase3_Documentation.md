# Phase 3: Data Modeling & Relationships
## 1. Standard & Custom Objects
### Standard Objects Used:
- User → Represents employees, managers, and HR.

### Custom Objects Created:

- Leave Request → Stores each leave application.
- Leave Balance → Tracks annual leave entitlement, used leaves, and remaining balance.
- Holiday Calendar → Stores organization-wide holidays.
- Approval History → Records manager approvals/rejections for audit purposes.

## 2. Fields

### Leave Request Object Fields:

- Employee (Lookup to User)
- Leave Type (Picklist: Sick, Casual, Earned, Maternity, etc.)
- From Date (Date)
- To Date (Date)
- Total Days (Formula: To Date – From Date – Holidays)
- Reason (Text Area)
- Status (Picklist: Draft, Submitted, Approved, Rejected, Cancelled)
- Manager Comments (Long Text)

### Leave Balance Object Fields:

- Employee (Lookup to User)
- Year (Picklist)
- Total Leaves (Number)
- Used Leaves (Number)
- Remaining Leaves (Formula: Total – Used)
  
## 3. Record Types

### Leave Request Record Types:

- Sick Leave Request
- Casual Leave Request
- Earned Leave Request
- Special Leave Request (e.g., Maternity, Paternity)
- Each record type has different page layouts and approval rules.

## 4. Page Layouts

- Employee Layout (Leave Request): Fields: From Date, To Date, Reason, Leave Type.
- Manager Layout (Leave Request): Includes additional fields: Status, Manager Comments.
- HR/Admin Layout: Full access including audit/approval history.

## 5. Compact Layouts

- For Leave Request, compact layout shows: Leave Type, Dates, Status.
- For Leave Balance, compact layout shows: Year, Remaining Leaves.

## 6. Schema Builder

Used to design relationships visually:

- User → Leave Request (Lookup)
- User → Leave Balance (Lookup)
- Holiday Calendar → Leave Request (for calculating days).

## 7. Relationships

### Lookup Relationship:

- Leave Request → User (Employee).
- Leave Balance → User.

### Master-Detail Relationship:

- Approval History → Leave Request (deletes when parent request is deleted).

### Junction Objects (if required):

- If employees can have multiple leave policies, a junction between User and Leave Policy object can be created.



## ✅ Phase 3 Outcome:

- Data model created with required custom objects and fields.
- Relationships established between employees, leave requests, balances, and holidays.
- Record types, page layouts, and compact layouts designed for different users.
- Schema validated for scalability and integration readiness.
