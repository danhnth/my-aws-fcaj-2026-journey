---
title: "Worklog Tuần 7"
date: 2026-08-01
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Mục tiêu tuần 7:

* Tham gia Agentic AI Build Week (AABW) — hackathon xây dựng ứng dụng Agentic AI trên nền tảng AWS.
* Tìm hiểu về Amazon Bedrock AgentCore, Strands Agent và hệ sinh thái agentic AI trên AWS.
* Nắm được kiến trúc agentic AI thực tế từ ba đội thi (S.H.E.P.H.E.R.D, Signal Scout, SA Professional Native App).
* Học hỏi về tư duy sản phẩm, ước tính chi phí và scoping cho ứng dụng AI trong điều kiện thời gian hạn chế.
* Viết bài thu hoạch sự kiện AABW cho hồ sơ thực tập FCAJ.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 (27/07) | - Tìm hiểu kiến thức nền tảng về Agentic AI trên AWS: <br>&emsp; + Amazon Bedrock AgentCore và Strands Agent <br>&emsp; + Các mẫu agentic: autonomous monitoring, copilot interfaces <br>&emsp; + Xem chương trình AABW và danh sách đội tham gia | 27/07/2026 | 27/07/2026 | <https://aws.amazon.com/bedrock/agent/> |
| 3 (28/07) | - Tham gia ngày demo AABW tại tòa nhà Bitexco: <br>&emsp; + Xem các đội trình bày sản phẩm (S.H.E.P.H.E.R.D, Signal Scout, SA Pro) <br>&emsp; + Học hỏi về quyết định kiến trúc và đánh đổi chi phí <br>&emsp; + Kết nối với người tham dự và diễn giả AWS | 28/07/2026 | 28/07/2026 | <4.1-Event1/> |
| 4 (29/07) | - Phân tích sâu kiến trúc ba sản phẩm: <br>&emsp; + S.H.E.P.H.E.R.D - thị giác máy tính thời gian thực + agentic AI cho giám sát đám đông <br>&emsp; + Signal Scout - phát hiện sớm thay đổi chiến lược doanh nghiệp <br>&emsp; + SA Professional Native App - trợ lý AI cho Solution Architect <br> - Ghi chép các mẫu kiến trúc và lựa chọn công nghệ chính | 29/07/2026 | 29/07/2026 | |
| 5 (30/07) | - Tổng hợp kiến thức từ AABW: <br>&emsp; + Viết ghi chú chi tiết về các mẫu agentic AI (Autonomous Monitor, Operator Copilot) <br>&emsp; + Tóm tắt mô hình chi phí và nguyên tắc thiết kế được các đội chia sẻ <br>&emsp; + Ghi lại các bài học về tư duy sản phẩm và cộng tác nhóm | 30/07/2026 | 30/07/2026 | |
| 6 (31/07) | - Áp dụng bài học AABW vào Security Operations Lab: <br>&emsp; + Khám phá cách agentic patterns có thể nâng cao giám sát bảo mật <br>&emsp; + Xem xét quy trình phát hiện và phản ứng sự cố tự động <br>&emsp; + Đánh giá ứng dụng AI hỗ trợ tài liệu và vẽ sơ đồ cho workshop | 31/07/2026 | 31/07/2026 | <../5-Workshop/> |
| 7 (01/08) | - **Thực hành:** <br>&emsp; + Viết bài thu hoạch AABW cho hồ sơ thực tập FCAJ <br>&emsp; + Suy ngẫm về sự khác biệt giữa agentic AI và tự động hóa truyền thống <br> - Xem xét tiến độ tuần 7 và chuẩn bị tài liệu cuối cùng cho tuần 8 | 01/08/2026 | 01/08/2026 | |

### Kết quả đạt được tuần 7:

* Đã tham gia thành công **Agentic AI Build Week (AABW)** tại AWS Event Hall, tòa nhà Bitexco, trải nghiệm cách các đội xây dựng ứng dụng Agentic AI end-to-end trên AWS trong vòng 24 giờ.

* Tiếp thu kiến thức thực tế về **Amazon Bedrock AgentCore và Strands Agent** — các dịch vụ AWS cốt lõi để xây dựng agent tự động có khả năng chủ động theo dõi, phân tích và cảnh báo thay vì chỉ phản hồi khi được yêu cầu.

* Nghiên cứu chi tiết ba kiến trúc sản phẩm khác nhau:

  * **S.H.E.P.H.E.R.D** — hệ thống giám sát đám đông thời gian thực kết hợp YOLO + ByteTrack (thị giác máy tính), Amazon SageMaker (inference trên cloud) và hai lớp agentic AI: *Autonomous Monitor* liên tục theo dõi chỉ số và tự tạo cảnh báo chủ động, và *Operator Copilot* cho phép nhân viên hỏi bằng ngôn ngữ tự nhiên dựa trên số liệu trực tiếp.

  * **Signal Scout** — hệ thống phát hiện sớm tín hiệu thay đổi chiến lược doanh nghiệp, sử dụng Amazon Bedrock, Lambda, DynamoDB, API Gateway và tổng hợp thông tin tình báo đa nguồn. Đội đã trình bày bảng bóc tách chi phí theo từng dịch vụ cho ba kịch bản (chỉ AWS khoảng 17-130 USD/tháng), cho thấy việc ước tính chi phí phải là một phần của thiết kế ngay từ đầu.

  * **SA Professional Native App** — trợ lý AI tự động hóa bốn công việc tốn thời gian nhất của Solution Architect: trích xuất yêu cầu từ tài liệu BRD/PRD, phác thảo kiến trúc high-level, sinh sơ đồ Draw.io với AWS Architecture Icons chính thức và ước tính chi phí AWS cho vùng *ap-southeast-1*.

* Học được về **tư duy sản phẩm**: bắt đầu từ nỗi đau vận hành thực tế thay vì từ công nghệ, giữ phạm vi nhỏ và làm cho xong, và luôn để con người giữ quyền quyết định cuối cùng dựa trên các khuyến nghị AI có bằng chứng.

* Học được về **cộng tác nhóm hiệu quả**: phân vai rõ ràng từ đầu, luyện demo trước để kể câu chuyện trong 3 phút, và chuẩn bị template khởi tạo sẵn để tối đa thời gian xây dựng.

* Hiểu được tầm quan trọng của **ước tính chi phí ngay từ đầu** — mọi đội đều trình bày bảng chi phí theo từng dịch vụ với các kịch bản min/mid/max như một phần bắt buộc của kiến trúc.

* Đã viết bài thu hoạch sự kiện AABW cho hồ sơ thực tập FCAJ, ghi chép cả ba kiến trúc sản phẩm, bài học chính và cách trải nghiệm này kết nối với công việc vận hành bảo mật tổng thể.
