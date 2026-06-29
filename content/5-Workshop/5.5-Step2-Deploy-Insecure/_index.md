---
title : "Step 2: Deploy Insecure Baseline"
date : 2026-06-26
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

{{%expand "AWS CLI Alternative" %}}
```bash
# 1. Create the bucket (public access is blocked by default)
aws s3 mb s3://vulnerable-public-data-<your-name> --region ap-southeast-1

# 2. Remove the public access block to make it public
aws s3api put-public-access-block --bucket vulnerable-public-data-<your-name> \
    --public-access-block-configuration "BlockPublicAcls=false,IgnorePublicAcls=false,BlockPublicPolicy=false,RestrictPublicBuckets=false"

# 3. Apply a public-read ACL
aws s3api put-bucket-acl --bucket vulnerable-public-data-<your-name> --acl public-read
```
{{%/expand%}}

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

{{%expand "AWS CLI Alternative" %}}
```bash
# 1. Create the wildcard IAM policy
aws iam create-policy --policy-name WildcardFullAccess --policy-document '{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "*",
      "Resource": "*"
    }
  ]
}'

# 2. Create IAM user (programmatic access only)
aws iam create-user --user-name developer-test

# 3. Attach the wildcard policy to the user
aws iam attach-user-policy --user-name developer-test --policy-arn arn:aws:iam::$(aws sts get-caller-identity --query Account --output text):policy/WildcardFullAccess

# 4. Generate access keys for the user
aws iam create-access-key --user-name developer-test
```
> **Note:** Save the `AccessKeyId` and `SecretAccessKey` from the output — they are needed for Step 3.

{{%/expand%}}

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

{{%expand "AWS CLI Alternative" %}}
```bash
# 1. Create the security group
aws ec2 create-security-group --group-name insecure-sg \
    --description "Security group with global SSH access" \
    --region ap-southeast-1

# 2. Add inbound SSH rule allowing access from anywhere
aws ec2 authorize-security-group-ingress --group-name insecure-sg \
    --protocol tcp --port 22 --cidr 0.0.0.0/0 \
    --region ap-southeast-1

# 3. (Optional) Launch a test EC2 instance
aws ec2 run-instances \
    --image-id resolve-ssm:/aws/service/ami-amazon-linux-latest/al2023-ami-kernel-default-x86_64 \
    --instance-type t2.micro \
    --security-groups insecure-sg \
    --region ap-southeast-1
```
> **Note:** The `resolve-ssm` parameter fetches the latest Amazon Linux 2023 AMI ID automatically. If `resolve-ssm` is unsupported, use `aws ssm get-parameters --names /aws/service/ami-amazon-linux-latest/al2023-ami-kernel-default-x86_64` to get the AMI ID first.

{{%/expand%}}
