---
title: "Blog 1"
date: 2026-07-24
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# Giới Thiệu Về AWS Security Hub

## AWS Security Hub Là Gì?

**AWS Security Hub** là giải pháp bảo mật đám mây thống nhất, giúp ưu tiên và phản hồi các vấn đề bảo mật quan trọng ở quy mô lớn. Dịch vụ này tự động thu thập, kết hợp và làm giàu các tín hiệu bảo mật từ nhiều dịch vụ AWS — bao gồm quản lý tư thế bảo mật (CSPM), quản lý lỗ hổng (Amazon Inspector), phát hiện dữ liệu nhạy cảm (Amazon Macie), và phát hiện mối đe dọa (Amazon GuardDuty) — mang đến một bảng điều khiển duy nhất cho tình trạng bảo mật của bạn.

Thay vì chuyển đổi giữa nhiều bảng điều khiển bảo mật khác nhau, Security Hub tập trung các findings, áp dụng phân tích ngữ cảnh, và hiển thị các rủi ro có thể hành động trước tiên.

## Các Tính Năng Chính

### Bảng Điều Khiển Bảo Mật Thống Nhất
Security Hub cung cấp cái nhìn toàn diện về mức độ phơi nhiễm, mối đe dọa, phạm vi bảo mật và tài nguyên. Bảng điều khiển bao gồm **attack path graph** tương tác, trực quan hóa cách kẻ tấn công tiềm năng có thể truy cập và xâm phạm tài nguyên liên quan đến một exposure finding.

### Thông Tin Chi Tiết Có Thể Hành Động
Thông qua phân tích nâng cao, Security Hub biến các tín hiệu bảo mật phức tạp thành thông tin chi tiết rõ ràng, được ưu tiên, giúp đội ngũ bảo mật đưa ra quyết định nhanh chóng.

### Exposure Findings
Security Hub kết hợp findings từ nhiều nguồn — CSPM control checks, Amazon Inspector và các dịch vụ AWS khác — để phát hiện mức độ phơi nhiễm liên quan đến tài nguyên AWS của bạn.

### Phân Tích Truy Cập Không Dùng
Security Hub tự động xác định IAM roles, users, access keys và permissions không được sử dụng trong vòng **90 ngày**. Dịch vụ có thể tạo đề xuất chính sách đặc quyền tối thiểu để giúp thu hẹp quyền truy cập.

### Định Dạng OCSF
Tất cả findings trong Security Hub được định dạng theo chuẩn OCSF, bao gồm findings từ Security Hub CSPM, GuardDuty, Macie và Inspector.

### Quy Trình Tự Động Hóa
Security Hub bao gồm khả năng phản hồi tự động và tích hợp với **Jira Cloud** và **ServiceNow ITSM** để quản lý ticket và tự động hóa quy trình làm việc.

## Cách Security Hub Hoạt Động Với Các Dịch Vụ AWS Khác

Security Hub nhận findings từ các dịch vụ bảo mật AWS sau:

| Dịch vụ | Vai trò |
|---------|---------|
| **AWS Security Hub CSPM** | Đánh giá môi trường theo tiêu chuẩn bảo mật |
| **Amazon GuardDuty** | Phát hiện mối đe dọa thông minh |
| **Amazon Inspector** | Quản lý lỗ hổng tự động |
| **Amazon Macie** | Phát hiện và phân loại dữ liệu nhạy cảm |
| **IAM Access Analyzer** | Xác định tài nguyên chia sẻ ngoài tài khoản |

AWS khuyến nghị nên bật **cả hai** dịch vụ Security Hub và Security Hub CSPM, cùng với GuardDuty, Inspector và Macie để có phạm vi bảo mật toàn diện nhất.

## Truy Cập Security Hub

Bạn có thể tương tác với Security Hub qua nhiều giao diện:

- **Console** — Giao diện web với dashboard và attack path graph
- **API** — Truy cập lập trình qua HTTPS
- **AWS CLI** — Quản lý dòng lệnh và scripting
- **AWS SDKs** — Thư viện cho C++, Go, Java, .NET và Python

## Tại Sao Điều Này Quan Trọng Cho Lab Của Tôi

Trong Security Operations Lab của tôi, Security Hub đóng vai trò là điểm tập trung trung tâm cho tất cả findings bảo mật. Khi tôi chạy GuardDuty Tester (được đề cập trong blog tiếp theo), những findings đó xuất hiện trong Security Hub cùng với kiểm tra tuân thủ từ CSPM và dữ liệu lỗ hổng từ Inspector.

## Bài Học Chính

AWS Security Hub biến các tín hiệu bảo mật rải rác thành một cái nhìn thống nhất, được ưu tiên về tư thế bảo mật đám mây của bạn.

**Tags:** `#AWS` `#SecurityHub` `#CloudSecurity` `#SIEM` `#FCAJ` `#AWSStudyGroup`
