# Lab 1: Advanced Identity and Access Management (IAM) in DevSecOps

This repository contains the documentation and configuration files for Lab 1 of the DevSecOps series. The lab focuses on identifying IAM vulnerabilities in AWS and implementing Policy-as-Code in Kubernetes.

## 🎯 Learning Objectives
*   **AWS IAM:** Identify and exploit privilege escalation vulnerabilities in trust policies.
*   **Kubernetes Security:** Implement **Policy-as-Code** using Open Policy Agent (OPA).
*   **Least Privilege:** Configure secure ServiceAccount bindings.
*   **Best Practices:** Apply IAM security standards within DevSecOps pipelines.

## 💻 Lab Environment
The lab is designed to run on **Al Nafi** cloud machines and includes:
*   Ubuntu 20.04 LTS
*   AWS CLI & `kubectl`
*   Open Policy Agent (OPA) / Gatekeeper
*   Pre-configured Kubernetes Cluster

---

## 🚀 Lab Tasks

### Task 1: AWS IAM Privilege Escalation
Demonstrates how overly permissive trust policies can lead to account compromise.
*   **Exploitation:** Assuming roles with `Principal: "*"` and region-based conditions.
*   **Remediation:** Implementing secure trust policies using specific ARNs, IP white-listing, and MFA requirements.

### Task 2: OPA Policy-as-Code for Kubernetes
Enforcing security standards at the admission control level.
*   **Setup:** Installing OPA Gatekeeper on a K8s cluster.
*   **Constraint Templates:** Defining custom Rego policies to restrict ServiceAccount usage.
*   **Enforcement:** Applying constraints to prevent pods from using unauthorized or default ServiceAccounts.

---

## 🛠️ Usage
To replicate the lab steps, follow the commands provided in the task files:
1.  **AWS Setup:** Use `trust-policy.json` and `permissions-policy.json` to test role assumptions.
2.  **K8s Policy:** Apply `serviceaccount-constraint-template.yaml` to your cluster to begin enforcing IAM boundaries.

## 📋 Prerequisites
*   Basic Linux CLI knowledge.
*   Familiarity with AWS IAM (JSON policy structure).
*   Basic understanding of Kubernetes YAML and Pod specs.

---
*Note: This lab is for educational purposes only. Always follow the principle of least privilege in production environments.*
