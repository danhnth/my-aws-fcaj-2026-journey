---
title: "Worklog Tuần 3"
date: 2026-07-04
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---

### Mục tiêu tuần 3:

* Lên kế hoạch kiến trúc dự án "Insecure-by-Design" và xác định các kịch bản misconfiguration.
* Bắt đầu triển khai các tài nguyên AWS đầu tiên được cấu hình sai có chủ đích.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 4 (01/07) | - Thiết kế kiến trúc "Insecure-by-Design" <br> - Xác định các kịch bản misconfiguration cần triển khai: <br>&emsp; + Public S3 bucket chứa dữ liệu nhạy cảm <br>&emsp; + IAM role với quyền wildcard (*) quá mức <br>&emsp; + EC2 instance mở SSH public không giới hạn <br> - Định nghĩa cấu trúc thư mục dự án và bố trí module | 01/07/2026 | 01/07/2026 | |

### Kết quả đạt được tuần 3:

* Thiết kế kiến trúc dự án Insecure-by-Design bao gồm ba kịch bản misconfiguration chính: S3 bucket công khai, IAM role quá privilege và EC2 instance truy cập công khai.

* Ghi chép tình trạng bảo mật hiện tại và xác nhận rằng AWS Trusted Advisor và Security Hub (khi được bật) sẽ gắn cờ các phát hiện này là critical.

* Chuẩn bị nền tảng cho tuần 4, triển khai thêm tài nguyên dễ bị tấn công và mở rộng phạm vi giám sát.
