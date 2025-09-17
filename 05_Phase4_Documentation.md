# Phase 4: Process Automation (Admin)
## 1. Validation Rules

- From Date cannot be greater than To Date.
- Reason field must be filled in before submitting a leave request.
- Employees cannot apply for more leaves than their available balance.
- Duplicate leave requests for the same period are restricted.

## 2. Workflow Rules (Legacy, but still considered in implementation)

- Auto-update Status: When a leave request is submitted, set status to “Pending Approval.”
- Email Alert: Notify manager when a new leave request is submitted.

## 3. Process Builder (Now replaced by Flows, but documented for understanding)

### On Leave Request Submission:

- Update status → “Pending Approval.”
- Notify manager → via Email Alert.
- Create a Task for the manager → “Review Leave Request.”

## 4. Flow Builder

### Record-Triggered Flows:

- When leave is Approved → Update Leave Balance (reduce remaining days).
- When leave is Rejected → Notify employee with rejection reason.
- When leave is Cancelled → Recalculate Leave Balance.

### Screen Flows (for employees):

Guided process to apply for leave.
- Step 1: Select Leave Type.
- Step 2: Pick Dates.
- Step 3: Provide Reason.
- Step 4: Review & Submit.

### Scheduled Flows:

- Send monthly leave balance summaries to employees.
- Auto-update status for expired requests (e.g., if leave date has passed but no action taken → mark as “Expired”).

### Auto-Launched Flows:

- Triggered by Approval/Rejection → Sends Email/SMS notification.

## 5. Approval Process

- Step 1: Employee submits request → Status = Pending.
- Step 2: Manager receives approval request.
- Step 3: Manager approves or rejects.
- Step 4: If approved → Update Leave Balance.
- Step 5: If rejected → Send email to employee.

## 6. Email Alerts

- Leave Request Submitted: Sent to Manager.
- Leave Request Approved: Sent to Employee.
- Leave Request Rejected: Sent to Employee.
- Leave Balance Reminder: Monthly email to Employee.

## 7. Field Updates

- On Approval: Status → Approved.
- On Rejection: Status → Rejected.
- On Cancellation: Status → Cancelled.

## 8. Tasks & Custom Notifications

- Task: Auto-created for managers to review requests.
- Custom Notification (via Salesforce App): Push notification sent when a new leave request is assigned to a manager.

## ✅ Phase 4 Outcome:

- All leave management workflows automated (submission, approval, balance updates, rejection, cancellation).
- Employees & managers receive real-time notifications.
- HR/Admin has complete visibility with fewer manual interventions.
