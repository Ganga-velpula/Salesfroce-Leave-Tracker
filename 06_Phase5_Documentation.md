# Phase 5: Apex Programming (Developer)
## 1. Classes & Objects

- LeaveRequestController: Handles leave application logic (submit, update, approve, reject).
- LeaveBalanceHandler: Manages employee leave balances (deduct on approval, update on cancellation).
- EmailNotificationService: Sends approval/rejection notifications.
- Utility Classes: For reusable logic like date validation, string formatting, and error handling.

## 2. Apex Triggers

### Before Insert/Update:

- Validate leave dates (From_Date ≤ To_Date).
- Prevent overlapping leave requests.

### After Insert:
- Notify manager of new leave request submission.

### After Update:

- If Status = Approved → Deduct leave balance.
- If Status = Rejected → Send rejection email.
- If Status = Cancelled → Restore leave balance.

## 3. Trigger Design Pattern

### Handler Class Pattern followed:

- One trigger per object (e.g., LeaveRequestTrigger).
- Delegates logic to LeaveRequestHandler class.
- Improves readability, reusability, and testability.

## 4. SOQL & SOSL Usage

### SOQL:

- Fetch leave requests of current user ([SELECT Id, From_Date__c, To_Date__c, Status__c FROM LeaveRequest__c WHERE User__c = :UserInfo.getUserId()]).
- Fetch manager details for email notifications.
- Aggregate queries for reports (e.g., total leaves per type).

### SOSL:

- Used for searching leave requests by employee name or reason.
- Collections (List, Set, Map)
- List: Store multiple leave requests fetched from SOQL.
- Set: Avoid duplicate leave request IDs during processing.
- Map: Map employee IDs to their leave balances for bulk updates.

### Control Statements

- If-Else: Approve vs Reject logic.
- For Loops: Bulk processing of leave requests.
- Switch (with enums): Handle leave types (Sick Leave, Casual Leave, Earned Leave).

## 5. Asynchronous Apex

### Future Methods:

- Send emails asynchronously for better performance.

### Batch Apex:

- Monthly batch job to recalculate leave balances.
- Archive old leave records.

### Queueable Apex:

- Process bulk leave balance adjustments during migrations.

### Scheduled Apex:

- Automatic monthly leave balance top-up.
- Reminder emails for unused leaves at year-end.

## 6.Exception Handling

- Try-Catch Blocks: Handle DML and SOQL exceptions.
- Custom Exceptions: For business rules like “Insufficient Leave Balance.”
- Error Logging: Store errors in a custom object Error_Log__c for admin review.

## 7. Test Classes

- Achieve > 85% coverage.
### Scenarios covered:

- Leave request submission (valid & invalid).
- Overlapping leave requests.
- Approval & Rejection flow.
- Cancellation and balance update.
- Email sending functionality.

Mock Data Creation: LeaveRequestSampleData utility class for test setup.

## ✅ Phase 5 Outcome:

- Robust Apex code with reusable classes and triggers.
- Asynchronous processing ensures performance.
- Proper exception handling + test coverage makes the system reliable and deployment-ready.****
