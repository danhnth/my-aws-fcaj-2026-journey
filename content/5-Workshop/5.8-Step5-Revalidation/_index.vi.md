---
title : "Bước 5: Tái thẩm định"
date : 2026-06-26
weight : 8
chapter : false
pre : " <b> 5.8. </b> "
---

#### Bước 5: Tái thẩm định kết quả

Sau khi hoàn tất các bước gia cố, chúng ta cần xác minh rằng các hành động khắc phục đã hiệu quả.

1. **Chờ chu kỳ quét mới**

   Security Hub chạy quét tuân thủ định kỳ. Chờ khoảng **30-60 phút** để quá trình quét tiếp theo hoàn tất sau khi bạn thay đổi cấu hình. Bạn cũng có thể làm mới trang findings thủ công.

2. **Kiểm tra lại Security Hub findings**

   Vào **Security Hub** → **Findings** và kiểm tra trạng thái của các control đã được gắn cờ trước đó:

   | Mã Control | Trước khi gia cố | Sau khi gia cố |
   |------------|-----------------|----------------|
   | S3.2 (Chặn S3 public) | **Failed** | **Passed** ✅ |
   | IAM.1 (Không có policy toàn quyền) | **Failed** | **Passed** ✅ |
   | EC2.19 (Giới hạn SSH) | **Failed** | **Passed** ✅ |

3. **So sánh điểm số tuân thủ**

   - Vào **Security Hub** → **Summary**.
   - So sánh **điểm số tuân thủ (Compliance score)** hiện tại với ảnh chụp từ Bước 3.
   - Điểm số sẽ tăng lên đáng kể sau khi gia cố.
   - Chụp ảnh màn hình mới cho thấy điểm số đã cải thiện.

4. **Xác nhận GuardDuty alerts**

   Các cảnh báo GuardDuty từ lần giả lập tấn công trước đó vẫn còn; nhưng sẽ không có cảnh báo nghiêm trọng mới nào được tạo ra từ hạ tầng đã được gia cố.

{{%expand "AWS CLI — Phương thức Dòng lệnh" %}}
```bash
# 1. Kiểm tra trạng thái S3.2 (sẽ là PASSED sau khi gia cố)
aws securityhub get-findings \
    --filters '{"ComplianceSecurityControlId":[{"Value":"S3.2","Comparison":"EQUALS"}]}' \
    --query 'Findings[].Compliance.Status' \
    --region ap-southeast-1

# 2. Kiểm tra trạng thái IAM.1
aws securityhub get-findings \
    --filters '{"ComplianceSecurityControlId":[{"Value":"IAM.1","Comparison":"EQUALS"}]}' \
    --query 'Findings[].Compliance.Status' \
    --region ap-southeast-1

# 3. Kiểm tra trạng thái EC2.19
aws securityhub get-findings \
    --filters '{"ComplianceSecurityControlId":[{"Value":"EC2.19","Comparison":"EQUALS"}]}' \
    --query 'Findings[].Compliance.Status' \
    --region ap-southeast-1

# 4. Tính điểm tuân thủ: PASSED / (PASSED + FAILED)
aws securityhub get-findings \
    --filters '{"ComplianceStatus":[{"Value":"PASSED","Comparison":"EQUALS"}]}' \
    --query 'length(Findings)' \
    --region ap-southeast-1

aws securityhub get-findings \
    --filters '{"ComplianceStatus":[{"Value":"FAILED","Comparison":"EQUALS"}]}' \
    --query 'length(Findings)' \
    --region ap-southeast-1
```
{{%/expand%}}
