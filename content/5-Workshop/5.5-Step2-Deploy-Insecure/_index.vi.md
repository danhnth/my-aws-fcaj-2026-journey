---
title : "Bước 2: Triển khai hạ tầng lỗi cấu hình"
date : 2026-06-26
weight : 5
chapter : false
pre : " <b> 5.5. </b> "
---

#### Bước 2: Triển khai hạ tầng lỗi cấu hình

Chúng ta sẽ cố tình tạo ra 3 "lỗ hổng" kinh điển để hệ thống quét phát hiện.

**1. Lỗ hổng S3 — Public Bucket**

1. Vào **S3** console → Chọn **Create bucket**.
2. Cấu hình:
   - **Tên bucket**: `vulnerable-public-data-<tên-bạn>`
   - **Region**: `ap-southeast-1` (Singapore)
3. Tại mục **Block Public Access settings for this bucket**, **bỏ tích** ô *Block all public access*.
4. Xác nhận cảnh báo rằng bucket sẽ được công khai.
5. Chọn **Create bucket**.

{{%expand "AWS CLI — Phương thức Dòng lệnh" %}}
```bash
# 1. Tạo bucket (mặc định chặn public access)
aws s3 mb s3://vulnerable-public-data-<tên-bạn> --region ap-southeast-1

# 2. Gỡ chặn public access để bucket có thể công khai
aws s3api put-public-access-block --bucket vulnerable-public-data-<tên-bạn> \
    --public-access-block-configuration "BlockPublicAcls=false,IgnorePublicAcls=false,BlockPublicPolicy=false,RestrictPublicBuckets=false"

# 3. Gán ACL public-read
aws s3api put-bucket-acl --bucket vulnerable-public-data-<tên-bạn> --acl public-read
```
{{%/expand%}}

**2. Lỗ hổng IAM — Wildcard Quyền hạn quá rộng**

1. Vào **IAM** console → **Users** → **Create user**.
2. **Tên người dùng**: `developer-test`
3. Bỏ chọn "Provide user access to the AWS Management Console".
4. Chọn **Next**.
5. Chọn **Attach policies directly** → Chọn **Create policy**.
6. Chuyển sang tab **JSON** và dán policy cực kỳ nguy hiểm sau:

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

   > **Lưu ý:** Policy này cho phép toàn quyền (`*` trên `*`), vi phạm nghiêm trọng nguyên tắc đặc quyền tối thiểu (Principle of Least Privilege).

7. Đặt tên policy là `WildcardFullAccess` → Chọn **Create policy**.
8. Quay lại, chọn policy `WildcardFullAccess` vừa tạo → Chọn **Next**.
9. Xem lại và chọn **Create user**.

{{%expand "AWS CLI — Phương thức Dòng lệnh" %}}
```bash
# 1. Tạo IAM policy wildcard
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

# 2. Tạo IAM user (chỉ truy cập programmatic)
aws iam create-user --user-name developer-test

# 3. Gán policy wildcard cho user
aws iam attach-user-policy --user-name developer-test --policy-arn arn:aws:iam::$(aws sts get-caller-identity --query Account --output text):policy/WildcardFullAccess

# 4. Tạo access keys cho user
aws iam create-access-key --user-name developer-test
```
> **Lưu ý:** Lưu `AccessKeyId` và `SecretAccessKey` từ kết quả — cần dùng ở Bước 3.

{{%/expand%}}

**3. Lỗ hổng EC2 — Mở cổng SSH toàn cầu**

1. Tạo security group:
   - Vào **EC2** console → **Security Groups** → **Create security group**.
   - **Tên**: `insecure-sg`
   - **Mô tả**: Security group cho phép SSH toàn cầu
   - **Inbound rules**: Thêm rule → Type: **SSH (Port 22)**, Source: `0.0.0.0/0`
   - Chọn **Create security group**.

2. (Tùy chọn) Khởi chạy một EC2 instance để tạo thêm findings:
   - Vào **EC2** → **Instances** → **Launch instance**.
   - **Tên**: `vulnerable-ec2`
   - **AMI**: Amazon Linux 2023 (free tier eligible)
   - **Loại instance**: `t2.micro`
   - **Key pair**: Tiếp tục không cần key pair
   - **Network settings**: Chọn **Edit** → Chọn **Select existing security group** → Chọn `insecure-sg`.
   - Chọn **Launch instance**.

{{%expand "AWS CLI — Phương thức Dòng lệnh" %}}
```bash
# 1. Tạo security group
aws ec2 create-security-group --group-name insecure-sg \
    --description "Security group cho phép SSH toàn cầu" \
    --region ap-southeast-1

# 2. Thêm inbound rule SSH từ 0.0.0.0/0
aws ec2 authorize-security-group-ingress --group-name insecure-sg \
    --protocol tcp --port 22 --cidr 0.0.0.0/0 \
    --region ap-southeast-1

# 3. (Tùy chọn) Khởi chạy EC2 instance
aws ec2 run-instances \
    --image-id resolve-ssm:/aws/service/ami-amazon-linux-latest/al2023-ami-kernel-default-x86_64 \
    --instance-type t2.micro \
    --security-groups insecure-sg \
    --region ap-southeast-1
```
> **Lưu ý:** Tham số `resolve-ssm` tự động lấy AMI ID mới nhất. Nếu không hỗ trợ, dùng `aws ssm get-parameters --names /aws/service/ami-amazon-linux-latest/al2023-ami-kernel-default-x86_64` để lấy AMI ID trước.

{{%/expand%}}
