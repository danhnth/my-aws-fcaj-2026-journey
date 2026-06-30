---
title: "Worklog Tuần 1"
date: 2026-06-25
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Mục tiêu tuần 1:

* Làm quen với các thành viên FCAJ, người hướng dẫn và cấu trúc chương trình.
* Hiểu nội quy thực tập, quy định và yêu cầu báo cáo.
* Tìm hiểu những kiến thức cơ bản về AWS — hạ tầng toàn cầu, các nhóm dịch vụ chính, và mô hình Shared Responsibility.
* Thiết lập tài khoản AWS Free Tier, AWS Management Console và AWS CLI.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 (15/06) | - Định hướng & giới thiệu chương trình FCAJ <br> - Gặp mentor và các thành viên trong nhóm <br> - Đọc nội quy và quy định thực tập | 15/06/2026 | 15/06/2026 | |
| 3 (16/06) | - Học các khái niệm AWS cơ bản <br>&emsp; + Hạ tầng toàn cầu (Regions, AZs, Edge locations) <br>&emsp; + Mô hình Shared Responsibility <br>&emsp; + Các nhóm dịch vụ chính <br> - Xem lộ trình học tập FCAJ Cloud Journey | 16/06/2026 | 16/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 (17/06) | - Tạo tài khoản AWS Free Tier <br> - Khám phá AWS Management Console <br> - Thiết lập billing alerts và MFA cho root account | 17/06/2026 | 17/06/2026 | <https://aws.amazon.com/free/> |
| 5 (18/06) | - Cài đặt & cấu hình AWS CLI <br>&emsp; + Tạo IAM user & Access Key <br>&emsp; + Cấu hình region mặc định và output format <br> - Thực hành các lệnh AWS CLI cơ bản | 18/06/2026 | 18/06/2026 | <https://docs.aws.amazon.com/cli/> |
| 6 (19/06) | - Tìm hiểu EC2 cơ bản <br>&emsp; + Instance types, AMI, EBS <br>&emsp; + Security Groups, Key Pairs <br>&emsp; + Các phương thức kết nối SSH <br> - Tạo EC2 instance t2.micro và kết nối SSH | 19/06/2026 | 20/06/2026 | <https://docs.aws.amazon.com/ec2/> |
| 7 (20/06) | - **Thực hành:** <br>&emsp; + Tạo và xóa EC2 instances <br>&emsp; + Gắn/tháo EBS volumes <br>&emsp; + Cấu hình Security Group rules <br> - Ôn tập và ghi chép lại kiến thức tuần 1 | 20/06/2026 | 20/06/2026 | |

### Kết quả đạt được tuần 1:

* Nắm vững kiến thức về hạ tầng toàn cầu của AWS và mô hình Shared Responsibility.

* Tạo và bảo mật tài khoản AWS Free Tier thành công với MFA và billing alerts.

* Thành thạo AWS Management Console — điều hướng dịch vụ, tìm tài nguyên và hiểu bảng điều khiển.

* Cài đặt và cấu hình AWS CLI với IAM credentials phù hợp, bao gồm:
  * Thiết lập Access Key & Secret Key
  * Region mặc định và output format (JSON)
  * Named profiles cho nhiều môi trường

* Sử dụng AWS CLI để thực hiện các thao tác cơ bản:
  * Kiểm tra danh tính (`aws sts get-caller-identity`)
  * Liệt kê regions (`aws ec2 describe-regions`)
  * Mô tả EC2 instances và key pairs
  * Tạo và quản lý S3 buckets qua CLI

* Đã tạo một EC2 instance (t2.micro, Amazon Linux 2), kết nối SSH và gắn thêm một EBS volume.

* Hiểu sự khác biệt giữa ephemeral và persistent storage, và cách Security Groups hoạt động như tường lửa ảo.

* Đã thiết lập nền tảng cho các tuần tiếp theo — tài khoản AWS sẵn sàng, CLI đã cấu hình, và các khái niệm compute/storage/networking cơ bản đã nắm vững.
