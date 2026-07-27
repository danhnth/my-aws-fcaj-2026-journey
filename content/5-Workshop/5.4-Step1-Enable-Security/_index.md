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

1. Navigate to **Security Hub** console → Click **Get started**.
2. In **Security capabilities**, choose **Enable all capabilities** (or **Customize capabilities** to pick specific ones).
3. In **Regions**, choose **Enable all Regions** (or **Enable specific Regions**).
4. (Optional) Add **Resource tags** as needed.
5. Click **Enable Security Hub**.

{{%expand "AWS CLI Alternative" %}}
```bash
# Enable Security Hub with default standards (includes CIS Benchmark v1.4.0)
aws securityhub enable-security-hub --enable-default-standards --region ap-southeast-1

# Wait 15-30 seconds, then verify which standards are enabled
aws securityhub get-enabled-standards --region ap-southeast-1
```
{{%/expand%}}

**4. Enable Security Standards (Security Hub CSPM)**

After Security Hub is enabled, you must activate the specific security standard used in this workshop.

1. Navigate to **Security Hub CSPM** (or from the left navigation choose **Security standards**).
2. Find **CIS AWS Foundations Benchmark v1.4.0**.
3. Click **Enable standard**.
4. The standard activates immediately, but the **security score** is calculated once every 24 hours. Until the first score is computed, you will see *"Unable to display security score: The score is still being generated."*
5. The score formula is: **Passed / (Passed + Failed)**, excluding controls with **No data**.

**5. AWS Config**

Security Hub subscription shows `READY` as soon as you enable a standard, but the actual compliance evaluation depends on **AWS Config** to continuously record your resource states. Without AWS Config enabled, most CIS benchmark controls will show `NO_DATA` or `NOT_RECORDED`.

1. Navigate to **AWS Config** console → Click **Get started**.
2. Under **Recording options**, choose **Record all resources** and enable **Include global resources** (e.g., IAM).
3. Under **Delivery method**, create a new S3 bucket or select an existing one.
4. Click **Set up**.
5. Once Config starts recording, Security Hub will automatically evaluate the CIS benchmark rules and generate findings. The security score updates once every 24 hours.

{{%expand "AWS CLI Alternative" %}}
```bash
# 1. Create S3 bucket for Config logs (name must be globally unique)
aws s3api create-bucket \
  --bucket config-bucket-<account-id>-ap-southeast-1 \
  --region ap-southeast-1 \
  --create-bucket-configuration LocationConstraint=ap-southeast-1

# 2. Create a delivery channel pointing to the bucket
aws configservice put-delivery-channel \
  --delivery-channel name=default,s3BucketName=config-bucket-<account-id>-ap-southeast-1 \
  --region ap-southeast-1

# 3. Create a configuration recorder (uses the AWS-managed Config role)
aws configservice put-configuration-recorder \
  --configuration-recorder name=default,roleARN=arn:aws:iam::<account-id>:role/aws-service-role/config.amazonaws.com/AWSServiceRoleForConfig \
  --recording-group allSupported=true,includeGlobalResourceTypes=true \
  --region ap-southeast-1

# 4. Start recording
aws configservice start-configuration-recorder \
  --configuration-recorder-name default \
  --region ap-southeast-1
```
{{%/expand%}}
