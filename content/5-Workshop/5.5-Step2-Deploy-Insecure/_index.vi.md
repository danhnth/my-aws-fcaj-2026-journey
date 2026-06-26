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
