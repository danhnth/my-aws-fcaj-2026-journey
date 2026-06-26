---
title : "Bước 6: Dọn dẹp tài nguyên"
date : 2024-01-01 
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
