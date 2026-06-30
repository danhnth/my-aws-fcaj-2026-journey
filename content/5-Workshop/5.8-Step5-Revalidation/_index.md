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

   Security Hub runs compliance scans periodically. Wait approximately **30-60 minutes** for the next scan to complete after making your changes. You can also manually refresh the findings page.

2. **Review Security Hub findings**

   Navigate to **Security Hub** → **Findings** and check the status of previously flagged controls:

   | Control ID | Before (Pre-Hardening) | After (Post-Hardening) |
   |------------|----------------------|----------------------|
   | S3.2 (S3 public access blocked) | **Failed** | **Passed** ✅ |
   | IAM.1 (No full admin policy) | **Failed** | **Passed** ✅ |
   | EC2.19 (SSH restricted) | **Failed** | **Passed** ✅ |

3. **Compare the compliance score**

   - Go to **Security Hub** → **Summary**.
   - Compare the current **Compliance score** with the screenshot you took in Step 3.
   - The score should have noticeably increased after hardening.
   - Take a new screenshot showing the improved score.

4. **Verify GuardDuty alerts**

   GuardDuty alerts from the earlier attack simulation will remain; but no new critical alerts should be generated from the now-hardened infrastructure.

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

# 4. Compute compliance score: PASSED / (PASSED + FAILED)
aws securityhub get-findings \
    --filters '{"ComplianceStatus":[{"Value":"PASSED","Comparison":"EQUALS"}]}' \
    --query 'length(Findings)' \
    --region ap-southeast-1

aws securityhub get-findings \
    --filters '{"ComplianceStatus":[{"Value":"FAILED","Comparison":"EQUALS"}]}' \
    --query 'length(Findings)' \
    --region ap-southeast-1
```
{{%/expand%}}
