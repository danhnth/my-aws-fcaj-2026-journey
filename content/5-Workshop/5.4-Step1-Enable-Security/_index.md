---
title : "Step 1: Enable Security Services"
date : 2024-01-01 
weight : 4
chapter : false
pre : " <b> 5.4. </b> "
---

#### Step 1: Enable Security Services

Before deploying the vulnerable infrastructure, we must first enable the AWS security monitoring services so they can capture all findings from the start.

**1. AWS CloudTrail**

CloudTrail records all API activity in your AWS account, providing an audit trail for later analysis.

1. Navigate to **CloudTrail** console → Click **Create trail**.
2. Configure:
   - **Trail name**: `FCAJ-Central-Trail`
   - **Storage location**: Create a new S3 bucket (e.g., `fcaj-security-logs-<random-id>`)
   - Keep the remaining defaults.
3. Click **Create trail**.

**2. Amazon GuardDuty**

GuardDuty uses machine learning and threat intelligence to detect suspicious behavior.

1. Navigate to **GuardDuty** console → Click **Get Started**.
2. Click **Enable GuardDuty** (no additional configuration required initially).
3. GuardDuty will begin analyzing logs within minutes.

**3. AWS Security Hub**

Security Hub provides a centralized view of security findings and compliance scores.

1. Navigate to **Security Hub** console → Click **Go to Security Hub**.
2. Under **Security standards**, check **CIS AWS Foundations Benchmark v1.4.0**.
3. Click **Enable Security Hub**.
4. Allow 15-30 minutes for the initial compliance scan to complete.
