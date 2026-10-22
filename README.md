# CI/CD Pipeline: Dockerized Web App on AWS EC2 🚀

An automated Continuous Integration and Continuous Deployment (CI/CD) pipeline built to deploy static web applications instantly to an AWS EC2 Linux instance using Docker and GitHub Actions.

---

## 🏗️ Architecture & Workflow
1. **Source Control:** Code changes are pushed to the `main` branch on GitHub.
2. **Execution:** A self-hosted GitHub Actions runner active on the EC2 instance detects the push.
3. **Containerization:** Docker builds a fresh Nginx image containing the updated code.
4. **Zero-Downtime Deployment:** The old container is safely replaced with the new version, instantly updating the live public website.

---

## 🛠️ Step-by-Step Implementation & Proof

### 1. Manual Verification & Container Build on EC2
Before setting up automation, the application was manually containerized, tested, and verified using Docker and Nginx on an Ubuntu EC2 instance.
![Manual Build and Docker PS](assets/manual-deploy.jpg)

### 2. Self-Hosted Runner Setup
To securely deploy updates without opening vulnerable inbound SSH ports to changing public runner IPs, a secure self-hosted GitHub Actions runner was configured directly on the EC2 instance.
![Runner Configuration](assets/runner-config.jpg)

### 3. CI/CD Workflow Configuration (`deploy.yml`)
The automated pipeline configuration defines the triggers, build steps, and container refresh logic.
![Workflow YAML File](assets/workflow-file.jpg)

### 4. Automated Pipeline Execution
Pushing code changes automatically triggers the GitHub Actions workflow, completing builds and deployments seamlessly.
![GitHub Actions Success](assets/actions-success.jpg)

### 5. Live Website Verification (Version 1 & Version 2)
* **Version 1 (Initial Deployment):**
  ![Webpage V1](assets/webpage-v1.png)

* **Version 2 (Post-Commit Auto-Update):** After modifying `index.html` on GitHub, the pipeline automatically deployed the update without manual intervention.
  ![Webpage V2](assets/webpage-v2.png)

---
