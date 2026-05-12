# DevSecOps: Identity & Access Management (IAM) 
Developed through [Al Nafi Cloud](https://alnafi.cloud/) Hands-on Labs

## 🚀 Overview
This project demonstrates the implementation of secure Identity and Access Management (IAM) practices within a DevSecOps pipeline. The lab focused on the "Least Privilege" principle, ensuring that users and services have only the minimum permissions necessary to function, thereby reducing the attack surface.

## 🛠️ Tools & Technologies
* **Cloud Platform:** AWS (via Al Nafi Cloud Sandbox)
* **IAM Services:** IAM Roles, Policies, Groups, and Users
* **Security Tools:** AWS CloudTrail, IAM Access Analyzer
* **Infrastructure:** [e.g., Docker, EC2, or Kubernetes]

## 🛡️ Key Features & Implementation
* **Least Privilege Policy:** Created custom JSON policies to restrict user access to specific S3 buckets and EC2 instances.
* **Role-Based Access Control (RBAC):** Implemented IAM Roles for cross-account access and service-to-service communication.
* **Security Auditing:** Used [AWS CloudTrail](https://alnafi.com/courses/diploma-in-sysops-and-cloud) to monitor and log IAM configuration changes.
* **Multi-Factor Authentication (MFA):** Enforced MFA for all administrative accounts to prevent unauthorized access.

## 📖 Lab Workflow
1. **Initial Setup:** Configured the Al Nafi Cloud environment and initialized the AWS CLI.
2. **Policy Creation:** Defined granular permissions using the IAM Policy Simulator.
3. **User Onboarding:** Organized users into functional groups (e.g., Developers, Admins) with attached group-level policies.
4. **Monitoring:** Set up alerts for failed login attempts and unauthorized API calls.

## 💡 Key Learnings
* Understanding the difference between **Authentication (AuthN)** and **Authorization (AuthZ)**.
* Mastering the syntax of IAM JSON policy documents.
* Integrating security checks early in the DevOps lifecycle (shifting security left).

## 🏁 Conclusion
By completing this lab on the [Al Nafi Cloud platform](https://alnafi.cloud/), I gained practical experience in securing cloud infrastructure using industry-standard IAM protocols.
