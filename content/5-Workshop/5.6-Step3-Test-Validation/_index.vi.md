---
title : "Bước 3: Kiểm thử & Đo lường"
date : 2024-01-01 
weight : 6
chapter : false
pre : " <b> 5.6. </b> "
---

#### Bước 3: Kiểm thử và Đo lường

Sau khi triển khai hạ tầng lỗi cấu hình, chờ khoảng **30 - 60 phút** để Security Hub và GuardDuty hoàn tất chu kỳ quét ban đầu.

**1. Kiểm tra Security Hub Findings**

1. Vào **Security Hub** console → **Findings**.
2. Bạn sẽ thấy các cảnh báo được gắn cờ đỏ liên quan đến lỗi cấu hình:

   | Mã Finding | Mô tả |
   |------------|-------|
   | **S3.2** | S3 buckets nên chặn truy cập công khai |
   | **IAM.1** | IAM policies không nên có toàn quyền quản trị |
   | **EC2.19** | Security groups không nên cho phép SSH không giới hạn |

3. Vào **Security Hub** → **Summary** để xem **điểm số tuân thủ (Compliance score)** tổng thể. Chụp ảnh màn hình điểm số thấp để làm minh chứng cho báo cáo.

**2. Kiểm tra GuardDuty Findings**

Để giả lập một hành vi tấn công và kích hoạt cảnh báo GuardDuty:

1. **Giả lập SSH brute force**: Từ máy local, thử SSH vào EC2 instance (sẽ thất bại vì không có key, nhưng GuardDuty sẽ ghi nhận):

   ```bash
   ssh ec2-user@<EC2-PUBLIC-IP>
   ```

2. **Giả lập hoạt động IAM đáng ngờ**: Dùng thông tin xác thực của `developer-test` (tạo access keys từ IAM console), chạy một API call bất thường:

   ```bash
   aws configure --profile dev-test
   # Nhập access key và secret key của developer-test
   aws ec2 describe-instances --profile dev-test
   aws ec2 create-snapshot --profile dev-test --volume-id <any-volume-id>
   ```

3. Quay lại **GuardDuty** console → **Findings** sau 15-30 phút. Bạn sẽ thấy các cảnh báo như:
   - `UnauthorizedAccess:EC2/SSHBruteForce`
   - `Behavior:IAMUser/ResourceConsumption`

4. Chụp ảnh màn hình các cảnh báo này để làm tài liệu cho báo cáo workshop.
