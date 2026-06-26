---
title: "Workshop"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}


# AWS Security Operations & Hardening Lab

## Insecure-by-Design to Managed Remediation

### Tổng quan

Workshop này hướng dẫn cách xây dựng một môi trường AWS giả lập chứa các lỗi cấu hình sai phổ biến về bảo mật (Insecure Baseline). Sau đó, chúng ta sẽ cấu hình các dịch vụ giám sát tự động của AWS để phát hiện sự cố, tiến hành vá lỗi (Hardening) và đo lường sự thay đổi của điểm số tuân thủ (Compliance Score).

Workshop theo một vòng đời bảo mật hoàn chỉnh:

1. **Kích hoạt dịch vụ bảo mật** — Bật AWS CloudTrail, Amazon GuardDuty và AWS Security Hub để thiết lập ghi nhật ký và phát hiện mối đe dọa tập trung.
2. **Triển khai hạ tầng lỗi cấu hình** — Cố tình tạo các lỗ hổng bảo mật phổ biến (S3 public, IAM quyền hạn quá rộng, Security Group EC2 mở toàn cầu).
3. **Kiểm thử & Đo lường** — Quan sát cách Security Hub và GuardDuty gắn cờ các lỗi cấu hình và tạo cảnh báo.
4. **Gia cố & Khắc phục** — Áp dụng nguyên tắc đặc quyền tối thiểu và sửa từng lỗ hổng dựa trên khuyến nghị từ Security Hub.
5. **Tái thẩm định** — Xác nhận các cảnh báo chuyển từ Failed sang Passed và điểm số tuân thủ được cải thiện.
6. **Dọn dẹp tài nguyên** — Xóa tất cả tài nguyên trong lab để tránh phát sinh chi phí.

#### Nội dung

1. [Giới thiệu workshop](5.1-Workshop-overview/)
2. [Điều kiện tiên quyết](5.2-Prerequiste/)
3. [Sơ đồ kiến trúc](5.3-Architecture/)
4. [Bước 1: Kích hoạt dịch vụ bảo mật](5.4-Step1-Enable-Security/)
5. [Bước 2: Triển khai hạ tầng lỗi cấu hình](5.5-Step2-Deploy-Insecure/)
6. [Bước 3: Kiểm thử & Đo lường](5.6-Step3-Test-Validation/)
7. [Bước 4: Gia cố & Khắc phục](5.7-Step4-Hardening/)
8. [Bước 5: Tái thẩm định](5.8-Step5-Revalidation/)
9. [Bước 6: Dọn dẹp tài nguyên](5.9-Step6-Cleanup/)
10. [Bài học rút ra](5.10-Lessons-Learned/)