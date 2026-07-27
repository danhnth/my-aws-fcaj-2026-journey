---
title: "Worklog Tuần 4"
date: 2026-07-18
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu tuần 4:

* Kích hoạt các dịch vụ giám sát bảo mật AWS (CloudTrail, GuardDuty, Security Hub) để thiết lập pipeline phát hiện tập trung.
* Triển khai hạ tầng cơ bản dễ bị tấn công có chủ đích.
* Chạy kiểm thử & xác nhận - quan sát cách Security Hub và GuardDuty phát hiện và gắn cờ các cấu hình sai.
* Bắt đầu giai đoạn hardening & khắc phục bằng cách sửa các phát hiện nghiêm trọng nhất.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 (06/07) | **Kích hoạt các dịch vụ giám sát bảo mật AWS** <br>&emsp; + Tạo CloudTrail trail (`FCAJ-Central-Trail`) với multi-region logging <br>&emsp; + Kích hoạt Amazon GuardDuty để phát hiện mối đe dọa <br>&emsp; + Kích hoạt AWS Security Hub với CIS AWS Foundations Benchmark v1.4.0 <br>&emsp; + Xác minh cả ba dịch vụ đều hoạt động và đang ghi log | 06/07/2026 | 06/07/2026 | <https://docs.aws.amazon.com/securityhub/> |
| 3 (07/07) | **Triển khai hạ tầng dễ bị tấn công** <br>&emsp; + Tạo VPC với public subnet <br>&emsp; + Tạo S3 bucket public với bucket policy cho phép đọc ẩn danh <br>&emsp; + Tạo IAM role quá privilege với wildcard permissions <br>&emsp; + Launch EC2 instance với SSH mở <br>&emsp; + Xác minh tất cả tài nguyên đã triển khai và cấu hình sai như dự định | 07/07/2026 | 07/07/2026 | |
| 4 (08/07) | **Chạy kiểm thử + GuardDuty Tester** *(gộp)* <br>&emsp; + Xem xét các phát hiện Security Hub - S3.2, IAM.1, EC2.19 (bản quét từ Thứ 3 hoàn tất qua đêm) <br>&emsp; + Ghi lại điểm tuân thủ trước hardening <br>&emsp; + Mô phỏng SSH brute force và hoạt động IAM đáng ngờ để kích hoạt cảnh báo GuardDuty <br>&emsp; + Triển khai Amazon GuardDuty Tester via CDK (triển khai nền trong khi đang xem xét findings) <br>&emsp; + Thực thi `guardduty_tester.py --all` để tạo 50+ loại phát hiện <br>&emsp; + Xem xét tất cả các phát hiện đã tạo trong GuardDuty console | 08/07/2026 | 08/07/2026 | <https://github.com/awslabs/amazon-guardduty-tester> |
| 5 (09/07) | **Hardening & khắc phục** <br>&emsp; + Sửa S3 - chặn tất cả truy cập public trên bucket dễ bị tấn công <br>&emsp; + Sửa IAM - gỡ policy wildcard, gắn policy đặc quyền tối thiểu, bật MFA <br>&emsp; + Sửa EC2 - giới hạn SSH inbound chỉ đến IP của tôi <br>&emsp; + Ghi chép từng hành động khắc phục với bằng chứng trước/sau | 09/07/2026 | 09/07/2026 | |
| 6 (10/07) | **Xác minh + tổng kết** <br>&emsp; + Xác minh cả ba bản sửa đã được áp dụng đúng <br>&emsp; + Chạy lại Security Hub scan và xác nhận findings chuyển sang PASSED <br>&emsp; + Chụp điểm tuân thủ sau hardening và so sánh với baseline <br>&emsp; + Xem xét tiến độ tuần 4 và lên kế hoạch tuần 5 | 10/07/2026 | 10/07/2026 | |

### Kết quả đạt được tuần 4:

* Đã kích hoạt thành công ba dịch vụ giám sát bảo mật AWS cốt lõi:
  * **AWS CloudTrail**: Tạo trail đa vùng (`FCAJ-Central-Trail`) ghi lại tất cả management events vào S3 bucket với log file validation được bật.
  * **Amazon GuardDuty**: Kích hoạt dịch vụ phát hiện mối đe dọa và xác minh nó bắt đầu phân tích CloudTrail, VPC Flow Logs và DNS logs trong vòng vài phút.
  * **AWS Security Hub**: Kích hoạt với tiêu chuẩn CIS AWS Foundations Benchmark v1.4.0 và xác nhận quá trình quét tuân thủ ban đầu đang chạy.

* Triển khai toàn bộ hạ tầng dễ bị tấn công:
  * S3 bucket public với bucket policy cho phép đọc ẩn danh
  * IAM role quá privilege (`WildcardFullAccess`) với `Action: "*"` và `Resource: "*"`
  * EC2 instance trong public subnet với SSH (port 22) mở cho 0.0.0.0/0
  * Xác minh tất cả tài nguyên đã được cấu hình sai như dự định qua AWS Console và CLI

* Đã chạy kiểm thử & xác nhận toàn diện:
  * Xem xét các phát hiện Security Hub - xác nhận S3.2 (bucket public), IAM.1 (admin toàn quyền) và EC2.19 (SSH không giới hạn) đều bị gắn cờ **FAILED**
  * Chụp điểm tuân thủ Security Hub trước hardening làm cơ sở so sánh
  * Mô phỏng SSH brute force và hoạt động IAM đáng ngờ để kích hoạt cảnh báo GuardDuty
  * Triển khai Amazon GuardDuty Tester qua CDK và thực thi `guardduty_tester.py --all`, tạo 50+ loại phát hiện trên các danh mục Recon, UnauthorizedAccess, Impact, CryptoCurrency, Policy và Trojan
  * Xem xét và ghi chép tất cả các phát hiện GuardDuty trong console

* Đã thực hiện giai đoạn hardening & khắc phục:
  * **S3**: Chặn tất cả truy cập public trên bucket dễ bị tấn công và đặt lại ACL về private
  * **IAM**: Gỡ policy `WildcardFullAccess` khỏi `developer-test`, gắn `AmazonS3ReadOnlyAccess` (đặc quyền tối thiểu) và bật MFA
  * **EC2**: Thu hồi quy tắc SSH inbound toàn cầu (0.0.0.0/0) và giới hạn truy cập chỉ đến IP công cộng của tôi
  * Ghi chép từng hành động khắc phục với lệnh CLI và ảnh chụp màn hình

* Đã chụp điểm tuân thủ Security Hub trước hardening để so sánh sau hardening trong Tuần 5.
