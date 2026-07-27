---
title: "Worklog Tuần 7"
date: 2026-08-01
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Mục tiêu tuần 7:

* Tham gia hội thảo GenAI-powered App-DB Modernization do AWS tổ chức.
* Tìm hiểu về Domain-Driven Design (DDD) và Event-Driven Architecture.
* Nắm được chiến lược hiện đại hóa ứng dụng và cơ sở dữ liệu trên AWS.
* Khám phá Amazon Q Developer như công cụ AI hỗ trợ vòng đời phát triển phần mềm.
* Củng cố kiến thức về Mô hình Shared Responsibility qua phổ tính toán (EC2 → ECS → Fargate → Lambda).

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 (27/07) | - Chuẩn bị trước hội thảo: <br>&emsp; + Xem chương trình hội thảo và các yêu cầu cần chuẩn bị <br>&emsp; + Đọc tài liệu nền tảng về Domain-Driven Design <br>&emsp; + Thiết lập môi trường AWS nếu cần | 27/07/2026 | 27/07/2026 | |
| 3 (28/07) | - Tham gia Ngày 1 của hội thảo GenAI-powered App-DB Modernization: <br>&emsp; + Domain-Driven Design (DDD) - strategic vs tactical design <br>&emsp; + Nguyên lý và mẫu hình Event-Driven Architecture <br>&emsp; + Chiến lược hiện đại hóa cho ứng dụng kế thừa | 28/07/2026 | 28/07/2026 | |
| 4 (29/07) | - Tham gia Ngày 2 của hội thảo: <br>&emsp; + Hiện đại hóa cơ sở dữ liệu - di chuyển từ monolithic sang purpose-built databases <br>&emsp; + Amazon Q Developer - trợ lý lập trình hỗ trợ AI <br>&emsp; + Mô hình Shared Responsibility qua phổ tính toán (EC2 → ECS → Fargate → Lambda) <br> - Tham gia các bài thực hành trong hội thảo | 29/07/2026 | 29/07/2026 | |
| 5 (30/07) | - Xem xét và tổng hợp kiến thức hội thảo: <br>&emsp; + Viết ghi chú chi tiết về các mẫu tactical DDD (entities, aggregates, domain events) <br>&emsp; + Ghi chép các mẫu Event-Driven Architecture (event sourcing, CQRS, saga) <br>&emsp; + Tóm tắt khả năng của Amazon Q Developer và các use cases | 30/07/2026 | 30/07/2026 | |
| 6 (31/07) | - Áp dụng kiến thức hội thảo: <br>&emsp; + Ánh xạ kiến trúc Security Operations Lab sang khái niệm DDD <br>&emsp; + Xác định các mẫu event-driven tiềm năng cho tự động hóa bảo mật <br>&emsp; + Khám phá cách Amazon Q Developer có thể hỗ trợ IaC templates và remediation scripts | 31/07/2026 | 31/07/2026 | |
| 7 (01/08) | - **Thực hành:** <br>&emsp; + Viết bài tóm tắt về hội thảo cho nhóm FCAJ <br>&emsp; + Suy ngẫm về cách phổ tính toán ảnh hưởng đến trách nhiệm bảo mật <br> - Xem xét tiến độ tuần 7 và chuẩn bị tài liệu cuối cùng cho tuần 8 | 01/08/2026 | 01/08/2026 | |

### Kết quả đạt được tuần 7:

* Đã tham gia thành công hội thảo GenAI-powered App-DB Modernization do AWS tổ chức, tiếp cận các mẫu kiến trúc phần mềm hiện đại và dịch vụ AI của AWS.

* Tiếp thu kiến thức nền tảng về Domain-Driven Design (DDD):
  * Hiểu sự khác biệt giữa strategic design (bounded contexts, ubiquitous language) và tactical design (entities, value objects, aggregates, domain events)
  * Học cách DDD giúp quản lý độ phức tạp trong hệ thống lớn qua ranh giới domain rõ ràng

* Nắm được các nguyên lý Event-Driven Architecture:
  * Event sourcing, CQRS (Command Query Responsibility Segregation) và Saga pattern cho distributed transactions
  * Cách hệ thống event-driven cải thiện khả năng mở rộng, chịu lỗi và tách rời giữa các services
  * Các dịch vụ AWS hỗ trợ kiến trúc event-driven (EventBridge, SQS, SNS, Lambda)

* Khám phá chiến lược hiện đại hóa cơ sở dữ liệu:
  * Lộ trình di chuyển từ cơ sở dữ liệu monolithic sang purpose-built databases (relational, key-value, document, graph)
  * Các dịch vụ cơ sở dữ liệu AWS và use cases tối ưu

* Có trải nghiệm thực hành với **Amazon Q Developer**:
  * Hiểu cách trợ lý lập trình AI tăng tốc vòng đời phát triển phần mềm
  * Khám phá khả năng sinh code, gỡ lỗi và đề xuất AWS best practices
  * Xác định ứng dụng tiềm năng cho tự động hóa bảo mật và tạo IaC templates

* Củng cố hiểu biết về **Mô hình Shared Responsibility qua phổ tính toán**:
  * Trách nhiệm khách hàng giảm dần khi di chuyển từ EC2 (nhiều kiểm soát, nhiều trách nhiệm) đến Lambda (ít kiểm soát, ít trách nhiệm)
  * Hệ quả cho tư thế bảo mật khi chọn các dịch vụ compute khác nhau
  * Ví dụ thực tế: gánh nặng vá lỗi trên EC2 so với Fargate được quản lý so với Lambda serverless

* Đã chia sẻ kiến thức hội thảo với nhóm FCAJ qua bài viết tóm tắt, củng cố kiến thức thông qua giảng dạy lại.
