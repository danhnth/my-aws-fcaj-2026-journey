---
title : "Step 5: Re-validation"
date : 2026-06-29
weight : 8
chapter : false
pre : " <b> 5.8. </b> "
---

#### Step 5: Re-validation

After completing the hardening steps, we need to verify that our remediation actions were effective.

1. **Wait for a new scan cycle**

   Security Hub runs compliance scans periodically. Wait approximately **30-60 minutes** for the next scan to complete after making your changes.

2. **Review Security Hub findings**

   Navigate to **Security Hub** → **CSPM** → **Findings** and check the status of previously flagged controls:

   | Control ID | Before (Pre-Hardening) | After (Post-Hardening) |
   |------------|----------------------|----------------------|
   | S3.2 (S3 public access blocked) | **Failed** | **Passed** X |
   | IAM.1 (No full admin policy) | **Failed** | **Passed** X |
   | EC2.19 (SSH restricted) | **Failed** | **Passed** X |

   ![S3 Block Public Access Control Passed](Screenshots/s3-block-public-access-resolved.png)

   > **Note:** Individual findings in **CSPM → Findings** update quickly after remediation. However, the overall security score and aggregated control statuses shown in **Security Hub → Summary** are recalculated only once every **24 hours**. If the score hasn't updated yet, check back the next day.

3. **Compare the compliance score**

   - Go to **Security Hub** → **CSPM** → **Controls** to see the security score.
   - Compare the current **Security score** with the screenshot you took in Step 3.
   - The score should have noticeably increased after hardening.
   - Take a new screenshot showing the improved score.

4. **Verify GuardDuty alerts**

   GuardDuty alerts from the earlier attack simulation will remain; but no new critical alerts should be generated from the now-hardened infrastructure.

5. ***(Optional)*** **Remediate additional S3 controls**

   If you want to go further, here are two common S3 security controls you can remediate to improve your compliance score further.

   **a. S3 general purpose buckets should require requests to use SSL**

   This control checks whether S3 buckets have a bucket policy that enforces `aws:SecureTransport`. Apply the following policy to your bucket to block non-SSL requests:

   ```bash
   aws s3api put-bucket-policy --bucket <your-bucket-name> --policy '{
     "Version": "2012-10-17",
     "Statement": [{
       "Sid": "DenyInsecureConnections",
       "Effect": "Deny",
       "Principal": "*",
       "Action": "s3:*",
       "Resource": "arn:aws:s3:::<your-bucket-name>/*",
       "Condition": {
         "Bool": {"aws:SecureTransport": "false"}
       }
     }]
   }'
   ```

   After applying, verify the control passes on the next scan cycle and take a screenshot of the passed status.

   **b. S3 general purpose buckets should have MFA delete enabled**

   MFA Delete adds an extra layer of protection by requiring multi-factor authentication for permanent delete operations.

   > **Note:** MFA Delete can only be enabled by the AWS account **root user** and requires a configured MFA device.

   ```bash
   aws s3api put-bucket-versioning \
       --bucket <your-bucket-name> \
       --versioning-configuration Status=Enabled,MFADelete=Enabled \
       --mfa "arn:aws:iam::<account-id>:mfa/root-account-mfa-device <mfa-code>"
   ```

   > **Note:** This is a sensitive operation. Once enabled, all delete operations require MFA authentication. Use with caution in production environments.

   After completing these optional remediations, wait for the next Security Hub scan (30-60 minutes) to verify the **Passed** status for each control.

![Security Score after Hardening](Screenshots/security-score-after-hardening.png)<br>
*CSPM score in Security Hub after hardening, with nearly all findings remediated and controls achieving a Passed status*

{{%expand "AWS CLI Alternative" %}}
```bash
# 1. Check S3.2 control status (should now be PASSED)
aws securityhub get-findings \
    --filters '{"ComplianceSecurityControlId":[{"Value":"S3.2","Comparison":"EQUALS"}]}' \
    --query 'Findings[].Compliance.Status' \
    --region ap-southeast-1

# 2. Check IAM.1 control status
aws securityhub get-findings \
    --filters '{"ComplianceSecurityControlId":[{"Value":"IAM.1","Comparison":"EQUALS"}]}' \
    --query 'Findings[].Compliance.Status' \
    --region ap-southeast-1

# 3. Check EC2.19 control status
aws securityhub get-findings \
    --filters '{"ComplianceSecurityControlId":[{"Value":"EC2.19","Comparison":"EQUALS"}]}' \
    --query 'Findings[].Compliance.Status' \
    --region ap-southeast-1

```
{{%/expand%}}
