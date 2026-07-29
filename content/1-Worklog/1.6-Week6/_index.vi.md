---
title: "Worklog Tuần 6"
date: 2026-07-25
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Mục tiêu tuần 6:

* Nghiên cứu và hiểu về AWS Security Hub — giải pháp quản lý tư thế bảo mật tập trung trên cloud.
* Khám phá Amazon GuardDuty Tester — công cụ mã nguồn mở mô phỏng các kịch bản tấn công thực tế.
* Viết và đăng tải blog kỹ thuật về AWS Security Hub và Amazon GuardDuty Tester trên cộng đồng AWS Study Group.
* Chia sẻ kiến thức với các bạn học viên FCAJ và củng cố kỹ năng viết kỹ thuật.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 (20/07) | - Nghiên cứu sâu về AWS Security Hub <br>&emsp; + Dashboard bảo mật tập trung và tổng hợp findings <br>&emsp; + CSPM (Cloud Security Posture Management) theo CIS benchmarks <br>&emsp; + Attack path graphs, exposure findings, phân tích truy cập không dùng <br>&emsp; + Tích hợp với GuardDuty, Inspector, Macie | 20/07/2026 | 20/07/2026 | <https://docs.aws.amazon.com/securityhub/latest/userguide/> |
| 3 (21/07) | - Nghiên cứu Amazon GuardDuty Tester <br>&emsp; + Triển khai CDK và hạ tầng kiểm thử <br>&emsp; + Sáu nhóm findings: Recon, UnauthorizedAccess, Impact, CryptoCurrency, Policy, Trojan <br>&emsp; + Cách xác thực pipeline phát hiện bằng mô phỏng tấn công | 21/07/2026 | 21/07/2026 | <https://github.com/awslabs/amazon-guardduty-tester> |
| 4 (22/07) | - Viết bản nháp các blog kỹ thuật <br>&emsp; + Blog 1: Giới thiệu AWS Security Hub (tổng quan, tính năng chính, tích hợp) <br>&emsp; + Blog 2: Amazon GuardDuty Tester — Công cụ mới kiểm tra phát hiện bảo mật AWS <br>&emsp; + Blog 3: Sử dụng Amazon GuardDuty Tester để tự động hóa kiểm thử bảo mật | 22/07/2026 | 23/07/2026 | |
| 5 (23/07) | - Xem xét và hoàn thiện bản nháp blog <br>&emsp; + Xác minh độ chính xác kỹ thuật của mọi mô tả tính năng <br>&emsp; + Thêm ảnh chụp màn hình và đoạn code minh họa <br>&emsp; + Soát lỗi và đảm bảo văn phong rõ ràng | 23/07/2026 | 24/07/2026 | |
| 6 (24/07) | - Xem xét lần cuối và đăng blog lên AWS Study Group <br>&emsp; + Định dạng bài viết cho nền tảng cộng đồng <br>&emsp; + Thêm tags và danh mục để dễ tìm kiếm <br>&emsp; + Chia sẻ link đã xuất bản với nhóm FCAJ để nhận phản hồi | 24/07/2026 | 24/07/2026 | <https://awsstudygroup.com/> |
| 7 (25/07) | - **Thực hành:** <br>&emsp; + Ghi chép các kiến thức kỹ thuật chính thu nhận từ việc viết blog <br>&emsp; + Suy ngẫm về cách Security Hub và GuardDuty Tester bổ trợ cho nhau <br> - Xem xét tiến độ tuần 6 và chuẩn bị cho tuần 7 | 25/07/2026 | 25/07/2026 | |

### Kết quả đạt được tuần 6:

* Nắm vững kiến thức về **AWS Security Hub** — giải pháp bảo mật cloud tập trung thu thập, kết nối và làm giàu các tín hiệu bảo mật từ nhiều dịch vụ AWS (GuardDuty, Inspector, Macie, IAM Access Analyzer) trên một dashboard duy nhất.

* Tìm hiểu các tính năng chính của Security Hub:
  * CSPM (Cloud Security Posture Management) với CIS AWS Foundations Benchmark v1.4.0
  * Attack path graphs trực quan hóa cách kẻ tấn công có thể truy cập tài nguyên
  * Exposure findings kết hợp dữ liệu từ nhiều dịch vụ để xác định rủi ro có thể hành động
  * Phân tích truy cập không dùng với đề xuất chính sách đặc quyền tối thiểu
  * OCSF (Open Cybersecurity Schema Framework) chuẩn hóa findings

* Nghiên cứu **Amazon GuardDuty Tester** — công cụ mã nguồn mở từ AWS Labs triển khai Lambda functions qua CDK để mô phỏng các kịch bản tấn công thực tế, tạo findings GuardDuty trên sáu nhóm (Recon, UnauthorizedAccess, Impact, CryptoCurrency, Policy, Trojan).

* Đã viết và xuất bản **ba blog kỹ thuật** trên cộng đồng AWS Study Group:
  * [Blog 1: Giới thiệu AWS Security Hub](../3-BlogsPosted/3.1-Blog1/) — tổng quan tính năng, tích hợp và vai trò trong Security Operations Lab
  * [Blog 2: Amazon GuardDuty Tester — Công cụ mới kiểm tra phát hiện bảo mật AWS](../3-BlogsPosted/3.2-Blog2/) — giới thiệu công cụ và cách xác thực pipeline phát hiện
  * [Blog 3: Sử dụng Amazon GuardDuty Tester để tự động hóa kiểm thử bảo mật](../3-BlogsPosted/3.3-Blog3/) — hướng dẫn triển khai, chạy kiểm thử và quy trình xác thực ba pha

* Đã đăng blog lên nền tảng cộng đồng AWS Study Group và chia sẻ với nhóm FCAJ, nhận được phản hồi tích cực từ bạn học và người hướng dẫn.

* Củng cố kỹ năng viết kỹ thuật — học cách giải thích các khái niệm bảo mật AWS phức tạp một cách dễ hiểu cho cộng đồng cloud, và thực hành viết tài liệu song ngữ cho đối tượng rộng hơn.
