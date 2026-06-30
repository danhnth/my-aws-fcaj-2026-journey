---
title: "Worklog Tuần 2"
date: 2026-06-27
weight: 1
chapter: false
pre: " <b> 1.2. </b> "
---

### Mục tiêu tuần 2:

* Hiểu sâu về AWS Identity and Access Management (IAM) — users, groups, roles, policies và nguyên tắc đặc quyền tối thiểu.
* Tìm hiểu về bảo mật S3 — bucket policies, ACLs, cài đặt public access và mã hóa.
* Khám phá các khái niệm VPC — subnets, route tables, Internet Gateway, NAT Gateway và các phương pháp bảo mật.
* Làm quen với CloudTrail để ghi log và giám sát hoạt động API.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 (22/06) | - Tìm hiểu sâu về IAM <br>&emsp; + Users, Groups, Roles, Policies <br>&emsp; + Managed vs Inline policies <br>&emsp; + IAM Policy Simulator <br> - Tạo IAM users với các mức phân quyền khác nhau | 22/06/2026 | 22/06/2026 | <https://docs.aws.amazon.com/IAM/> |
| 3 (23/06) | - Tìm hiểu IAM Roles và trust policies <br> - Thực hành: truy cập cross-account với IAM Roles <br> - Hiểu IAM best practices (least privilege, password policies, key rotation) | 23/06/2026 | 23/06/2026 | <https://docs.aws.amazon.com/IAM/> |
| 4 (24/06) | - Tìm hiểu Amazon S3 chuyên sâu <br>&emsp; + Bucket policies vs ACLs <br>&emsp; + Block Public Access settings <br>&emsp; + Server-side encryption (SSE-S3, SSE-KMS, SSE-C) <br> - Thực hành: tạo S3 buckets public vs private | 24/06/2026 | 24/06/2026 | <https://docs.aws.amazon.com/s3/> |
| 5 (25/06) | - Tìm hiểu VPC cơ bản <br>&emsp; + VPC, Subnets (public/private) <br>&emsp; + Route Tables, Internet Gateway <br>&emsp; + NAT Gateway, Security Groups, NACLs <br> - Tạo EC2 instances trong public và private subnets | 25/06/2026 | 26/06/2026 | <https://docs.aws.amazon.com/vpc/> |
| 6 (26/06) | - Giới thiệu AWS CloudTrail <br>&emsp; + CloudTrail là gì? (management vs data events) <br>&emsp; + Tạo trail và ghi log vào S3 <br>&emsp; + CloudTrail Insights <br> - Xem lại CloudTrail logs trong Console | 26/06/2026 | 26/06/2026 | <https://docs.aws.amazon.com/cloudtrail/> |
| 7 (27/06) | - **Thực hành:** <br>&emsp; + Kết hợp IAM + S3 + VPC trong một mini-lab <br>&emsp; + Cấu hình VPC Flow Logs để giám sát mạng <br> - Ôn tập và ghi chép kiến thức tuần 2 | 27/06/2026 | 27/06/2026 | |

### Kết quả đạt được tuần 2:

* Nắm vững kiến thức về IAM — tạo users với phân quyền chi tiết, thiết lập groups với managed policies, và kiểm tra access boundaries bằng IAM Policy Simulator.

* Hiểu sự khác biệt giữa IAM Roles và Users, và thực hành giả định role cross-account.

* Áp dụng IAM best practices: thiết lập chính sách mật khẩu mạnh, luân chuyển access keys, và xóa credentials không sử dụng.

* Thành thạo các kiểm soát bảo mật S3:
  * Chặn truy cập public ở cấp tài khoản và bucket
  * Cấu hình bucket policies cho truy cập dựa trên IP và role
  * Bật SSE-S3 encryption trên tất cả các bucket
  * Kiểm tra các nỗ lực truy cập public để xác minh Block Public Access

* Xây dựng VPC tùy chỉnh từ đầu với:
  * Public và private subnets qua hai Availability Zones
  * Internet Gateway cho truy cập public subnet
  * NAT Gateway cho kết nối ra ngoài từ private subnet
  * Security Groups với quy tắc đặc quyền tối thiểu và Network ACLs cho lọc ở cấp subnet

* Tạo EC2 instances trong cả public và private subnets để xác minh kết nối (SSH vào public instance, private instance ra ngoài qua NAT).

* Thiết lập AWS CloudTrail với trail chỉ ghi management events vào S3 bucket, và khám phá CloudTrail event history để hiểu cách ghi lại hoạt động API.

* Cấu hình VPC Flow Logs và phân tích các mẫu log entry để hiểu các mẫu lưu lượng được phép/từ chối.
