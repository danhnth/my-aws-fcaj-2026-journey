---
title : "Bước 4: Gia cố & Khắc phục"
date : 2026-06-26
weight : 7
chapter : false
pre : " <b> 5.7. </b> "
---

#### Bước 4: Gia cố hệ thống (Hardening & Remediation)

Bây giờ, chúng ta đóng vai trò Kỹ sư bảo mật để vá lại các lỗ hổng dựa trên gợi ý từ Security Hub.

**1. Vá lỗi S3 — Bật lại Block Public Access**

1. Vào **S3** console.
2. Chọn bucket `vulnerable-public-data-<tên-bạn>`.
3. Vào tab **Permissions** → **Block Public Access**.
4. Chọn **Edit** → Tích chọn **Block all public access**.
5. Chọn **Save changes**.

{{%expand "AWS CLI — Phương thức Dòng lệnh" %}}
```bash
# Bật lại Block All Public Access cho bucket
aws s3api put-public-access-block --bucket vulnerable-public-data-<tên-bạn> \
    --public-access-block-configuration "BlockPublicAcls=true,IgnorePublicAcls=true,BlockPublicPolicy=true,RestrictPublicBuckets=true"

# Đặt lại ACL về private
aws s3api put-bucket-acl --bucket vulnerable-public-data-<tên-bạn> --acl private
```
{{%/expand%}}

**2. Vá lỗi IAM — Áp dụng đặc quyền tối thiểu**

1. Vào **IAM** console → **Users** → `developer-test`.
2. Vào tab **Permissions**.
3. Tìm inline policy `WildcardFullAccess` → Chọn **Remove** (hoặc **Delete**).
4. Chọn **Add permissions** → **Attach policies directly**.
5. Tìm và chọn **AmazonS3ReadOnlyAccess** (một policy cụ thể, đặc quyền tối thiểu).
6. Chọn **Next** → **Add permissions**.
7. (Khuyến nghị) Vào tab **Security credentials** → Mục **Multi-factor authentication (MFA)** → **Assign MFA device** để bật MFA cho user này.

{{%expand "AWS CLI — Phương thức Dòng lệnh" %}}
```bash
# 1. Gỡ bỏ wildcard policy (tìm policy ARN trước)
aws iam list-attached-user-policies --user-name developer-test

aws iam detach-user-policy --user-name developer-test \
    --policy-arn arn:aws:iam::$(aws sts get-caller-identity --query Account --output text):policy/WildcardFullAccess

# 2. Gán policy đặc quyền tối thiểu (S3 ReadOnly)
aws iam attach-user-policy --user-name developer-test \
    --policy-arn arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess

# 3. (Tùy chọn) Kiểm tra danh sách policy đã gán
aws iam list-attached-user-policies --user-name developer-test
```
{{%/expand%}}

**3. Vá lỗi EC2 — Giới hạn SSH**

1. Vào **EC2** console → **Security Groups**.
2. Chọn `insecure-sg`.
3. Vào tab **Inbound rules** → Chọn **Edit inbound rules**.
4. Tìm rule SSH với Source `0.0.0.0/0`.
5. Thay đổi **Source** thành **My IP** (sẽ tự động điền địa chỉ IP hiện tại của bạn).
6. Chọn **Save rules**.

   > Thao tác này giới hạn SSH chỉ đến địa chỉ IP của bạn, loại bỏ hoàn toàn việc phơi bày cổng SSH ra toàn cầu.

{{%expand "AWS CLI — Phương thức Dòng lệnh" %}}
```bash
# 1. Xóa rule SSH toàn cầu
aws ec2 revoke-security-group-ingress --group-name insecure-sg \
    --protocol tcp --port 22 --cidr 0.0.0.0/0 \
    --region ap-southeast-1

# 2. Thêm SSH chỉ cho phép IP của bạn
aws ec2 authorize-security-group-ingress --group-name insecure-sg \
    --protocol tcp --port 22 --cidr $(curl -s http://checkip.amazonaws.com/)/32 \
    --region ap-southeast-1

# 3. Kiểm tra lại rules
aws ec2 describe-security-groups --group-names insecure-sg --region ap-southeast-1
```
{{%/expand%}}
