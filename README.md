# Lab 1: Advanced Identity and Access Management (IAM) in DevSecOps

This repository contains the walkthrough and configuration files for Lab 1, focusing on advanced IAM concepts, privilege escalation exploitation, and implementing Policy-as-Code.

## 🎯 Learning Objectives
By completing this lab, you will:
*   **Identify IAM Vulnerabilities:** Exploit overly permissive AWS IAM trust policies.
*   **Policy-as-Code:** Implement security guardrails using **Open Policy Agent (OPA)** and Gatekeeper.
*   **K8s Security:** Configure least-privilege `ServiceAccount` bindings in Kubernetes.
*   **Security Best Practices:** Recognize and mitigate common IAM misconfigurations in DevSecOps pipelines.

## 📋 Prerequisites
*   Basic understanding of Cloud Computing and AWS services.
*   Familiarity with the Linux command line.
*   Understanding of Kubernetes fundamentals, YAML, and JSON.

## 💻 Lab Environment
The lab is pre-configured on **Al Nafi** cloud machines and includes:
*   **OS:** Ubuntu 20.04 LTS
*   **Tools:** AWS CLI, `kubectl`, Open Policy Agent (OPA)
*   **Access:** Sample Kubernetes cluster access

---

## 🚀 Lab Tasks

### Task 1: AWS IAM Privilege Escalation
In this task, we explore how weak trust policies allow unauthorized users to assume sensitive roles.
*   **Subtask 1.1:** Creating a vulnerable IAM role with a broad trust policy (`Principal: "*"`).
*   **Subtask 1.2:** Attaching S3 and EC2 permissions to the role.
*   **Subtask 1.3:** Exploiting the misconfiguration using `aws sts assume-role` and escalating privileges to list S3 buckets and EC2 instances.
*   **Subtask 1.4:** Implementing a **Secure Trust Policy** using specific ARNs, IP restrictions, and MFA conditions.

### Task 2: OPA Policy-as-Code for Kubernetes
This task demonstrates how to enforce security policies automatically using Gatekeeper.
*   **Subtask 2.1:** Setting up **OPA Gatekeeper** on the cluster.
*   **Subtask 2.2:** Creating a `ConstraintTemplate` using **Rego** to define rules for `ServiceAccount` usage.
*   **Subtask 2.3:** Applying constraints to ensure pods only use approved ServiceAccounts, preventing unauthorized permission usage within the cluster.

---

## 🛠️ Key Configuration Files
*   `trust-policy.json`: Initial vulnerable AWS trust policy.
*   `permissions-policy.json`: Permissions attached to the vulnerable role.
*   `secure-trust-policy.json`: Remediation policy with strict conditions.
*   `serviceaccount-constraint-template.yaml`: OPA/Rego template for K8s admission control.

---

## 🛡️ Best Practices Applied
1.  **Least Privilege:** Restricting role assumption to specific principals.
2.  **Condition Keys:** Using `aws:SourceIp` and `aws:MultiFactorAuthPresent`.
3.  **Admission Control:** Using Policy-as-Code to prevent insecure deployments before they reach the cluster.

---
**Disclaimer:** This lab is for educational purposes only. Always test IAM changes in a sandbox environment before applying to production.
