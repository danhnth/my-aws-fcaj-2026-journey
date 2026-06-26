---
title : "Step 2: Deploy Insecure Baseline"
date : 2024-01-01 
weight : 5
chapter : false
pre : " <b> 5.5. </b> "
---

#### Step 2: Deploy Insecure Baseline

We will intentionally create three classic cloud misconfigurations so that Security Hub and GuardDuty can detect them.

**1. S3 Vulnerability — Public Bucket**

1. Navigate to **S3** console → Click **Create bucket**.
2. Configure:
   - **Bucket name**: `vulnerable-public-data-<your-name>`
   - **Region**: `ap-southeast-1` (Singapore)
3. Under **Block Public Access settings for this bucket**, **uncheck** *Block all public access*.
4. Acknowledge the warning that the bucket will become public.
5. Click **Create bucket**.

**2. IAM Vulnerability — Over-privileged Wildcard Policy**

1. Navigate to **IAM** console → **Users** → **Create user**.
2. **User name**: `developer-test`
3. Uncheck "Provide user access to the AWS Management Console" (we only need programmatic access).
4. Click **Next**.
5. Select **Attach policies directly** → Click **Create policy**.
6. Switch to the **JSON** tab and paste the following overly-permissive policy:

   ```json
   {
       "Version": "2012-10-17",
       "Statement": [
           {
               "Effect": "Allow",
               "Action": "*",
               "Resource": "*"
           }
       ]
   }
   ```

   > **Note:** This policy grants full administrative access (`*` over `*`), which severely violates the Principle of Least Privilege.

7. Name the policy `WildcardFullAccess` → Click **Create policy**.
8. Go back, select the newly created `WildcardFullAccess` policy → Click **Next**.
9. Review and click **Create user**.

**3. EC2 Vulnerability — Open SSH to the World**

1. First, create a security group:
   - Navigate to **EC2** console → **Security Groups** → **Create security group**.
   - **Name**: `insecure-sg`
   - **Description**: Security group with global SSH access
   - **Inbound rules**: Add rule → Type: **SSH (Port 22)**, Source: `0.0.0.0/0`
   - Click **Create security group**.

2. (Optional) Launch a test EC2 instance using this security group to generate additional findings:
   - Go to **EC2** → **Instances** → **Launch instance**.
   - **Name**: `vulnerable-ec2`
   - **AMI**: Amazon Linux 2023 (free tier eligible)
   - **Instance type**: `t2.micro`
   - **Key pair**: Proceed without a key pair (or create one if you want SSH access)
   - **Network settings**: Select **Edit** → Choose **Select existing security group** → Pick `insecure-sg`.
   - Click **Launch instance**.
