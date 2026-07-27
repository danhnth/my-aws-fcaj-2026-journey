---
title: "Blog 2"
date: 2026-07-22
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

# Amazon GuardDuty Tester - Công Cụ Mới Kiểm Tra Phát Hiện Bảo Mật AWS

## Amazon GuardDuty Tester Là Gì?

**Amazon GuardDuty Tester** là công cụ mã nguồn mở từ AWS Labs, mô phỏng các kịch bản tấn công thực tế trong tài khoản AWS của bạn. Công cụ này tạo ra các GuardDuty findings thật để bạn xác nhận pipeline phát hiện mối đe dọa hoạt động đúng cách.

Thay vì chờ một sự cố bảo mật thực sự để kiểm tra khả năng phát hiện, bạn có thể chạy công cụ này và thấy findings xuất hiện trong GuardDuty và Security Hub chỉ trong vài phút.

## Tại Sao Tôi Sử Dụng Nó

Trong Security Operations Lab, tôi đã bật GuardDuty, CloudTrail và Security Hub - nhưng không có cách nào xác nhận chúng thực sự phát hiện mối đe dọa. Các tài nguyên dễ tổn thương như S3 bucket công khai sẽ không kích hoạt cảnh báo nếu chỉ nằm im. Tôi cần mô phỏng kẻ tấn công tương tác với chúng, và GuardDuty Tester làm chính xác điều đó.

## Cách Hoạt Động

Công cụ triển khai các Lambda functions qua AWS CDK để thực hiện các hoạt động độc hại mô phỏng - quét cổng, lạm dụng credential, DNS query đào crypto, v.v. Mô hình ML của GuardDuty phân tích các hoạt động này và tạo findings trên sáu nhóm:

- **Recon** - Quét cổng, dò DNS, liệt kê API
- **UnauthorizedAccess** - Lạm dụng credential, SSH brute force
- **Impact** - Xóa tài nguyên, kết thúc EC2
- **CryptoCurrency** - DNS query đến mining pool
- **Policy** - Vi phạm IAM policy, vượt S3 public access
- **Trojan** - C2 communication, reverse shell

Chạy `guardduty_tester.py --all` tạo ra hơn 50 findings trong khoảng 15 phút - xác nhận hoàn chỉnh hệ thống phát hiện của tôi.

## Bài Học Chính

GuardDuty Tester biến một hệ thống giám sát thụ động thành pipeline phát hiện được xác nhận chủ động. Bạn chuyển từ *hy vọng* các dịch vụ bảo mật hoạt động sang *biết chắc* chúng hoạt động.

**Tags:** `#AWS` `#GuardDuty` `#SecurityTesting` `#CloudSecurity` `#FCAJ` `#AWSStudyGroup`
