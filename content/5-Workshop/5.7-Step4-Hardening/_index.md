---
title : "Step 4: Hardening & Remediation"
date : 2024-01-01 
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

**2. Fix IAM — Apply Least Privilege**

1. Navigate to **IAM** console → **Users** → `developer-test`.
2. Go to the **Permissions** tab.
3. Locate the inline policy `WildcardFullAccess` → Click **Remove** (or **Delete**).
4. Click **Add permissions** → **Attach policies directly**.
5. Search for and select **AmazonS3ReadOnlyAccess** (a scoped, least-privilege policy).
6. Click **Next** → **Add permissions**.
7. (Optional but recommended) Go to **Security credentials** tab → Under **Multi-factor authentication (MFA)** → **Assign MFA device** to enable MFA for this user.

**3. Fix EC2 — Restrict SSH Access**

1. Navigate to **EC2** console → **Security Groups**.
2. Select `insecure-sg`.
3. Go to **Inbound rules** tab → Click **Edit inbound rules**.
4. Find the SSH rule with Source `0.0.0.0/0`.
5. Change **Source** to **My IP** (this will auto-populate your current public IP address).
6. Click **Save rules**.

   > This restricts SSH access to only your IP address, eliminating the global exposure.
