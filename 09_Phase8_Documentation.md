# Phase 8: Deployment & Release Management
## 🔹 Objective

- To ensure smooth and error-free deployment of Leave Tracker customizations from development to higher environments (UAT, Production) using best practices and tools.

## 1. Deployment Approaches

- Change Sets (click-based, easy for Admins, limited for Dev-heavy projects).
- VS Code with Salesforce CLI (SFDX) – developer-friendly, supports version control (GitHub/GitLab/Bitbucket).
- CI/CD Tools: GitHub Actions, Bitbucket Pipelines, or Copado for automated deployment.

## 2. VS Code Deployment Setup
### 🛠️ Prerequisites
- Install Visual Studio Code.
- Install Salesforce CLI (SFDX).
- Install Salesforce Extension Pack in VS Code.
- Connect Org → sfdx force:auth:web:login -d -a DevHub.

    📂 Sample Project Structure (VS Code)
    leave-tracker-project/
     ├── force-app/
     │    └── main/
     │         └── default/
     │              ├── classes/        (Apex Classes)
     │              ├── lwc/            (Lightning Web Components)
     │              ├── objects/        (Custom Objects)
     │              ├── triggers/       (Apex Triggers)
     │              └── email/          (Email Templates)
     ├── sfdx-project.json
     └── .gitignore

💻 Sample Deployment Commands
# Retrieve metadata from source org
sfdx force:source:retrieve -m ApexClass,CustomObject,LWC

# Deploy metadata to target org
sfdx force:source:deploy -p force-app/main/default

# Run all tests before deployment
sfdx force:apex:test:run --resultformat human --codecoverage

3. Deployment Checklist

✅ Code Quality Check (PMD, Prettier for LWC).
✅ Apex Test Coverage ≥ 75%.
✅ Run Validation Deployment (test without committing).
✅ Backup Production metadata before final push.
✅ Post-deployment steps (activate Flows, verify Email Deliverability).

4. CI/CD Integration (Optional Advanced)

GitHub Actions: Automate deployments on every push.

Copado / Gearset: Enterprise-grade release management.

5. Visuals
🖼️ Example Deployment Architecture

(Dev Org → GitHub Repo → UAT Sandbox → Production Org)

Developer Org → GitHub (Main Branch) → UAT Sandbox → Production
         ↑               ↓
       VS Code       CI/CD Pipeline

🖼️ Screenshot Suggestions (for your doc):

VS Code with project folder open (showing Apex, LWC, Objects).

Terminal with SFDX commands running.

Change Set setup page in Salesforce (for Admin audience).

Deployment Status Page (in Setup → Deployment Status).

👉 This way Phase 8 has step-by-step clarity + VS Code integration + visuals so that it’s realistic for your project documentation.
