---
title: "Blog 3"
date: 2026-07-22
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# Sử Dụng Amazon GuardDuty Tester Để Tự Động Hóa Kiểm Thử Bảo Mật

## Vấn Đề

Sau khi triển khai hạ tầng AWS, làm thế nào để biết hệ thống giám sát bảo mật thực sự hoạt động? Kiểm tra thủ công thì chậm và dễ bỏ sót. Chờ một cuộc tấn công thực sự thì quá nguy hiểm. Bạn cần một cách để **tự động xác nhận** GuardDuty, Security Hub và quy trình incident response hoạt động chính xác.

GuardDuty Tester giải quyết vấn đề này.

## Triển Khai

Triển khai đơn giản với AWS CDK:

```bash
git clone https://github.com/awslabs/amazon-guardduty-tester.git
cd amazon-guardduty-tester/cdk
cdk bootstrap
cdk deploy
```

CDK stack tạo hạ tầng cần thiết để mô phỏng tấn công - Lambda functions cho mô phỏng cấp API và EC2 instances tùy chọn cho kịch bản cấp mạng. Toàn bộ quá trình mất khoảng 10 phút.

## Chạy Kiểm Thử

Sau khi triển khai, dùng Python CLI để chạy tests:

```bash
# Chạy tất cả nhóm
python3 guardduty_tester.py --all --region us-east-1

# Hoặc chạy một nhóm
python3 guardduty_tester.py --test-type Recon --region us-east-1
```

Findings xuất hiện trong GuardDuty sau 5-15 phút. Nếu đã bật Security Hub, chúng cũng xuất hiện ở đó cùng với kiểm tra tuân thủ.

## Cách Tôi Sử Dụng Trong Lab

Tôi chạy GuardDuty Tester trong ba giai đoạn:

1. **Trước hardening** - Thiết lập baseline với 52 findings trên sáu nhóm
2. **Sau khi áp dụng bản sửa** - Chạy lại và thấy findings Critical/High giảm
3. **Xác nhận** - Xác nhận các bản sửa (chặn public S3, giới hạn IAM, khóa SSH) thay đổi kết quả phát hiện

## Bài Học Chính

GuardDuty Tester cho phép **tự động hóa việc xác nhận pipeline phát hiện bảo mật**. Một lệnh chạy toàn bộ suite và bạn có xác nhận ngay rằng hệ thống giám sát hoạt động như mong đợi.

**Tags:** `#AWS` `#GuardDuty` `#Automation` `#SecurityTesting` `#CloudSecurity` `#FCAJ` `#AWSStudyGroup`
