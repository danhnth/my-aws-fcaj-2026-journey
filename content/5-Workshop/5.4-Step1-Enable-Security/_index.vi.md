---
title : "Bước 1: Kích hoạt các dịch vụ Bảo mật"
date : 2024-01-01 
weight : 4
chapter : false
pre : " <b> 5.4. </b> "
---

#### Bước 1: Kích hoạt các dịch vụ Giám sát và Bảo mật

Để hệ thống ghi nhận kịp thời các lỗ hổng, chúng ta cần bật nền tảng giám sát trước khi triển khai hạ tầng lỗi cấu hình.

**1. AWS CloudTrail**

CloudTrail ghi lại tất cả hoạt động API trong tài khoản AWS, cung cấp nhật ký kiểm toán để phân tích sau này.

1. Truy cập **CloudTrail** Console → Chọn **Create trail**.
2. Cấu hình:
   - **Tên Trail**: `FCAJ-Central-Trail`
   - **Nơi lưu trữ**: Tạo một S3 bucket mới (ví dụ: `fcaj-security-logs-<random-id>`)
   - Giữ nguyên các cài đặt mặc định khác.
3. Chọn **Create trail**.

**2. Amazon GuardDuty**

GuardDuty sử dụng máy học (ML) và thông tin tình báo về mối đe dọa để phát hiện hành vi đáng ngờ.

1. Truy cập **GuardDuty** Console → Nhấn **Get Started**.
2. Nhấn **Enable GuardDuty** (không cần cấu hình thêm).
3. GuardDuty sẽ bắt đầu phân tích nhật ký trong vòng vài phút.

**3. AWS Security Hub**

Security Hub cung cấp một giao diện tập trung cho các cảnh báo bảo mật và điểm số tuân thủ.

1. Truy cập **Security Hub** Console → Nhấn **Go to Security Hub**.
2. Tại mục **Security standards**, tích chọn **CIS AWS Foundations Benchmark v1.4.0**.
3. Nhấn **Enable Security Hub**.
4. Chờ 15-30 phút để quá trình quét tuân thủ ban đầu hoàn tất.
