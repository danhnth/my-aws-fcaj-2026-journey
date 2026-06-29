---
title : "Step 3: Test & Validation"
date : 2026-06-26
weight : 6
chapter : false
pre : " <b> 5.6. </b> "
---

#### Step 3: Test & Validation

After deploying the insecure baseline, wait approximately **30-60 minutes** for Security Hub and GuardDuty to complete their initial scan cycles.

**1. Check Security Hub Findings**

1. Navigate to **Security Hub** console → **Findings**.
2. You should see findings flagged in relation to the misconfigurations we created:

   | Finding ID | Description |
   |------------|-------------|
   | **S3.2** | S3 buckets should have public access blocked |
   | **IAM.1** | IAM policies should not have full administrative privileges |
   | **EC2.19** | Security groups should not allow unrestricted SSH access |

3. Navigate to **Security Hub** → **Summary** to view the overall **Compliance score**. Take a screenshot of the low score for your report.

{{%expand "AWS CLI Alternative" %}}
```bash
# List all Security Hub findings
aws securityhub get-findings --region ap-southeast-1

# Filter findings for specific controls
aws securityhub get-findings \
    --filters '{"ComplianceSecurityControlId":[{"Value":"S3.2","Comparison":"EQUALS"}]}' \
    --region ap-southeast-1
aws securityhub get-findings \
    --filters '{"ComplianceSecurityControlId":[{"Value":"IAM.1","Comparison":"EQUALS"}]}' \
    --region ap-southeast-1
aws securityhub get-findings \
    --filters '{"ComplianceSecurityControlId":[{"Value":"EC2.19","Comparison":"EQUALS"}]}' \
    --region ap-southeast-1

# Count failed findings
aws securityhub get-findings \
    --filters '{"ComplianceStatus":[{"Value":"FAILED","Comparison":"EQUALS"}]}' \
    --query 'length(Findings)' \
    --region ap-southeast-1
```
{{%/expand%}}

**2. Check GuardDuty Findings**

To simulate an actual attack and trigger GuardDuty alerts:

1. **Simulate SSH brute force**: From your local machine, attempt to SSH into the EC2 instance (the attempt will fail without a key, but GuardDuty will log it):

   ```bash
   ssh ec2-user@<EC2-PUBLIC-IP>
   ```

2. **Simulate suspicious IAM activity**: Using the `developer-test` credentials (generate access keys from the IAM console), run an unusual API call:

   ```bash
   aws configure --profile dev-test
   # Enter the access key and secret key for developer-test
   aws ec2 describe-instances --profile dev-test
   aws ec2 create-snapshot --profile dev-test --volume-id <any-volume-id>
   ```

3. Return to **GuardDuty** console → **Findings** after 15-30 minutes. You should see alerts such as:
   - `UnauthorizedAccess:EC2/SSHBruteForce`
   - `Behavior:IAMUser/ResourceConsumption`

4. Take screenshots of these findings for your workshop report documentation.

{{%expand "AWS CLI Alternative" %}}
```bash
# List GuardDuty detectors and get the detector ID
aws guardduty list-detectors --region ap-southeast-1

# List all findings (replace <detector-id> with the ID from above)
aws guardduty list-findings --detector-id <detector-id> --region ap-southeast-1

# Get details of specific findings
aws guardduty get-findings --detector-id <detector-id> \
    --finding-ids $(aws guardduty list-findings --detector-id <detector-id> --query FindingIds --output text) \
    --region ap-southeast-1
```
{{%/expand%}}
