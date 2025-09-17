# Phase 8: Deployment & Release Management
## 🔹 Objective

- To ensure smooth and error-free deployment of Leave Tracker customizations from development to higher environments (UAT, Production) using best practices and tools.

## 1. Deployment Approaches

- Change Sets (click-based, easy for Admins, limited for Dev-heavy projects).
- VS Code with Salesforce CLI (SFDX) – developer-friendly, supports version control (GitHub/GitLab/Bitbucket).
- CI/CD Tools: GitHub Actions, Bitbucket Pipelines, or Copado for automated deployment.
  
## 3. Change Sets

Used Change Sets for deploying metadata between environments (Sandbox → Production).
### Included:

- Custom Objects (LeaveRequest__c, LeaveBalance__c)
- Apex Classes (LeaveRequestController, Triggers)
- Lightning Web Components (applyLeave, myLeaves, leaveRequest)
- Email Templates & Flows

## 3. VS Code Deployment Setup
### 🛠️ Prerequisites
- Install Visual Studio Code.
- Install Salesforce CLI (SFDX).
- Install Salesforce Extension Pack in VS Code.
- Connect Org → sfdx force:auth:web:login -d -a DevHub.

   - 📂 Sample Project Structure (VS Code)
          <img width="873" height="362" alt="image" src="https://github.com/user-attachments/assets/21220f0a-6324-4ff3-8680-6e42230da82b" />


    - 💻 Sample Deployment Commands
        - Retrieve metadata from source org
            - sfdx force:source:retrieve -m ApexClass,CustomObject,LWC
        - Deploy metadata to target org
            - sfdx force:source:deploy -p force-app/main/default
        - Run all tests before deployment
            - sfdx force:apex:test:run --resultformat human --codecoverage

## 4. Deployment Checklist

- ✅ Code Quality Check (PMD, Prettier for LWC).
- ✅ Apex Test Coverage ≥ 75%.
- ✅ Run Validation Deployment (test without committing).
- ✅ Backup Production metadata before final push.
- ✅ Post-deployment steps (activate Flows, verify Email Deliverability).

## 5. CI/CD Integration (Optional Advanced)

- GitHub Actions: Automate deployments on every push.
- Copado / Gearset: Enterprise-grade release management.


