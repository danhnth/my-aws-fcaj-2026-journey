---
title: "Worklog Tuần 5"
date: 2026-07-18
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Mục tiêu tuần 5:

* Hoàn thành giai đoạn hardening & khắc phục bằng cách xác minh tất cả các bản vá có hiệu quả.
* Chạy đánh giá lại (Bước 5): so sánh điểm tuân thủ Security Hub sau hardening với baseline trước hardening.
* Thực hiện dọn dẹp hoàn toàn (Bước 6): xóa tất cả tài nguyên lab để tránh phát sinh chi phí.
* Tổng hợp tài liệu dự án cuối cùng, báo cáo so sánh tuân thủ và bài học kinh nghiệm.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 (13/07) | - Hoàn thành hardening & khắc phục: <br>&emsp; + Xác minh S3 bucket đã hoàn toàn private (kiểm tra truy cập ẩn danh) <br>&emsp; + Xác minh IAM user chỉ có quyền đặc quyền tối thiểu <br>&emsp; + Xác minh security group EC2 giới hạn SSH chỉ đến IP của tôi <br> - Chạy lại Security Hub scan và kiểm tra cả ba controls chuyển sang PASSED | 13/07/2026 | 13/07/2026 | |
| 3 (14/07) | - Chạy đánh giá lại (Bước 5): <br>&emsp; + So sánh điểm tuân thủ Security Hub sau hardening với baseline trước hardening <br>&emsp; + Xác nhận S3.2, IAM.1, EC2.19 đã chuyển từ FAILED sang PASSED <br>&emsp; + Xác minh không có cảnh báo GuardDuty nghiêm trọng mới từ hạ tầng đã được hardening <br> - Chụp ảnh điểm tuân thủ đã cải thiện cho báo cáo cuối cùng | 14/07/2026 | 14/07/2026 | <https://docs.aws.amazon.com/securityhub/> |
| 4 (15/07) | - Thực hiện dọn dẹp (Bước 6): <br>&emsp; + Xóa IAM user `developer-test` và gỡ/xóa policies <br>&emsp; + Hủy EC2 instance `vulnerable-ec2` <br>&emsp; + Xóa security group `insecure-sg` <br>&emsp; + Làm rỗng và xóa S3 bucket `vulnerable-public-data-*` <br>&emsp; + Tắt GuardDuty detector <br>&emsp; + Tắt Security Hub <br>&emsp; + Xóa CloudTrail trail và S3 bucket chứa log <br> - Xác minh toàn bộ tài nguyên đã được xóa | 15/07/2026 | 15/07/2026 | |
| 5 (16/07) | - Tổng hợp báo cáo dự án cuối cùng: <br>&emsp; + Viết so sánh tuân thủ (trước và sau hardening) <br>&emsp; + Ghi chép tất cả hành động khắc phục kèm lệnh CLI <br>&emsp; + Sắp xếp ảnh chụp màn hình Security Hub findings và GuardDuty alerts <br>&emsp; + Tóm tắt kết quả vòng đời bảo mật | 16/07/2026 | 17/07/2026 | |
| 6 (17/07) | - Viết phần bài học kinh nghiệm: <br>&emsp; + Các kiến thức kỹ thuật chính từ lab security operations <br>&emsp; + Thách thức gặp phải và cách giải quyết <br>&emsp; + Cải tiến trong tương lai và các kịch bản bảo mật nâng cao <br> - Xem xét và hoàn thiện tất cả tài liệu | 17/07/2026 | 17/07/2026 | |
| 7 (18/07) | - **Thực hành:** <br>&emsp; + Xác minh không còn tài nguyên nào phát sinh chi phí (AWS Cost Explorer) <br>&emsp; + Nộp worklog cuối cùng và tài liệu dự án <br> - Suy ngẫm về hành trình 5 tuần workshop | 18/07/2026 | 18/07/2026 | |

### Kết quả đạt được tuần 5:

* Đã hoàn thành giai đoạn hardening & khắc phục với kết quả đã xác minh:
  * **S3**: Xác nhận bucket đã hoàn toàn private - các yêu cầu truy cập ẩn danh trả về 403 Forbidden
  * **IAM**: Xác nhận user `developer-test` chỉ còn `AmazonS3ReadOnlyAccess`; policy wildcard đã được gỡ hoàn toàn
  * **EC2**: Xác nhận quy tắc SSH inbound đã giới hạn chỉ đến IP công cộng của tôi; truy cập toàn cầu (0.0.0.0/0) đã bị thu hồi

* Đã chạy đánh giá lại và xác nhận cả ba Security Hub controls chuyển từ FAILED sang PASSED:
  * **S3.2** (Chặn truy cập public S3): FAILED → **PASSED** X
  * **IAM.1** (Không có policy admin toàn quyền): FAILED → **PASSED** X
  * **EC2.19** (SSH bị giới hạn): FAILED → **PASSED** X
  * Điểm tuân thủ Security Hub tổng thể đã cải thiện đáng kể so với baseline trước hardening

* Đã thực hiện dọn dẹp hoàn toàn tất cả tài nguyên lab:
  * Xóa IAM user `developer-test` và tất cả policies đã gắn
  * Hủy EC2 instance `vulnerable-ec2` và xóa security group `insecure-sg`
  * Làm rỗng và xóa S3 bucket dễ bị tấn công và S3 bucket chứa CloudTrail logs
  * Tắt GuardDuty detector và Security Hub
  * Xóa CloudTrail trail (`FCAJ-Central-Trail`)
  * Xác minh toàn bộ tài nguyên đã được xóa qua AWS Console và Cost Explorer

* Đã tổng hợp báo cáo dự án cuối cùng:
  * Báo cáo so sánh tuân thủ trước và sau hardening kèm ảnh chụp màn hình
  * Ghi chép tất cả hành động khắc phục với lệnh AWS CLI tương ứng
  * Phân loại các phát hiện GuardDuty theo danh mục (Recon, UnauthorizedAccess, Impact, CryptoCurrency, Policy, Trojan)
  * Tóm tắt vòng đời bảo mật hoàn chỉnh: Kích hoạt → Triển khai → Phát hiện → Hardening → Đánh giá lại → Dọn dẹp

* Đã ghi chép các bài học kinh nghiệm chính:
  * Các dịch vụ bảo mật cần được kích hoạt **trước khi** triển khai workloads để ghi lại toàn bộ dòng thời gian phát hiện
  * Infrastructure as Code hiệu quả cho hạ tầng có thể tái tạo nhưng cần quản lý state cẩn thận
  * CIS AWS Foundations Benchmark cung cấp khuôn khổ thực tế để đánh giá và cải thiện tư thế bảo mật đám mây
  * GuardDuty với ML-based threat detection có thể xác định các mẫu tấn công (SSH brute force, port scanning, crypto mining) mà giám sát truyền thống bỏ lỡ
  * Nguyên tắc đặc quyền tối thiểu là kiểm soát bảo mật có tác động lớn nhất đối với IAM
  * Khắc phục tự động qua tích hợp Security Hub sẽ giảm đáng kể thời gian phản hồi trong môi trường sản xuất
