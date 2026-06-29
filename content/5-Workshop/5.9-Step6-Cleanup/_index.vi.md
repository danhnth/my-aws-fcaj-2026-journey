---
title : "Bước 6: Dọn dẹp tài nguyên"
date : 2026-06-26
weight : 9
chapter : false
pre : " <b> 5.9. </b> "
---

#### Bước 6: Dọn dẹp tài nguyên

Bước bắt buộc để tránh phát sinh chi phí ngoài ý muốn. Xóa tất cả tài nguyên trong lab:

1. **Xóa IAM user**: Vào **IAM** → **Users** → Chọn `developer-test` → **Delete**.

2. **Terminate EC2 instance**: Vào **EC2** → **Instances** → Chọn `vulnerable-ec2` → **Instance state** → **Terminate**.

3. **Xóa security group**: Vào **EC2** → **Security Groups** → Chọn `insecure-sg` → **Actions** → **Delete security groups**.

4. **Xóa S3 bucket**: Vào **S3** → Chọn `vulnerable-public-data-<tên-bạn>` → **Empty** (xác nhận) → **Delete**.

5. **Tắt GuardDuty**: Vào **GuardDuty** → **Settings** → **Disable GuardDuty**.

6. **Tắt Security Hub**: Vào **Security Hub** → **Settings** → **General** → **Disable Security Hub**.

7. **Xóa CloudTrail trail**: Vào **CloudTrail** → **Trails** → Chọn `FCAJ-Central-Trail` → **Delete**.

8. **Xóa S3 bucket của CloudTrail**: Vào **S3** → Chọn bucket log (`fcaj-security-logs-<random-id>`) → **Empty** → **Delete**.

{{%expand "AWS CLI — Phương thức Dòng lệnh" %}}
```bash
# === Dọn IAM ===
# Liệt kê và xóa access keys của developer-test
aws iam list-access-keys --user-name developer-test
aws iam delete-access-key --user-name developer-test --access-key-id <access-key-id>

# Gỡ bỏ policies
aws iam detach-user-policy --user-name developer-test \
    --policy-arn arn:aws:iam::$(aws sts get-caller-identity --query Account --output text):policy/WildcardFullAccess
aws iam detach-user-policy --user-name developer-test \
    --policy-arn arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess

# Xóa IAM user
aws iam delete-user --user-name developer-test

# Xóa custom policy
aws iam delete-policy \
    --policy-arn arn:aws:iam::$(aws sts get-caller-identity --query Account --output text):policy/WildcardFullAccess

# === Dọn EC2 ===
# Tìm instances dùng insecure-sg
aws ec2 describe-instances --filters "Name=instance.group-name,Values=insecure-sg" \
    --query 'Reservations[].Instances[].InstanceId' --region ap-southeast-1

# Terminate các instances đó
aws ec2 terminate-instances --instance-ids <instance-id> --region ap-southeast-1

# Xóa security group
aws ec2 delete-security-group --group-name insecure-sg --region ap-southeast-1

# === Dọn S3 ===
# Xóa nội dung và bucket vulnerable
aws s3 rm s3://vulnerable-public-data-<tên-bạn> --recursive
aws s3 rb s3://vulnerable-public-data-<tên-bạn>

# === Tắt GuardDuty ===
aws guardduty list-detectors --region ap-southeast-1
aws guardduty delete-detector --detector-id <detector-id> --region ap-southeast-1

# === Tắt Security Hub ===
aws securityhub disable-security-hub --region ap-southeast-1

# === Dọn CloudTrail ===
aws cloudtrail delete-trail --name FCAJ-Central-Trail

# Xóa nội dung và bucket log CloudTrail
aws s3 rm s3://fcaj-security-logs-<random-id> --recursive
aws s3 rb s3://fcaj-security-logs-<random-id>
```
{{%/expand%}}
