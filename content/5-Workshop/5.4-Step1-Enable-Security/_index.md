---
title : "Step 1: Enable Security Services"
date : 2026-06-29
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

{{%expand "AWS CLI Alternative" %}}
```bash
# 1. Create S3 bucket for CloudTrail logs
aws s3 mb s3://fcaj-security-logs-<random-id> --region ap-southeast-1

# 2. Create trail with log file validation
aws cloudtrail create-trail --name FCAJ-Central-Trail --s3-bucket-name fcaj-security-logs-<random-id> --is-multi-region-trail --enable-log-file-validation

# 3. Start logging
aws cloudtrail start-logging --name FCAJ-Central-Trail
```
{{%/expand%}}

**2. Amazon GuardDuty**

GuardDuty uses machine learning and threat intelligence to detect suspicious behavior.

1. Navigate to **GuardDuty** console → Click **Get Started**.
2. Click **Enable GuardDuty** (no additional configuration required initially).
3. GuardDuty will begin analyzing logs within minutes.

{{%expand "AWS CLI Alternative" %}}
```bash
# Enable GuardDuty (creates a detector)
aws guardduty create-detector --enable --region ap-southeast-1

# Verify it's active
aws guardduty list-detectors --region ap-southeast-1
```
{{%/expand%}}

**3. AWS Security Hub**

Security Hub provides a centralized view of security findings and compliance scores.

1. Navigate to **Security Hub** console → Click **Go to Security Hub**.
2. Under **Security standards**, check **CIS AWS Foundations Benchmark v1.4.0**.
3. Click **Enable Security Hub**.
4. Allow 15-30 minutes for the initial compliance scan to complete.

{{%expand "AWS CLI Alternative" %}}
```bash
# Enable Security Hub with default standards (includes CIS Benchmark v1.4.0)
aws securityhub enable-security-hub --enable-default-standards --region ap-southeast-1

# Wait 15-30 seconds, then verify which standards are enabled
aws securityhub get-enabled-standards --region ap-southeast-1
```
{{%/expand%}}
