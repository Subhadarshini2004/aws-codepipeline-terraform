# AWS CodePipeline using Terraform & DevSecOps with GitHub Actions and Kubernetes Sealed Secrets

## Project Overview

This project demonstrates the automation of a complete CI/CD pipeline on AWS using **Terraform**, **GitHub Actions**, and **Kubernetes Sealed Secrets**. It consists of two main tasks:
- **Task 1**: Provisioning AWS CodePipeline using Terraform.
- **Task 2**: Integrating DevSecOps practices using GitHub Actions with tools like `tfsec`, `Trivy`, and Sealed Secrets for Kubernetes.


## ✅ Task 1: CodePipeline using Terraform

Terraform is used to provision the following AWS resources:

### Infrastructure Provisioned:
- **S3 Bucket** – for CodePipeline artifacts.
- **IAM Roles and Policies** – for CodePipeline, CodeBuild, and EC2.
- **CodePipeline** – triggers on code changes from GitHub.
- **CodeBuild** – builds the code (can run tests or validations).
- **EC2 Instance** – as a deployment target.
  
### Files Created:
- `main.tf` – contains all Terraform code.
- `variables.tf` – defines input variables.
- `outputs.tf` – defines output values like EC2 IP.
- `provider.tf` – configures AWS provider.

### Flow:
1. Developer pushes code to GitHub.
2. CodePipeline fetches code from GitHub.
3. CodeBuild builds the code.
4. CodeDeploy/EC2 deploys the application.

## ✅ Task 2: DevSecOps with GitHub Actions and Sealed Secrets

### 🔐 DevSecOps Practices Implemented:
- **CI/CD Workflow with GitHub Actions** triggered on push.
- **Security Scanning Tools**:
  - [`tfsec`]: Scans Terraform code for misconfigurations.
  - [`Trivy`]: Scans Docker images for vulnerabilities.
- **Kubernetes Sealed Secrets**:
  - Secrets encrypted using `kubeseal` and stored in GitHub as `sealed-secret.yaml`.
  - A `deployment.yaml` file is created which pulls values from the Kubernetes secret.

### ⚠️ Important Note:
Due to the limitations of the **Killercoda environment**, the final GitHub Actions step **did not apply the sealed secret and deployment.yaml to a live Kubernetes cluster**.
However, the YAML files were created, tested, and pushed to GitHub for demonstration.

# 📁 Repository Structure
.
├── main.tf
├── variables.tf
├── outputs.tf
├── provider.tf
├── sealed-secret.yaml
├── deployment.yaml
├── .github
│   └── workflows
│       └── main.yml
└── README.md

⚙️ Tools Used
Terraform – Infrastructure as Code
AWS CodePipeline – CI/CD pipeline
AWS CodeBuild – Code building & testing
AWS EC2 – Application hosting
GitHub Actions – Workflow automation
tfsec – Terraform security scanner
Trivy – Docker vulnerability scanner
Kubernetes + Sealed Secrets – Secret management

Test Steps (Killercoda-based)
Since a live EKS cluster was not used:
Sealed Secrets were created and tested in the Killercoda Kubernetes playground.
Secrets were confirmed using kubectl and environment variables inside a running pod.

<img width="1920" height="1080" alt="Screenshot (655)" src="https://github.com/user-attachments/assets/df58b746-a8c3-4049-936e-16a456ab9a09" />
<img width="1920" height="1080" alt="Screenshot (713)" src="https://github.com/user-attachments/assets/87d98242-ce76-4b7e-ae95-b504db817140" />
<img width="1920" height="1080" alt="Screenshot (659)" src="https://github.com/user-attachments/assets/94efbdef-092f-4d76-97f2-2bd0b02b7e3e" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/c5dbc965-014e-49ae-bbc5-eedfddf19058" />

🙋 Author
P Subhadarshini Paramanik
GitHub: Subhadarshini2004

