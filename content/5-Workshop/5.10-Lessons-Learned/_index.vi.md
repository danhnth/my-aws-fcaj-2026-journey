---
title : "Bài học rút ra"
date : 2024-01-01 
weight : 10
chapter : false
pre : " <b> 5.10. </b> "
---

#### Bài học rút ra & Hướng phát triển

**Khó khăn đã gặp**

Các dịch vụ bảo mật của AWS không cập nhật kết quả ngay lập tức (Real-time) mà có độ trễ từ **15 đến 30 phút**, gây khó khăn cho việc kiểm thử nhanh và lặp lại nhiều lần.

**Bài học rút ra**

- Hiểu sâu hơn về tầm quan trọng của việc thắt chặt quyền hạn (Least Privilege) ngay từ khi tạo tài nguyên thay vì đợi đến khi hệ thống bị cảnh báo.
- Các dịch vụ bảo mật gốc của AWS (CloudTrail, GuardDuty, Security Hub) tích hợp liền mạch và cung cấp tầm nhìn toàn diện khi được cấu hình cùng nhau.
- Phần lớn các lỗ hổng cloud đến từ **lỗi cấu hình** chứ không phải từ các cuộc tấn công phức tạp, khiến việc thiết lập cấu hình cơ bản đúng đắn trở nên rất quan trọng.

**Hướng phát triển tương lai**

Thay vì vào Console để vá lỗi thủ công (Manual Remediation), em sẽ nghiên cứu sử dụng **AWS Lambda** kết hợp với **Amazon EventBridge** để tự động vá lỗi ngay khi Security Hub phát hiện lỗ hổng (Auto-Remediation). Cách tiếp cận này sẽ:

1. Giảm thời gian khắc phục trung bình (MTTR)
2. Giảm thiểu lỗi do con người trong quá trình khắc phục
3. Cho phép thực thi nhất quán các chính sách bảo mật ở quy mô lớn
