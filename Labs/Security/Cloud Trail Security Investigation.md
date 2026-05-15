# AWS Lab 187 - CloudTrail Security Investigation

## Overview

In this lab, I worked with AWS monitoring and security services to investigate suspicious activity affecting a web server environment.

The objective was to analyze CloudTrail logs, identify unauthorized actions, trace the responsible identity, and understand how the infrastructure was exposed.

This was one of my favorite AWS labs because it simulated a real-world cloud security investigation workflow.

---

## AWS Services Used

- Amazon CloudTrail
- Amazon Athena
- AWS Glue
- Amazon S3
- Amazon EC2
- AWS IAM
- AWS KMS

---

## Lab Architecture

1. CloudTrail generated API activity logs
2. Logs were stored in Amazon S3
3. AWS Glue cataloged the CloudTrail data
4. Amazon Athena queried and analyzed the logs
5. Security events were investigated to identify suspicious activity


---

## Key Investigation Tasks

### 1. Access CloudTrail Logs

Connected to the EC2 web server via SSH and extracted CloudTrail log files stored in Amazon S3.

### 2. Configure Athena

Created and explored the CloudTrail table

<img width="891" height="347" alt="Lab 187 Cloud Trail" src="https://github.com/user-attachments/assets/f6ee17b3-eeda-435f-b0ad-542fc3365c90" />

Configured query result locations in S3

Queried logs using SQL


### 3. Identify Suspicious Activity

The investigation revealed a suspicious user

<img width="852" height="523" alt="Lab 187 Security Groups opened" src="https://github.com/user-attachments/assets/27fea6e2-2e7f-4879-ba01-1b85da9bbc0f" />

Suspicious API action identified:

<img width="968" height="652" alt="Lab 187 Identify the Hacker username" src="https://github.com/user-attachments/assets/1c8e1871-62c9-496e-a10d-6cf9243f8ed9" />

<img width="670" height="843" alt="187 Update SSH Security" src="https://github.com/user-attachments/assets/7e7138d5-4c66-47f4-adb5-0417df84e839" />


### Key Security Findings
Security groups can become attack vectors if improperly configured
CloudTrail provides critical forensic visibility
Athena is extremely powerful for log investigation
Monitoring and auditing are essential in cloud security

<img width="1029" height="682" alt="187 Delete the Chaos Hacker" src="https://github.com/user-attachments/assets/34ce1cbd-fb3d-432e-a130-4082a05b90d9" />


### Skills Practiced

Cloud security investigation
AWS monitoring
SQL querying with Athena
Log analysis
Security incident tracing
IAM and EC2 analysis

### Outcome

Successfully traced suspicious activity to a specific identity and identified the API action responsible for exposing the web server.

This lab provided hands-on experience with AWS cloud security operations and incident investigation workflows.
Working with CloudTrail forensic data


