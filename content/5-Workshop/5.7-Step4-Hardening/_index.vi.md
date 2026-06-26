---
title : "Bước 4: Gia cố & Khắc phục"
date : 2024-01-01 
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

**2. Vá lỗi IAM — Áp dụng đặc quyền tối thiểu**

1. Vào **IAM** console → **Users** → `developer-test`.
2. Vào tab **Permissions**.
3. Tìm inline policy `WildcardFullAccess` → Chọn **Remove** (hoặc **Delete**).
4. Chọn **Add permissions** → **Attach policies directly**.
5. Tìm và chọn **AmazonS3ReadOnlyAccess** (một policy cụ thể, đặc quyền tối thiểu).
6. Chọn **Next** → **Add permissions**.
7. (Khuyến nghị) Vào tab **Security credentials** → Mục **Multi-factor authentication (MFA)** → **Assign MFA device** để bật MFA cho user này.

**3. Vá lỗi EC2 — Giới hạn SSH**

1. Vào **EC2** console → **Security Groups**.
2. Chọn `insecure-sg`.
3. Vào tab **Inbound rules** → Chọn **Edit inbound rules**.
4. Tìm rule SSH với Source `0.0.0.0/0`.
5. Thay đổi **Source** thành **My IP** (sẽ tự động điền địa chỉ IP hiện tại của bạn).
6. Chọn **Save rules**.

   > Thao tác này giới hạn SSH chỉ đến địa chỉ IP của bạn, loại bỏ hoàn toàn việc phơi bày cổng SSH ra toàn cầu.
