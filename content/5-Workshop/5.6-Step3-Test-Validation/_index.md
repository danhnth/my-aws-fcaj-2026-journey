---
title : "Step 3: Test & Validation"
date : 2024-01-01 
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
