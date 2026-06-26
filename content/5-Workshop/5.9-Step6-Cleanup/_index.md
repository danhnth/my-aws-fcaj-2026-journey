---
title : "Step 6: Clean-up"
date : 2024-01-01 
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
