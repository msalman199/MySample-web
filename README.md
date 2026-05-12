# Lab 1: Advanced Identity and Access Management (IAM) in DevSecOps

This repository contains the walkthrough and configuration files for Lab 1, focusing on advanced IAM concepts, privilege escalation exploitation, and implementing Policy-as-Code.

## 📂 Project Structure

```text
.
├── README.md
├── aws-iam/
│   ├── trust-policy.json           # Vulnerable trust policy (Principal: "*")
│   ├── permissions-policy.json     # Policy with S3 and EC2 describe actions
│   └── secure-trust-policy.json    # Remediated policy with IP and MFA conditions
└── k8s-opa/
    ├── gatekeeper-install.sh       # Script to deploy OPA Gatekeeper
    ├── serviceaccount-template.yaml # Rego-based ConstraintTemplate
    └── serviceaccount-constraint.yaml # Specific enforcement parameters
```

## 🎯 Learning Objectives
By completing this lab, you will:
*   **Identify IAM Vulnerabilities:** Exploit overly permissive AWS IAM trust policies.
*   **Policy-as-Code:** Implement security guardrails using **Open Policy Agent (OPA)**.
*   **K8s Security:** Configure least-privilege `ServiceAccount` bindings.
*   **Security Best Practices:** Recognize and mitigate common IAM misconfigurations.

## 💻 Lab Environment
The lab is pre-configured on **Al Nafi** cloud machines:
*   **Tools:** AWS CLI, `kubectl`, Open Policy Agent (OPA)
*   **OS:** Ubuntu 20.04 LTS

---

## 🚀 Lab Tasks

### Task 1: AWS IAM Privilege Escalation
Explore how weak trust policies allow unauthorized users to assume sensitive roles.
*   **Exploitation:** Creating a role with a broad trust policy and assuming it via STS.
*   **Remediation:** Updating the role with a secure policy using specific ARNs, IP restrictions, and MFA.

### Task 2: OPA Policy-as-Code for Kubernetes
Enforce security standards automatically using Gatekeeper.
*   **Setup:** Installing Gatekeeper on the cluster.
*   **Rego Policies:** Defining a `ConstraintTemplate` to restrict `ServiceAccount` usage.
*   **Enforcement:** Applying constraints to prevent unauthorized pod deployments.

---

## 🛡️ Best Practices Applied
1.  **Least Privilege:** Restricting role assumption to specific principals.
2.  **Condition Keys:** Using `aws:SourceIp` and `aws:MultiFactorAuthPresent`.
3.  **Admission Control:** Using Policy-as-Code to stop insecure deployments at the gate.

---
**Disclaimer:** For educational purposes only. Always test IAM changes in a sandbox environment before applying to production.
