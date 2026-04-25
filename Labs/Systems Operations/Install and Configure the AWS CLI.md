#  AWS CLI Lab – IAM Policy Retrieval

## Overview

This lab demonstrates how to use the **AWS CLI** to retrieve a customer-managed IAM policy (`lab_policy`) in JSON format — without using the AWS Management Console.

The objective is to build hands-on experience with AWS CLI commands related to IAM and understand how policies are structured and accessed programmatically.

---

## Objectives

* Configure and use the AWS CLI
* Identify customer-managed IAM policies
* Retrieve policy metadata and versions
* Extract and save a policy document in JSON format

---

## Tools & Technologies

* AWS CLI
* IAM (Identity and Access Management)
* JSON
* Terminal / Command Line

---

## Steps Performed

### 1. List Customer-Managed Policies

Used the AWS CLI to list locally created IAM policies:

```bash
aws iam list-policies --scope Local
```

---

### 2. Identify the Target Policy

Located the `lab_policy` and copied its **ARN** (Amazon Resource Name).

---

### 3. Retrieve Policy Metadata

Fetched details of the policy to identify the default version:

```bash
aws iam get-policy --policy-arn <"arn:aws:iam::191686983678:policy/lab_policy">
```

<img width="806" height="600" alt="Lab 168 Install and Configure the AWS CLI 1" src="https://github.com/user-attachments/assets/cad1e61b-8b7d-4611-a536-43dfca6c7e21" />

---

### 4. Get the Policy Version

Used the version ID to retrieve the actual JSON policy document:

```bash
aws iam get-policy-version \
  --policy-arn <POLICY_ARN> \
  --version-id <VERSION_ID>
```

---

### 5. Export the Policy to a File

Saved the policy document locally:

```bash
aws iam get-policy-version \
  --policy-arn <POLICY_ARN> \
  --version-id <VERSION_ID> \
  --query 'PolicyVersion.Document' \
  --output json > lab_policy.json
```

---

## 📄 Output

The result is a JSON file:

```
lab_policy.json
```

This file contains the full IAM policy document, including permissions, actions, and resource definitions.


<img width="806" height="600" alt="Lab 168 Instal and Configure the CLI" src="https://github.com/user-attachments/assets/4f0c6c6f-bd04-4934-80c0-53c738743a34" />

---

## Key Learnings

* How to work with IAM policies via AWS CLI
* Understanding policy versions and structure
* Filtering CLI output using `--query`
* Redirecting output to files using `>`

---

## Why This Matters

Working with AWS CLI is essential for:

* Automation and scripting
* Infrastructure as Code (IaC)
* Efficient cloud resource management without relying on the UI

---

## Notes

* The lab uses **pre-configured credentials** (`awsstudent`)
* No manual key creation is required
* All actions are performed via CLI for learning purposes

---

## Author

Myrna Garza

---
