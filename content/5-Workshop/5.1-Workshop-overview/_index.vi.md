---
title : "Giới thiệu Workshop"
date : 2024-01-01 
weight : 1
chapter : false
pre : " <b> 5.1. </b> "
---

#### Giới thiệu Workshop

Workshop này tiếp cận AWS Cloud qua góc nhìn của một **Kỹ sư Bảo mật Cloud (Cloud Security Engineer)**. Mục tiêu cốt lõi là triển khai một môi trường cloud có kiểm soát nhưng cố tình chứa lỗ hổng ("Insecure-by-Design"), giám sát nó bằng các dịch vụ bảo mật gốc của AWS, và gia cố hệ thống một cách có hệ thống để đáp ứng các chuẩn mực bảo mật doanh nghiệp (như CIS AWS Foundations Benchmark).

**Các giai đoạn chính:**

1. **Xây dựng hạ tầng lỗi cấu hình** — Tạo các lỗ hổng phổ biến: S3 bucket công khai, IAM role với quyền wildcard quá rộng, và EC2 instance mở cổng SSH toàn cầu.
2. **Giám sát & Phát hiện liên tục** — Thiết lập pipeline ghi nhật ký và phát hiện mối đe dọa tập trung với AWS CloudTrail, Amazon GuardDuty và AWS Security Hub.
3. **Gia cố & Khắc phục** — Thực hiện các bước vá lỗi để áp dụng nguyên tắc đặc quyền tối thiểu và xử lý từng cảnh báo.
4. **Kiểm toán & Xác thực** — So sánh điểm số tuân thủ trước và sau khi gia cố bằng bài đánh giá CIS AWS Foundations Benchmark của Security Hub.

**Kết quả đạt được:**

Sau khi hoàn thành workshop, bạn sẽ có kinh nghiệm thực tế trong:
- Xác định các lỗi cấu hình bảo mật AWS phổ biến
- Cấu hình dịch vụ bảo mật AWS để giám sát tập trung
- Diễn giải các cảnh báo và điểm số tuân thủ từ Security Hub
- Áp dụng chính sách IAM đặc quyền tối thiểu và kiểm soát mạng
- Xác thực cải thiện tình trạng bảo mật qua các chỉ số định lượng
