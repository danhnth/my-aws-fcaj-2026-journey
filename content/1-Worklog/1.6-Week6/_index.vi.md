---
title: "Worklog Tuần 6"
date: 2026-07-25
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Mục tiêu tuần 6:

* Nghiên cứu và hiểu về Amazon EKS Pod Identity và tính năng Session Policies.
* Viết blog kỹ thuật giải thích cách Session Policies thu hẹp IAM permissions cho từng pod riêng lẻ.
* Đăng tải blog lên cộng đồng AWS Study Group và chia sẻ kiến thức với các bạn học viên khác.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 (20/07) | - Nghiên cứu kiến trúc Amazon EKS Pod Identity <br>&emsp; + Hiểu cách Pod Identity ánh xạ IAM roles vào Kubernetes service accounts <br>&emsp; + So sánh với phương pháp IRSA (IAM Roles for Service Accounts) truyền thống <br> - Thiết lập EKS cluster thử nghiệm (nếu cần) để khám phá thực hành | 20/07/2026 | 20/07/2026 | <https://docs.aws.amazon.com/eks/latest/userguide/pod-identities.html> |
| 3 (21/07) | - Tìm hiểu sâu về Session Policies cho EKS Pod Identity <br>&emsp; + Học cách session policies giới hạn thêm permissions ở cấp pod <br>&emsp; + Hiểu các use cases: workloads đa tenant, đặc quyền tối thiểu cho từng pod <br>&emsp; + Xem xét các ví dụ IAM session policy documents | 21/07/2026 | 21/07/2026 | <https://docs.aws.amazon.com/eks/latest/userguide/eks-pod-identity-session-policies.html> |
| 4 (22/07) | - Viết bản nháp đầu tiên của blog kỹ thuật <br>&emsp; + Cấu trúc: giới thiệu, vấn đề, giải pháp, hướng dẫn từng bước <br>&emsp; + Bao gồm code snippets cho IAM roles, service accounts và session policies <br>&emsp; + Thêm sơ đồ kiến trúc giải thích luồng hoạt động | 22/07/2026 | 23/07/2026 | |
| 5 (23/07) | - Xem xét và hoàn thiện bản nháp blog <br>&emsp; + Xác minh độ chính xác kỹ thuật của tất cả lệnh AWS CLI và ví dụ IAM policy <br>&emsp; + Thêm ảnh chụp màn hình EKS console và cấu hình IAM <br>&emsp; + Soát lỗi chính tả và đảm bảo văn phong rõ ràng | 23/07/2026 | 24/07/2026 | |
| 6 (24/07) | - Xem xét lần cuối và đăng blog lên AWS Study Group <br>&emsp; + Định dạng bài viết cho nền tảng cộng đồng <br>&emsp; + Thêm tags và danh mục để dễ tìm kiếm <br>&emsp; + Chia sẻ link đã xuất bản với nhóm FCAJ để nhận phản hồi | 24/07/2026 | 24/07/2026 | <https://awsstudygroup.com/> |
| 7 (25/07) | - **Thực hành:** <br>&emsp; + Ghi chép các kiến thức kỹ thuật chính thu nhận được trong quá trình viết blog <br>&emsp; + Suy ngẫm về cách session policies so sánh với các cơ chế IAM isolation khác <br> - Xem xét tiến độ tuần 6 và chuẩn bị cho hội thảo tuần 7 | 25/07/2026 | 25/07/2026 | |

### Kết quả đạt được tuần 6:

* Nắm vững kiến thức về Amazon EKS Pod Identity — cách nó ánh xạ IAM roles vào Kubernetes service accounts ở cấp pod, và cách nó đơn giản hóa quy trình quản lý credentials so với phương pháp IRSA truyền thống.

* Làm chủ tính năng Session Policies cho EKS Pod Identity:
  * Hiểu cách session policies hoạt động như một ranh giới permission runtime, thu hẹp thêm quyền của IAM role cho từng pod riêng lẻ
  * Xác định các use cases chính: EKS clusters đa tenant nơi các pod khác nhau cần mức phân quyền khác nhau, và các kịch bản yêu cầu kiểm soát truy cập linh hoạt
  * Tạo các ví dụ session policy documents minh họa mẫu truy cập read-only và read-write

* Đã viết và xuất bản blog kỹ thuật về chủ đề này, bao gồm:
  * Động lực cho việc IAM isolation ở cấp pod trong Kubernetes
  * Hướng dẫn từng bước thiết lập EKS Pod Identity với session policies
  * Ví dụ code thực tế và sơ đồ kiến trúc
  * So sánh giữa IRSA và phương pháp Pod Identity mới

* Đã đăng blog lên nền tảng cộng đồng AWS Study Group và chia sẻ với nhóm FCAJ, nhận được phản hồi tích cực từ bạn học và người hướng dẫn.

* Củng cố kỹ năng viết kỹ thuật — học cách giải thích các khái niệm bảo mật AWS phức tạp một cách dễ hiểu cho cộng đồng cloud.
