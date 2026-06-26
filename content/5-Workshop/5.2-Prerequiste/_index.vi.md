---
title : "Điều kiện tiên quyết"
date : 2026-06-26
weight : 2
chapter : false
pre : " <b> 5.2. </b> "
---

#### Điều kiện tiên quyết

Trước khi bắt đầu workshop, hãy đảm bảo bạn có những điều sau:

1. **Tài khoản AWS** — Một tài khoản AWS hợp lệ có quyền quản trị. Nên sử dụng tài khoản mới hoặc tài khoản Sandbox AWS Free Tier để tránh ảnh hưởng đến môi trường sản xuất.

2. **Quyền AdministratorAccess** — IAM user hoặc role của bạn phải có managed policy `AdministratorAccess` (hoặc quyền tương đương) để kích hoạt và cấu hình các dịch vụ bảo mật.

3. **AWS CLI** — AWS Command Line Interface đã được cài đặt và cấu hình trên máy local. [Hướng dẫn cài đặt](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)

4. **Region mặc định** — Đặt region mặc định thành **Singapore (ap-southeast-1)** để đồng nhất với workshop này.

   ```bash
   aws configure set region ap-southeast-1
   ```

5. **Kiến thức AWS cơ bản** — Làm quen với AWS Management Console, IAM, S3, EC2 và các khái niệm mạng cơ bản sẽ hữu ích nhưng không bắt buộc.