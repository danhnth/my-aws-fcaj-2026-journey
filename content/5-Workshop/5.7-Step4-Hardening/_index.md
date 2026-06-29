---
title : "Step 4: Hardening & Remediation"
date : 2026-06-26
weight : 7
chapter : false
pre : " <b> 5.7. </b> "
---

#### Step 4: Hardening & Remediation

Now, acting as a Cloud Security Engineer, we will fix each vulnerability based on the recommendations from Security Hub.

**1. Fix S3 — Block Public Access**

1. Navigate to **S3** console.
2. Select the bucket `vulnerable-public-data-<your-name>`.
3. Go to **Permissions** tab → **Block Public Access**.
4. Click **Edit** → Check **Block all public access**.
5. Click **Save changes**.

{{%expand "AWS CLI Alternative" %}}
```bash
# Block all public access on the bucket
aws s3api put-public-access-block --bucket vulnerable-public-data-<your-name> \
    --public-access-block-configuration "BlockPublicAcls=true,IgnorePublicAcls=true,BlockPublicPolicy=true,RestrictPublicBuckets=true"

# Reset ACL to private
aws s3api put-bucket-acl --bucket vulnerable-public-data-<your-name> --acl private
```
{{%/expand%}}

**2. Fix IAM — Apply Least Privilege**

1. Navigate to **IAM** console → **Users** → `developer-test`.
2. Go to the **Permissions** tab.
3. Locate the inline policy `WildcardFullAccess` → Click **Remove** (or **Delete**).
4. Click **Add permissions** → **Attach policies directly**.
5. Search for and select **AmazonS3ReadOnlyAccess** (a scoped, least-privilege policy).
6. Click **Next** → **Add permissions**.
7. (Optional but recommended) Go to **Security credentials** tab → Under **Multi-factor authentication (MFA)** → **Assign MFA device** to enable MFA for this user.

{{%expand "AWS CLI Alternative" %}}
```bash
# 1. Detach the wildcard policy (find the policy ARN first)
aws iam list-attached-user-policies --user-name developer-test

aws iam detach-user-policy --user-name developer-test \
    --policy-arn arn:aws:iam::$(aws sts get-caller-identity --query Account --output text):policy/WildcardFullAccess

# 2. Attach a least-privilege policy (S3 ReadOnly)
aws iam attach-user-policy --user-name developer-test \
    --policy-arn arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess

# 3. (Optional) List attached policies to verify
aws iam list-attached-user-policies --user-name developer-test
```
{{%/expand%}}

**3. Fix EC2 — Restrict SSH Access**

1. Navigate to **EC2** console → **Security Groups**.
2. Select `insecure-sg`.
3. Go to **Inbound rules** tab → Click **Edit inbound rules**.
4. Find the SSH rule with Source `0.0.0.0/0`.
5. Change **Source** to **My IP** (this will auto-populate your current public IP address).
6. Click **Save rules**.

   > This restricts SSH access to only your IP address, eliminating the global exposure.

{{%expand "AWS CLI Alternative" %}}
```bash
# 1. Revoke the global SSH rule
aws ec2 revoke-security-group-ingress --group-name insecure-sg \
    --protocol tcp --port 22 --cidr 0.0.0.0/0 \
    --region ap-southeast-1

# 2. Add SSH access restricted to your public IP only
aws ec2 authorize-security-group-ingress --group-name insecure-sg \
    --protocol tcp --port 22 --cidr $(curl -s http://checkip.amazonaws.com/)/32 \
    --region ap-southeast-1

# 3. Verify the updated rules
aws ec2 describe-security-groups --group-names insecure-sg --region ap-southeast-1
```
{{%/expand%}}
