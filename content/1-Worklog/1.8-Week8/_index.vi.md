---
title: "Worklog Tuần 8"
date: 2026-08-14
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Mục tiêu tuần 8:

* Tổng hợp và hoàn thiện tất cả tài liệu dự án từ Security Operations Lab.
* Viết báo cáo so sánh compliance (trước và sau hardening) kèm bằng chứng.
* Hoàn thiện tài liệu GuardDuty findings với phân loại và phân tích.
* Hoàn thiện blog kỹ thuật về EKS Pod Identity Session Policies.
* Chuẩn bị và nộp báo cáo thực tập cuối cùng và tài liệu bàn giao.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 (03/08) | - Hoàn thiện tài liệu Security Operations Lab Workshop: <br>&emsp; + Xem xét tất cả 6 bước (Kích hoạt → Triển khai → Phát hiện → Hardening → Đánh giá lại → Dọn dẹp) <br>&emsp; + Đảm bảo hướng dẫn song ngữ (EN/VI) đầy đủ và nhất quán <br>&emsp; + Xác minh tất cả lệnh CLI và bước điều hướng console chính xác | 03/08/2026 | 03/08/2026 | |
| 3 (04/08) | - Viết Báo cáo So sánh Tuân thủ: <br>&emsp; + Ghi chép điểm tuân thủ Security Hub trước hardening và các phát hiện <br>&emsp; + Ghi chép cải thiện sau hardening (S3.2, IAM.1, EC2.19 → PASSED) <br>&emsp; + Bao gồm ảnh chụp màn hình và kết quả CLI làm bằng chứng <br>&emsp; + Thêm bảng so sánh trước/sau cho ba CIS controls | 04/08/2026 | 05/08/2026 | |
| 4 (05/08) | - Hoàn thiện Tài liệu GuardDuty Findings: <br>&emsp; + Phân loại 50+ phát hiện theo loại (Recon, UnauthorizedAccess, Impact, CryptoCurrency, Policy, Trojan) <br>&emsp; + Ghi chép mức độ nghiêm trọng và đề xuất khắc phục cho từng danh mục <br>&emsp; + Thêm ảnh chụp màn hình từ GuardDuty console | 05/08/2026 | 06/08/2026 | |
| 5 (06/08) | - Xem xét lần cuối blog kỹ thuật: <br>&emsp; + Tiếp thu phản hồi từ bạn học và người hướng dẫn <br>&emsp; + Đảm bảo tất cả ví dụ code và sơ đồ kiến trúc chính xác <br>&emsp; + Xác nhận blog đã được đăng và có thể truy cập trên AWS Study Group <br> - Bắt đầu tổng hợp báo cáo thực tập cuối cùng (Chương 1-5) | 06/08/2026 | 07/08/2026 | |
| 6 (07/08) | - Hoàn thiện báo cáo thực tập cuối cùng: <br>&emsp; + Viết Chương 4 (Sản phẩm đạt được) với mô tả tất cả deliverables <br>&emsp; + Viết Chương 5 (Tổng kết) với bài học kinh nghiệm và cảm nhận <br>&emsp; + Xem xét và soát lỗi toàn bộ báo cáo <br> - Nộp báo cáo cho người hướng dẫn xem xét | 07/08/2026 | 08/08/2026 | |
| 7 (08/08) | - **Kết thúc:** <br>&emsp; + Tiếp thu phản hồi từ người hướng dẫn vào báo cáo cuối cùng <br>&emsp; + Chuẩn bị gói bàn giao (tất cả tài liệu, code, ảnh chụp màn hình) <br>&emsp; + Xác minh không còn tài nguyên AWS nào phát sinh chi phí <br> - Suy ngẫm về hành trình 8 tuần FCAJ và ghi lại những bài học chính | 08/08/2026 | 14/08/2026 | |

### Kết quả đạt được tuần 8:

* Hoàn thiện **Security Operations & Hardening Lab Workshop** - hướng dẫn song ngữ (EN/VI) đầy đủ bao gồm tất cả 6 bước của vòng đời bảo mật với hướng dẫn AWS Console và CLI song song.

* Hoàn thành **Báo cáo So sánh Tuân thủ**:
  * Ghi chép baseline trước hardening với các phát hiện Security Hub (S3.2, IAM.1, EC2.19 đều FAILED)
  * Ghi lại kết quả sau hardening với bằng chứng cả ba controls chuyển sang PASSED
  * Chứng minh sự cải thiện đáng kể trong điểm tuân thủ tổng thể
  * Bao gồm ảnh chụp màn hình trước/sau và lệnh CLI xác minh

* Hoàn thành **Tài liệu GuardDuty Findings**:
  * Phân loại 50+ phát hiện trên tất cả sáu loại (Recon, UnauthorizedAccess, Impact, CryptoCurrency, Policy, Trojan)
  * Ghi chép mức độ nghiêm trọng, tài nguyên bị ảnh hưởng và các bước khắc phục được đề xuất cho từng danh mục
  * Bao gồm ảnh chụp màn hình từ GuardDuty console làm bằng chứng

* Đã xuất bản và hoàn thiện **blog kỹ thuật** về EKS Pod Identity Session Policies trên cộng đồng AWS Study Group.

* Tổng hợp **báo cáo thực tập cuối cùng** (tài liệu LaTeX này):
  * Hoàn thành tất cả 5 chương bao gồm giới thiệu công ty, quá trình thực tập, kiến thức thu nhận được, sản phẩm đạt được và cảm nhận cá nhân
  * Đã nộp báo cáo cho người hướng dẫn xem xét và tiếp thu phản hồi

* Chuẩn bị gói bàn giao dự án hoàn chỉnh:
  * Tất cả mã nguồn, mẫu CloudFormation/IaC (nếu có) và script CLI
  * Sắp xếp ảnh chụp màn hình và tệp bằng chứng
  * Hoàn thiện tài liệu worklog cho tất cả 8 tuần

* **Bài học chính:** Chương trình FCAJ cung cấp một hành trình có cấu trúc, thực hành từ kiến thức AWS cơ bản đến vận hành bảo mật nâng cao. Security Operations Lab đặc biệt chứng minh vòng đời khắc phục hoàn chỉnh và giá trị thực tế của CIS AWS Foundations Benchmark. Việc viết blog kỹ thuật và tham gia hội thảo GenAI đã bổ sung các kỹ năng chuyên nghiệp quý giá ngoài kỹ năng kỹ thuật thuần túy.
