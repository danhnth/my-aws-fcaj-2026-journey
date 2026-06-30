---
title : "Step 6: Clean-up"
date : 2026-06-29
weight : 9
chapter : false
pre : " <b> 5.9. </b> "
---

#### Step 6: Clean-up

This step is mandatory to avoid unexpected charges. Remove all lab resources:

1. **Delete IAM user**: Navigate to **IAM** → **Users** → Select `developer-test` → **Delete**.

2. **Terminate EC2 instance**: Navigate to **EC2** → **Instances** → Select `vulnerable-ec2` → **Instance state** → **Terminate**.

3. **Delete security group**: Navigate to **EC2** → **Security Groups** → Select `insecure-sg` → **Actions** → **Delete security groups**.

4. **Delete S3 bucket**: Navigate to **S3** → Select `vulnerable-public-data-<your-name>` → **Empty** (confirm) → **Delete**.

5. **Disable GuardDuty**: Navigate to **GuardDuty** → **Settings** → **Disable GuardDuty**.

6. **Disable Security Hub**: Navigate to **Security Hub** → **Settings** → **General** → **Disable Security Hub**.

7. **Delete CloudTrail trail**: Navigate to **CloudTrail** → **Trails** → Select `FCAJ-Central-Trail` → **Delete**.

8. **Delete CloudTrail S3 bucket**: Navigate to **S3** → Select the logging bucket (`fcaj-security-logs-<random-id>`) → **Empty** → **Delete**.

{{%expand "AWS CLI Alternative" %}}
```bash
# === IAM Cleanup ===
# List and delete access keys for developer-test
aws iam list-access-keys --user-name developer-test
aws iam delete-access-key --user-name developer-test --access-key-id <access-key-id>

# Detach policies
aws iam detach-user-policy --user-name developer-test \
    --policy-arn arn:aws:iam::$(aws sts get-caller-identity --query Account --output text):policy/WildcardFullAccess
aws iam detach-user-policy --user-name developer-test \
    --policy-arn arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess

# Delete the IAM user
aws iam delete-user --user-name developer-test

# Delete the custom policy
aws iam delete-policy \
    --policy-arn arn:aws:iam::$(aws sts get-caller-identity --query Account --output text):policy/WildcardFullAccess

# === EC2 Cleanup ===
# Find instances using insecure-sg
aws ec2 describe-instances --filters "Name=instance.group-name,Values=insecure-sg" \
    --query 'Reservations[].Instances[].InstanceId' --region ap-southeast-1

# Terminate those instances
aws ec2 terminate-instances --instance-ids <instance-id> --region ap-southeast-1

# Delete the security group
aws ec2 delete-security-group --group-name insecure-sg --region ap-southeast-1

# === S3 Cleanup ===
# Empty and delete the vulnerable bucket
aws s3 rm s3://vulnerable-public-data-<your-name> --recursive
aws s3 rb s3://vulnerable-public-data-<your-name>

# === GuardDuty Cleanup ===
# Find and disable the detector
aws guardduty list-detectors --region ap-southeast-1
aws guardduty delete-detector --detector-id <detector-id> --region ap-southeast-1

# === Security Hub Cleanup ===
aws securityhub disable-security-hub --region ap-southeast-1

# === CloudTrail Cleanup ===
aws cloudtrail delete-trail --name FCAJ-Central-Trail

# Empty and delete the CloudTrail log bucket
aws s3 rm s3://fcaj-security-logs-<random-id> --recursive
aws s3 rb s3://fcaj-security-logs-<random-id>
```
{{%/expand%}}
