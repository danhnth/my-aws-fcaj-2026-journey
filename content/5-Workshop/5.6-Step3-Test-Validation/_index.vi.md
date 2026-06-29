---
title : "Bước 3: Kiểm thử & Đo lường"
date : 2026-06-26
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

{{%expand "AWS CLI — Phương thức Dòng lệnh" %}}
```bash
# Liệt kê tất cả Security Hub findings
aws securityhub get-findings --region ap-southeast-1

# Lọc findings theo từng control cụ thể
aws securityhub get-findings \
    --filters '{"ComplianceSecurityControlId":[{"Value":"S3.2","Comparison":"EQUALS"}]}' \
    --region ap-southeast-1
aws securityhub get-findings \
    --filters '{"ComplianceSecurityControlId":[{"Value":"IAM.1","Comparison":"EQUALS"}]}' \
    --region ap-southeast-1
aws securityhub get-findings \
    --filters '{"ComplianceSecurityControlId":[{"Value":"EC2.19","Comparison":"EQUALS"}]}' \
    --region ap-southeast-1

# Đếm số lượng findings FAILED
aws securityhub get-findings \
    --filters '{"ComplianceStatus":[{"Value":"FAILED","Comparison":"EQUALS"}]}' \
    --query 'length(Findings)' \
    --region ap-southeast-1
```
{{%/expand%}}

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

{{%expand "AWS CLI — Phương thức Dòng lệnh" %}}
```bash
# Liệt kê GuardDuty detectors để lấy detector ID
aws guardduty list-detectors --region ap-southeast-1

# Liệt kê tất cả findings (thay <detector-id> bằng ID ở trên)
aws guardduty list-findings --detector-id <detector-id> --region ap-southeast-1

# Xem chi tiết findings
aws guardduty get-findings --detector-id <detector-id> \
    --finding-ids $(aws guardduty list-findings --detector-id <detector-id> --query FindingIds --output text) \
    --region ap-southeast-1
```
{{%/expand%}}
