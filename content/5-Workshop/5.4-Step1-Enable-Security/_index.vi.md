---
title : "Bước 1: Kích hoạt các dịch vụ Bảo mật"
date : 2026-06-29
weight : 4
chapter : false
pre : " <b> 5.4. </b> "
---

#### Bước 1: Kích hoạt các dịch vụ Giám sát và Bảo mật

Để hệ thống ghi nhận kịp thời các lỗ hổng, chúng ta cần bật nền tảng giám sát trước khi triển khai hạ tầng lỗi cấu hình.

**1. AWS CloudTrail**

CloudTrail ghi lại tất cả hoạt động API trong tài khoản AWS, cung cấp nhật ký kiểm toán để phân tích sau này.

1. Truy cập **CloudTrail** Console → Chọn **Create trail**.
2. Cấu hình:
   - **Tên Trail**: `FCAJ-Central-Trail`
   - **Nơi lưu trữ**: Tạo một S3 bucket mới (ví dụ: `fcaj-security-logs-<random-id>`)
   - Giữ nguyên các cài đặt mặc định khác.
3. Chọn **Create trail**.

{{%expand "AWS CLI Alternative" %}}
```bash
# 1. Tạo S3 bucket để lưu log CloudTrail
aws s3 mb s3://fcaj-security-logs-<random-id> --region ap-southeast-1

# 2. Tạo trail với xác thực log file
aws cloudtrail create-trail --name FCAJ-Central-Trail --s3-bucket-name fcaj-security-logs-<random-id> --is-multi-region-trail --enable-log-file-validation

# 3. Bắt đầu ghi log
aws cloudtrail start-logging --name FCAJ-Central-Trail
```
{{%/expand%}}

**2. Amazon GuardDuty**

GuardDuty sử dụng máy học (ML) và thông tin tình báo về mối đe dọa để phát hiện hành vi đáng ngờ.

1. Truy cập **GuardDuty** Console → Nhấn **Get Started**.
2. Nhấn **Enable GuardDuty** (không cần cấu hình thêm).
3. GuardDuty sẽ bắt đầu phân tích nhật ký trong vòng vài phút.

{{%expand "AWS CLI Alternative" %}}
```bash
# Kích hoạt GuardDuty (tạo detector)
aws guardduty create-detector --enable --region ap-southeast-1

# Kiểm tra trạng thái
aws guardduty list-detectors --region ap-southeast-1
```
{{%/expand%}}

**3. AWS Security Hub**

Security Hub cung cấp một giao diện tập trung cho các cảnh báo bảo mật và điểm số tuân thủ.

1. Truy cập **Security Hub** Console → Nhấn **Get started**.
2. Trong mục **Security capabilities**, chọn **Enable all capabilities** (hoặc **Customize capabilities** để chọn riêng).
3. Trong mục **Regions**, chọn **Enable all Regions** (hoặc **Enable specific Regions**).
4. (Tùy chọn) Thêm **Resource tags** nếu cần.
5. Nhấn **Enable Security Hub**.

{{%expand "AWS CLI Alternative" %}}
```bash
# Kích hoạt Security Hub với các tiêu chuẩn mặc định (bao gồm CIS Benchmark v1.4.0)
aws securityhub enable-security-hub --enable-default-standards --region ap-southeast-1

# Chờ 15-30 giây, sau đó kiểm tra các tiêu chuẩn đã được kích hoạt
aws securityhub get-enabled-standards --region ap-southeast-1
```
{{%/expand%}}

**4. Bật Tiêu chuẩn Bảo mật (Security Hub CSPM)**

Sau khi kích hoạt Security Hub, bạn cần bật tiêu chuẩn bảo mật cụ thể dùng trong workshop này.

1. Truy cập vào **Security Hub CSPM** (hoặc từ thanh điều hướng bên trái chọn **Security standards**).
2. Tìm **CIS AWS Foundations Benchmark v1.4.0**.
3. Nhấn **Enable standard**.
4. Tiêu chuẩn được kích hoạt ngay lập tức, nhưng **điểm bảo mật** chỉ được tính mỗi 24 giờ một lần. Cho đến khi điểm đầu tiên được tính, bạn sẽ thấy *"Unable to display security score: The score is still being generated."*
5. Công thức tính điểm: **Passed / (Passed + Failed)**, không bao gồm các control có trạng thái **No data**.

**5. AWS Config**

Trạng thái đăng ký Security Hub hiển thị `READY` ngay khi bạn bật tiêu chuẩn, nhưng quá trình đánh giá tuân thủ thực tế phụ thuộc vào **AWS Config** để ghi nhận liên tục trạng thái tài nguyên của bạn. Nếu không bật AWS Config, hầu hết các kiểm tra CIS benchmark sẽ hiển thị `NO_DATA` hoặc `NOT_RECORDED`.

1. Truy cập **AWS Config** Console → Nhấn **Get started**.
2. Trong mục **Recording options**, chọn **Record all resources** và bật **Include global resources** (ví dụ: IAM).
3. Trong mục **Delivery method**, tạo S3 bucket mới hoặc chọn bucket có sẵn.
4. Nhấn **Set up**.
5. Sau khi Config bắt đầu ghi nhận, Security Hub sẽ tự động đánh giá các quy tắc CIS benchmark và tạo ra các findings. Điểm bảo mật được cập nhật mỗi 24 giờ một lần.

{{%expand "AWS CLI Alternative" %}}
```bash
# 1. Tạo S3 bucket cho Config logs (tên bucket phải là duy nhất toàn cầu)
aws s3api create-bucket \
  --bucket config-bucket-<account-id>-ap-southeast-1 \
  --region ap-southeast-1 \
  --create-bucket-configuration LocationConstraint=ap-southeast-1

# 2. Tạo delivery channel trỏ đến bucket vừa tạo
aws configservice put-delivery-channel \
  --delivery-channel name=default,s3BucketName=config-bucket-<account-id>-ap-southeast-1 \
  --region ap-southeast-1

# 3. Tạo configuration recorder (sử dụng AWS-managed Config role)
aws configservice put-configuration-recorder \
  --configuration-recorder name=default,roleARN=arn:aws:iam::<account-id>:role/aws-service-role/config.amazonaws.com/AWSServiceRoleForConfig \
  --recording-group allSupported=true,includeGlobalResourceTypes=true \
  --region ap-southeast-1

# 4. Bắt đầu ghi nhận
aws configservice start-configuration-recorder \
  --configuration-recorder-name default \
  --region ap-southeast-1
```
{{%/expand%}}
