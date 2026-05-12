📌 Overview

This project demonstrates advanced Identity and Access Management (IAM) concepts in a DevSecOps environment using AWS and Kubernetes. The lab focuses on identifying IAM privilege escalation risks, securing cloud access policies, and enforcing Kubernetes security standards through Policy-as-Code with Open Policy Agent (OPA) Gatekeeper.

The repository includes configuration files, IAM policies, Kubernetes manifests, and policy templates used to simulate and remediate real-world security vulnerabilities.

🎯 Learning Objectives

By completing this lab, you will learn how to:

Identify and exploit insecure AWS IAM trust policies.
Understand privilege escalation through overly permissive role assumptions.
Implement secure IAM trust relationships using:
Specific AWS ARN principals
MFA enforcement
IP address restrictions
Deploy and configure OPA Gatekeeper in Kubernetes.
Create and enforce Policy-as-Code using Rego policies.
Restrict Kubernetes pods from using unauthorized ServiceAccounts.
Apply DevSecOps security best practices and least privilege principles.
🏗️ Lab Architecture

The lab environment consists of:

AWS IAM Roles & Policies
Kubernetes Cluster
OPA Gatekeeper Admission Controller
ServiceAccount Security Policies
💻 Lab Environment

The lab is designed to run on Al Nafi Cloud Machines with the following tools pre-installed:

Component	Version
Ubuntu	20.04 LTS
AWS CLI	Latest
kubectl	Latest
Kubernetes Cluster	Pre-configured
OPA Gatekeeper	Installed
📂 Project Structure
.
├── aws/
│   ├── trust-policy.json
│   ├── permissions-policy.json
│
├── kubernetes/
│   ├── serviceaccount-constraint-template.yaml
│   ├── serviceaccount-constraint.yaml
│   ├── pod-test.yaml
│
├── docs/
│   ├── task1-iam-escalation.md
│   ├── task2-opa-policy.md
│
└── README.md
🚀 Lab Tasks
🔐 Task 1: AWS IAM Privilege Escalation

This task demonstrates how insecure IAM trust policies can lead to unauthorized role assumption and privilege escalation.

🧪 Exploitation Scenario

An IAM role is configured with:

"Principal": "*"

Combined with weak conditions, attackers may assume the role from unauthorized accounts or regions.

⚠️ Security Risks
Unauthorized cross-account access
Privilege escalation
Full account compromise
Credential abuse
✅ Remediation Techniques

Secure trust policies by implementing:

Specific IAM Role/User ARNs
MFA enforcement
Source IP restrictions
Least privilege permissions
Region-based controls
Example Secure Trust Policy
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "AWS": "arn:aws:iam::123456789012:user/security-admin"
      },
      "Action": "sts:AssumeRole",
      "Condition": {
        "Bool": {
          "aws:MultiFactorAuthPresent": "true"
        }
      }
    }
  ]
}
☸️ Task 2: Kubernetes Policy-as-Code with OPA

This task focuses on implementing security controls using OPA Gatekeeper.

🔧 Installing Gatekeeper

Apply the Gatekeeper manifests:

kubectl apply -f https://raw.githubusercontent.com/open-policy-agent/gatekeeper/release-3.14/deploy/gatekeeper.yaml

Verify installation:

kubectl get pods -n gatekeeper-system
📜 Constraint Templates

The lab includes custom Rego policies to restrict the use of insecure or default ServiceAccounts.

Example Policy Goals
Prevent pods from using the default ServiceAccount
Enforce approved ServiceAccounts only
Apply namespace-level IAM restrictions
🛡️ Enforcement Example

Apply the constraint template:

kubectl apply -f serviceaccount-constraint-template.yaml

Apply the constraint:

kubectl apply -f serviceaccount-constraint.yaml
🧪 Testing the Policy

Deploy a test pod using the default ServiceAccount:

kubectl apply -f pod-test.yaml

Expected Result:

Error from server ([denied by serviceaccount-policy] unauthorized service account): admission webhook denied the request
🛠️ Usage Guide
1️⃣ AWS IAM Testing

Use the provided IAM policy files:

trust-policy.json
permissions-policy.json

Test role assumptions:

aws sts assume-role \
  --role-arn arn:aws:iam::ACCOUNT_ID:role/TestRole \
  --role-session-name security-test
2️⃣ Kubernetes OPA Policy Testing

Apply all Kubernetes manifests:

kubectl apply -f kubernetes/

Verify constraints:

kubectl get constrainttemplates
kubectl get constraints
📋 Prerequisites

Before starting this lab, ensure you have:

Basic Linux command-line knowledge
Familiarity with AWS IAM policies
Understanding of Kubernetes YAML
Access to an AWS account
kubectl configured properly
🔒 Security Best Practices

This project emphasizes:

Principle of Least Privilege (PoLP)
Zero Trust IAM configuration
Admission Controller security
Infrastructure-as-Code security validation
Continuous policy enforcement
📖 Key Technologies Used
Technology	Purpose
AWS IAM	Identity & Access Management
STS	Temporary credential management
Kubernetes	Container orchestration
OPA Gatekeeper	Policy enforcement
Rego	Policy language
kubectl	Kubernetes CLI
🎓 Learning Outcomes

After completing this lab, you will be able to:

✅ Detect insecure IAM trust relationships
✅ Secure AWS role assumptions
✅ Implement Kubernetes admission control policies
✅ Write custom OPA/Rego security policies
✅ Enforce least privilege in cloud-native environments
✅ Integrate IAM security into DevSecOps workflows

⚠️ Disclaimer

This lab is intended strictly for educational and ethical security training purposes.

Do not attempt these techniques on systems you do not own or have explicit permission to test.

Always follow organizational security policies and the principle of least privilege in production environments.

👨‍💻 Author

DevSecOps Security Lab Series
Focused on practical cloud security, Kubernetes hardening, and secure CI/CD practices.

📜 License
