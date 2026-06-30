---
title: "Worklog Tuần 3"
date: 2026-07-04
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---

### Mục tiêu tuần 3:

* Làm quen với Infrastructure as Code (IaC) sử dụng Terraform — khái niệm cốt lõi, cú pháp HCL và quản lý state.
* Lên kế hoạch kiến trúc dự án "Insecure-by-Design" và xác định các kịch bản misconfiguration.
* Thiết kế và viết các module Terraform cho hạ tầng cơ bản dễ bị tấn công.
* Bắt đầu triển khai các tài nguyên AWS đầu tiên được cấu hình sai có chủ đích.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 (29/06) | - Giới thiệu Terraform <br>&emsp; + IaC là gì? Tại sao Terraform? <br>&emsp; + Cú pháp HCL — resources, data sources, variables, outputs <br>&emsp; + Terraform workflow (init, plan, apply, destroy) <br> - Cài đặt Terraform và cấu hình AWS provider | 29/06/2026 | 29/06/2026 | <https://developer.hashicorp.com/terraform/docs> |
| 3 (30/06) | - Tìm hiểu quản lý state trong Terraform <br>&emsp; + Local vs remote state <br>&emsp; + State locking với DynamoDB <br> - Thiết lập S3 backend cho Terraform state <br> - Viết Terraform script đơn giản tạo S3 bucket và EC2 instance | 30/06/2026 | 30/06/2026 | <https://developer.hashicorp.com/terraform/language/state> |
| 4 (01/07) | - Thiết kế kiến trúc "Insecure-by-Design" <br> - Xác định các kịch bản misconfiguration cần triển khai: <br>&emsp; + Public S3 bucket chứa dữ liệu nhạy cảm <br>&emsp; + IAM role với quyền wildcard (*) quá mức <br>&emsp; + EC2 instance mở SSH public không giới hạn <br> - Định nghĩa cấu trúc thư mục dự án và bố trí module | 01/07/2026 | 01/07/2026 | |
| 5 (02/07) | - Viết Terraform modules cho hạ tầng cơ bản dễ bị tấn công: <br>&emsp; + Module: `vpc` — VPC cơ bản với public subnets <br>&emsp; + Module: `s3-vulnerable` — S3 bucket public với permissive bucket policy <br>&emsp; + Module: `iam-vulnerable` — IAM role với wildcard permissions | 02/07/2026 | 03/07/2026 | |
| 6 (03/07) | - Viết root module Terraform và kết nối các dependencies <br> - Tạo `terraform.tfvars` với cấu hình môi trường <br> - Chạy `terraform init` và `terraform plan` để xác thực cấu hình <br> - Xem lại các tài nguyên đã lên kế hoạch với mentor | 03/07/2026 | 03/07/2026 | |
| 7 (04/07) | - **Thực hành:** <br>&emsp; + Chạy `terraform apply` để triển khai hạ tầng dễ bị tấn công <br>&emsp; + Xác minh tài nguyên đã triển khai trong AWS Console <br>&emsp; + Kiểm tra khả năng truy cập public S3 bucket từ trình duyệt bên ngoài <br> - Ghi chép phát hiện ban đầu và lên kế hoạch tuần 4 | 04/07/2026 | 04/07/2026 | |

### Kết quả đạt được tuần 3:

* Nắm vững Terraform cơ bản — viết cấu hình HCL sử dụng resources, variables, outputs và data sources. Chạy thành công toàn bộ Terraform workflow (init, plan, apply, destroy) trên tài nguyên thử nghiệm.

* Thiết lập remote backend cho Terraform state sử dụng S3 bucket với DynamoDB state locking, cho phép cộng tác nhóm an toàn và lưu trữ state bền vững.

* Thiết kế kiến trúc dự án Insecure-by-Design bao gồm ba kịch bản misconfiguration chính: S3 bucket công khai, IAM role quá privilege và EC2 instance truy cập công khai.

* Cấu trúc dự án Terraform với các module tái sử dụng:
  * `modules/vpc/` — VPC cơ bản với public subnet, Internet Gateway và route table
  * `modules/s3-vulnerable/` — S3 bucket cấu hình bucket policy cho phép đọc công khai
  * `modules/iam-vulnerable/` — IAM role với `Action: "*"` và `Resource: "*"` (mô phỏng DevOps role quá privilege)
  * `modules/ec2-vulnerable/` — EC2 instance trong public subnet với SSH access từ 0.0.0.0/0

* Triển khai thành công hạ tầng dễ bị tấn công với `terraform apply` và xác minh:
  * S3 bucket có thể được list và đọc từ trình duyệt không phải AWS (mô phỏng góc nhìn attacker)
  * IAM role cho phép mọi hành động trên mọi tài nguyên (xác minh qua IAM Policy Simulator)
  * EC2 instance không giới hạn SSH inbound từ tất cả IP

* Ghi chép tình trạng bảo mật hiện tại và xác nhận rằng AWS Trusted Advisor và Security Hub (khi được bật) sẽ gắn cờ các phát hiện này là critical.

* Chuẩn bị nền tảng cho tuần 4 — triển khai thêm tài nguyên dễ bị tấn công và mở rộng phạm vi giám sát.
