````markdown
# DevSecOps IAM & Kubernetes Security 

## 📌 Overview
This project demonstrates advanced Identity and Access Management (IAM) concepts in a DevSecOps environment using AWS and Kubernetes. The lab focuses on identifying IAM privilege escalation risks, securing cloud access policies, and enforcing Kubernetes security standards through Policy-as-Code using Open Policy Agent (OPA) Gatekeeper.

---

# 📂 Project Structure

```bash
.
├── README.md
├── aws/
│   ├── trust-policy.json
│   └── permissions-policy.json
│
├── kubernetes/
│   ├── serviceaccount-constraint-template.yaml
│   ├── serviceaccount-constraint.yaml
│   └── pod-test.yaml
│
└── docs/
    ├── task1-aws-iam.md
    └── task2-opa-gatekeeper.md
````

---

# 🎯 Learning Objectives

* Identify AWS IAM privilege escalation vulnerabilities
* Secure IAM trust policies
* Implement Kubernetes Policy-as-Code
* Configure secure ServiceAccount bindings
* Apply DevSecOps security best practices

---

# 💻 Lab Environment

| Component          | Details                |
| ------------------ | ---------------------- |
| OS                 | Ubuntu 20.04 LTS       |
| Cloud              | Al Nafi Cloud Machines |
| AWS CLI            | Installed              |
| kubectl            | Installed              |
| OPA Gatekeeper     | Installed              |
| Kubernetes Cluster | Pre-configured         |

---

# 🚀 Lab Tasks

## 🔐 Task 1: AWS IAM Privilege Escalation

This task demonstrates how insecure IAM trust policies can lead to unauthorized role assumptions and privilege escalation.

### Exploitation

* Roles configured with:

  ```json
  "Principal": "*"
  ```
* Weak conditions allowing unauthorized access

### Remediation

* Use specific AWS ARNs
* Enforce MFA
* Restrict source IPs
* Apply least privilege permissions

---

## ☸️ Task 2: Kubernetes Policy-as-Code

This task demonstrates enforcing Kubernetes security policies using OPA Gatekeeper.

### Objectives

* Install OPA Gatekeeper
* Create Rego constraint templates
* Restrict unauthorized ServiceAccounts
* Block pods using default ServiceAccounts

---

# 🛠️ Installation & Setup

## 1️⃣ Clone Repository

```bash
git clone https://github.com/your-repo/devsecops-iam-lab.git
cd devsecops-iam-lab
```

---

## 2️⃣ Install OPA Gatekeeper

```bash
kubectl apply -f https://raw.githubusercontent.com/open-policy-agent/gatekeeper/release-3.14/deploy/gatekeeper.yaml
```

Verify installation:

```bash
kubectl get pods -n gatekeeper-system
```

---

## 3️⃣ Apply Constraint Templates

```bash
kubectl apply -f kubernetes/serviceaccount-constraint-template.yaml
kubectl apply -f kubernetes/serviceaccount-constraint.yaml
```

---

# 🧪 Testing

## AWS IAM Role Assumption

```bash
aws sts assume-role \
  --role-arn arn:aws:iam::ACCOUNT_ID:role/TestRole \
  --role-session-name security-test
```

---

## Kubernetes Policy Test

```bash
kubectl apply -f kubernetes/pod-test.yaml
```

Expected output:

```bash
Error from server ([denied by serviceaccount-policy] unauthorized service account)
```

---

# 📋 Prerequisites

* Basic Linux command-line knowledge
* Understanding of AWS IAM
* Basic Kubernetes YAML knowledge
* Access to AWS account
* kubectl configured

---

# 🔒 Security Best Practices

* Principle of Least Privilege (PoLP)
* IAM role hardening
* Policy-as-Code enforcement
* Kubernetes admission control security
* Continuous compliance validation

---

# 📖 Technologies Used

| Technology     | Purpose                 |
| -------------- | ----------------------- |
| AWS IAM        | Identity Management     |
| Kubernetes     | Container Orchestration |
| OPA Gatekeeper | Policy Enforcement      |
| Rego           | Policy Language         |
| kubectl        | Kubernetes CLI          |

---

# ⚠️ Disclaimer

This project is intended for educational and ethical security training purposes only.

Do not test these techniques on systems without authorization.

---

# 👨‍💻 Author

DevSecOps Security Lab Series

```
```
