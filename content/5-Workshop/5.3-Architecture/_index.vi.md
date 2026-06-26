---
title : "Kiến trúc"
date : 2026-06-26 
weight : 3
chapter : false
pre : " <b> 5.3. </b> "
---

#### Sơ đồ kiến trúc

Luồng dữ liệu và phát hiện bảo mật trong workshop được mô tả như sau:

```text
[User/Attacker] ──(Cấu hình sai)──> [ EC2 / S3 Bucket / IAM Role ]
                                              │
                                        (Ghi nhận Log)
                                              ▼
                                       [ AWS CloudTrail ]
                                              │
                                        (Phân tích hành vi)
                                              ▼
                                      [ Amazon GuardDuty ]
                                              │
                                        (Tổng hợp & Chấm điểm)
                                              ▼
                                      [ AWS Security Hub ]
```

#### Giải thích luồng kiến trúc

1. **Lỗ hổng đầu vào** — Kẻ tấn công hoặc người dùng khai thác các cấu hình sai trên EC2, S3, hoặc IAM (ví dụ: S3 public, SSH mở toàn cầu, IAM policy `*/*`).
2. **Ghi nhận** — AWS CloudTrail ghi lại tất cả các API calls, bao gồm cả những hành động độc hại hoặc trái phép.
3. **Phát hiện** — Amazon GuardDuty phân tích hành vi và nhật ký để phát hiện các mối đe dọa và bất thường.
4. **Tổng hợp & Đánh giá** — AWS Security Hub tổng hợp các phát hiện từ GuardDuty và tự động chấm điểm tuân thủ dựa trên CIS AWS Foundations Benchmark.

#### Các dịch vụ AWS sử dụng

| Dịch vụ | Vai trò |
|---------|---------|
| **AWS CloudTrail** | Ghi nhật ký API tập trung và kiểm toán |
| **Amazon GuardDuty** | Phát hiện mối đe dọa bằng ML và thông tin tình báo |
| **AWS Security Hub** | Tổng hợp phát hiện bảo mật và đánh giá tuân thủ |
| **Amazon S3** | Lưu trữ log CloudTrail và dữ liệu có thể bị lỗ hổng |
| **Amazon EC2** | Compute instances (với cấu hình sai ban đầu) |
| **AWS IAM** | Quản lý danh tính và truy cập (bao gồm role quá hạn) |