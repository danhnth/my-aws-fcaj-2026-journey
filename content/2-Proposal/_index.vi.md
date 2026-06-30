---
title: "Bản đề xuất"
date: 2026-06-26
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}

Tại phần này, bạn cần tóm tắt các nội dung trong workshop mà bạn **dự tính** sẽ làm.

# AWS Security Operations & Hardening Lab
## Insecure-by-Design to Managed Remediation

### 1. Tóm tắt điều hành
AWS Security Operations & Hardening Lab tiếp cận AWS Cloud qua góc nhìn của một **Kỹ sư Bảo mật Cloud (Cloud Security Engineer)**, thay vì chỉ đơn thuần triển khai các tài nguyên hoạt động. Mục tiêu cốt lõi là triển khai một môi trường cloud có kiểm soát nhưng cố tình chứa lỗ hổng ("Insecure-by-Design"), giám sát nó bằng các dịch vụ bảo mật gốc của AWS, và gia cố hệ thống một cách có hệ thống để đáp ứng các chuẩn mực bảo mật doanh nghiệp như **CIS AWS Foundations Benchmark**. Workshop thực hành này minh họa vòng đời bảo mật hoàn chỉnh: từ xác định các cấu hình sai, phát hiện mối đe dọa theo thời gian thực, thực thi chiến lược khắc phục, và xác thực tình trạng tuân thủ.

### 2. Tuyên bố vấn đề
#### Vấn đề hiện tại
Nhiều kỹ sư cloud có thể triển khai hạ tầng AWS nhưng thiếu kinh nghiệm thực tế trong **vận hành bảo mật cloud**. Có một khoảng cách đáng kể giữa việc vận hành tài nguyên cloud và bảo vệ chúng đúng cách. Các tổ chức thường gặp khó khăn với:
- Phát hiện sớm các cấu hình sai phổ biến (S3 bucket công khai, IAM role quá hạn, dữ liệu chưa mã hóa)
- Thiết lập ghi nhật ký và phát hiện mối đe dọa tập trung
- Hiểu về các khung tuân thủ và cách triển khai chúng
- Phản hồi và khắc phục các cảnh báo bảo mật theo thời gian thực

#### Giải pháp
Workshop này tạo ra một **phòng thí nghiệm vận hành bảo mật hoàn chỉnh** bằng cách cố tình triển khai hạ tầng AWS chứa lỗ hổng, sau đó gia cố hệ thống một cách có hệ thống. Người tham gia trải qua:
- **Hạ tầng lỗi cấu hình (Insecure Baseline)**: Các lỗ hổng phổ biến (S3 bucket public, IAM wildcard permissions, tài nguyên chưa mã hóa)
- **Giám sát & Phát hiện liên tục**: AWS CloudTrail, Amazon GuardDuty, và AWS Security Hub để phát hiện mối đe dọa tập trung
- **Gia cố & Khắc phục**: Áp dụng nguyên tắc đặc quyền tối thiểu và thực hiện các bước vá lỗi thực hành
- **Kiểm toán & Xác thực**: Đánh giá tuân thủ trước và sau khi gia cố bằng Security Hub

#### Lợi ích và kết quả học tập
Người tham gia có được **kinh nghiệm thực tế về vận hành bảo mật cloud** thông qua:
- Xác định và khắc phục lỗ hổng thực hành
- Hiểu về tích hợp các dịch vụ bảo mật gốc AWS
- Xác thực tuân thủ và đánh giá tình trạng bảo mật
- Các thực hành bảo mật tốt nhất có thể áp dụng lại cho môi trường sản xuất
- Nền tảng cho các vai trò bảo mật cloud nâng cao (Cloud Security Engineer, SecOps specialist)

### 3. Kiến trúc giải pháp
Kiến trúc phòng thí nghiệm của workshop tuân theo **vòng đời bảo mật hoàn chỉnh** với 6 bước tuần tự:

1. **Kích hoạt dịch vụ bảo mật**: Bật AWS CloudTrail, Amazon GuardDuty và AWS Security Hub để thiết lập ghi nhật ký và phát hiện mối đe dọa tập trung trước khi triển khai bất kỳ tài nguyên nào.
   - **AWS CloudTrail**: Ghi lại tất cả hoạt động API trên tài khoản AWS
   - **Amazon GuardDuty**: Phát hiện mối đe dọa bằng ML và thông tin tình báo
   - **AWS Security Hub**: Tập trung các cảnh báo bảo mật và kiểm tra tuân thủ

2. **Triển khai hạ tầng lỗi cấu hình**: Cố tình tạo các lỗ hổng bảo mật phổ biến
   - S3 bucket public không mã hóa
   - IAM role quá hạn với quyền wildcard
   - EC2 instance mở cổng SSH toàn cầu (0.0.0.0/0)

3. **Kiểm thử & Đo lường**: Quan sát cách Security Hub và GuardDuty phát hiện và gắn cờ các lỗi cấu hình
   - Xem xét các cảnh báo bảo mật được tạo trong Security Hub
   - Phân tích các cảnh báo phát hiện mối đe dọa từ GuardDuty
   - Ghi nhận baseline tuân thủ trước khi gia cố

4. **Gia cố & Khắc phục**: Sửa từng lỗ hổng dựa trên khuyến nghị từ Security Hub
   - Áp dụng nguyên tắc đặc quyền tối thiểu cho IAM policies
   - Bật mã hóa cho dữ liệu lưu trữ và truyền tải
   - Giới hạn truy cập mạng bằng Security Groups và Network ACLs
   - Bật MFA cho tài khoản người dùng

5. **Tái thẩm định**: Xác nhận các cảnh báo chuyển từ Failed sang Passed và điểm số tuân thủ được cải thiện
   - Đánh giá theo **CIS AWS Foundations Benchmark**
   - So sánh điểm số tuân thủ Security Hub trước và sau khi gia cố
   - Ghi lại các hành động khắc phục và kết quả

6. **Dọn dẹp tài nguyên**: Xóa tất cả tài nguyên trong lab để tránh phát sinh chi phí
   - Xóa EC2 instances và S3 buckets
   - Tắt CloudTrail, GuardDuty và Security Hub
   - Xác minh toàn bộ tài nguyên đã được xóa

#### Các dịch vụ AWS sử dụng
| Dịch vụ | Vai trò |
|---------|---------|
| **AWS CloudTrail** | Ghi nhật ký API tập trung và kiểm toán |
| **Amazon GuardDuty** | Phát hiện mối đe dọa bằng ML và thông tin tình báo |
| **AWS Security Hub** | Tập trung cảnh báo bảo mật và đánh giá tuân thủ |
| **Amazon S3** | Lưu trữ log CloudTrail và dữ liệu có thể bị lỗ hổng |
| **Amazon EC2** | Compute instances (với cấu hình sai ban đầu) |
| **AWS IAM** | Quản lý danh tính và truy cập (bao gồm role quá hạn) |
| **Amazon VPC** | Mạng (với kiểm soát bảo mật yếu ban đầu) |

#### Thành phần workshop
- **Hạ tầng lỗi cấu hình**: Môi trường AWS cơ bản với các lỗ hổng đã biết
- **Pipeline giám sát**: Tích hợp CloudTrail, GuardDuty và Security Hub
- **Sổ tay gia cố**: Hướng dẫn thực thi kỹ thuật từng bước
- **Đánh giá tuân thủ**: Báo cáo Security Hub trước và sau khi gia cố

### 4. Triển khai kỹ thuật
#### Phương pháp triển khai
Workshop được cấu trúc theo các bước tuần tự để xây dựng kiến thức bảo mật tiến bộ:

**Bước 1: Kích hoạt dịch vụ bảo mật (Tuần 1)**
- Bật AWS CloudTrail logging vào S3 để kiểm toán API tập trung
- Kích hoạt Amazon GuardDuty để phát hiện mối đe dọa
- Cấu hình AWS Security Hub làm bảng điều khiển bảo mật tập trung

**Bước 2: Triển khai hạ tầng lỗi cấu hình (Tuần 1-2)**
- Cung cấp hạ tầng AWS cơ bản với các cấu hình sai cố ý
- Tạo IAM role và policy quá hạn với quyền wildcard
- Bật S3 bucket public không mã hóa
- Thiết lập EC2 instance với Security Group quá thoáng (SSH mở 0.0.0.0/0)
- Ghi lại trạng thái lỗ hổng để so sánh sau này

**Bước 3: Kiểm thử & Đo lường (Tuần 2)**
- Xem xét các cảnh báo bảo mật được tạo trong Security Hub
- Phân tích các cảnh báo phát hiện mối đe dọa từ GuardDuty
- Ghi nhận baseline tuân thủ trước khi gia cố và điểm số Security Hub
- Lưu lại bằng chứng về các lỗi cấu hình để so sánh

**Bước 4: Gia cố & Khắc phục (Tuần 3-4)**
- Triển khai IAM đặc quyền tối thiểu (loại bỏ wildcard, thu hẹp quyền)
- Bật mã hóa trên S3 bucket và EBS volumes
- Giới hạn Security Groups EC2 chỉ cho phép các cổng cần thiết
- Bật MFA cho IAM users
- Triển khai VPC Flow Logs để giám sát mạng
- Xử lý từng cảnh báo từ Security Hub một cách có hệ thống

**Bước 5: Tái thẩm định (Tuần 4)**
- Xem xét điểm số tuân thủ Security Hub sau khi gia cố
- So sánh với baseline trước khi gia cố
- Xác nhận các cảnh báo chuyển từ Failed sang Passed
- Ghi lại tất cả các hành động khắc phục đã thực hiện

**Bước 6: Dọn dẹp tài nguyên (Tuần 5)**
- Xóa EC2 instances và S3 buckets
- Tắt CloudTrail, GuardDuty và Security Hub
- Xác minh toàn bộ tài nguyên đã được xóa để tránh phát sinh chi phí

#### Yêu cầu kỹ thuật
- Tài khoản AWS với quyền phù hợp (cho môi trường lab có kiểm soát)
- Kiến thức thực tế về AWS IAM, S3, EC2, VPC, CloudTrail, GuardDuty và Security Hub
- Quen thuộc với AWS Management Console và AWS CLI
- Hiểu về các khái niệm bảo mật cloud (đặc quyền tối thiểu, phòng thủ theo chiều sâu, CIS benchmarks)
- Khả năng đọc và diễn giải CloudTrail logs và Security Hub findings

### 5. Lộ trình & Mốc triển khai
#### Tiến độ dự án
- **Trước workshop (Tuần 0)**: Nghiên cứu các khái niệm bảo mật cloud và yêu cầu CIS benchmark
- **Thực hiện workshop (Tuần 1-5)**:
    - Tuần 1: Kích hoạt dịch vụ bảo mật (CloudTrail, GuardDuty, Security Hub)
    - Tuần 1-2: Triển khai hạ tầng lỗi cấu hình và chạy kiểm thử & đo lường
    - Tuần 3-4: Thực hiện gia cố và khắc phục
    - Tuần 4: Tái thẩm định điểm số tuân thủ
    - Tuần 5: Dọn dẹp tất cả tài nguyên lab
- **Sau workshop**: Tiếp tục truy cập lab để xem xét và các kịch bản bổ sung (tối đa 8 tuần)

#### Các sản phẩm bàn giao chính
- Tài liệu hạ tầng lỗi cấu hình baseline
- Báo cáo đánh giá Security Hub trước khi gia cố
- Sổ tay gia cố từng bước với các lệnh kỹ thuật
- Báo cáo đánh giá Security Hub sau khi gia cố
- So sánh tuân thủ và tóm tắt khắc phục

### 6. Ước tính ngân sách
#### Chi phí dịch vụ AWS (Thực hiện lab)
Các dịch vụ sau sẽ được sử dụng trong suốt 5 tuần workshop:

**Phân tích chi phí**
- **AWS CloudTrail**: ~2,50 USD (ghi log API calls trong 5 tuần)
- **Amazon GuardDuty**: ~30-40 USD (phát hiện mối đe dọa trong 5 tuần, ~6-8 USD/tuần)
- **AWS Security Hub**: ~30-40 USD (cảnh báo tập trung, ~6-8 USD/tuần)
- **Amazon S3**: ~1-2 USD (lưu trữ CloudTrail và log)
- **Amazon EC2**: ~5-10 USD (instance nhỏ trong 5 tuần)
- **AWS IAM**: Miễn phí
- **Amazon VPC**: Miễn phí

**Tổng chi phí ước tính**: 70-90 USD cho toàn bộ 5 tuần lab

**Ghi chú tối ưu chi phí**
- Tài nguyên lab được thiết kế tối thiểu để giữ chi phí thấp
- CloudTrail và GuardDuty là các dịch vụ thiết yếu cho mục tiêu học tập
- Có thể xóa tài nguyên ngay sau khi hoàn thành giai đoạn xác thực
- AWS Free Tier có thể giảm hoặc loại bỏ chi phí thực tế

**Lưu ý sau workshop**
- Cần dọn dẹp hạ tầng lab sau khi hoàn thành để tránh phát sinh chi phí
- Có thể lưu trữ CloudTrail logs vào Glacier để lưu trữ dài hạn với chi phí tối thiểu
- Có thể tạm ngưng Security Hub cho đến khi cần đánh giá bảo mật tiếp theo

### 7. Đánh giá rủi ro
#### Ma trận rủi ro

| Rủi ro | Tác động | Xác suất | Giảm thiểu |
|--------|----------|----------|------------|
| Tài khoản AWS bị xâm phạm | Cao | Thấp | Sử dụng tài khoản lab riêng, bật MFA, giám sát với GuardDuty |
| Vô tình xóa hạ tầng | Cao | Trung bình | Dùng AWS Config để theo dõi tài nguyên, bật termination protection |
| Chi phí vượt ngân sách | Trung bình | Thấp | Đặt cảnh báo AWS Budgets, theo dõi chi phí hàng ngày, giới hạn tài nguyên |
| Không đủ thời gian gia cố | Trung bình | Trung bình | Lên kế hoạch trước các bước khắc phục, ghi chú quy trình trước |
| Quá nhiều cảnh báo từ GuardDuty/Security Hub | Thấp | Cao | Lọc cảnh báo theo mức độ nghiêm trọng, tập trung vào critical/high trước |

#### Chiến lược giảm thiểu
- **Bảo mật tài khoản**: Sử dụng tài khoản AWS riêng cho lab, tách biệt với sản xuất
- **Quản lý tài nguyên**: Gắn thẻ (tag) tất cả tài nguyên để dễ nhận dạng và dọn dẹp
- **Giám sát**: Bật AWS Cost Explorer và đặt cảnh báo ngân sách ở mức 50 USD và 75 USD
- **Tài liệu**: Tạo runbook cho mỗi bước khắc phục trước khi workshop bắt đầu
- **Sao lưu**: Ghi nhận trạng thái baseline lỗ hổng để có thể tái tạo nếu cần

#### Kế hoạch dự phòng
- Nếu khối lượng cảnh báo quá lớn: Lọc Security Hub để chỉ hiển thị các cảnh báo critical trước
- Nếu thời gian không đủ: Ưu tiên khắc phục dựa trên các kiểm soát quan trọng của CIS benchmark
- Nếu chi phí vượt ngân sách: Xóa các tài nguyên không thiết yếu, lưu trữ log vào Glacier
- Nếu dịch vụ AWS không khả dụng: Sử dụng các cảnh báo đã ghi nhận trước để phân tích và lập kế hoạch khắc phục

### 8. Kết quả kỳ vọng
#### Kiến thức & Kỹ năng kỹ thuật
- Kinh nghiệm thực hành với các dịch vụ bảo mật AWS (CloudTrail, GuardDuty, Security Hub)
- Hiểu về các loại lỗi cấu hình bảo mật và tác động của chúng
- Thành thạo trong việc áp dụng nguyên tắc đặc quyền tối thiểu
- Khả năng đọc và hành động dựa trên các cảnh báo bảo mật
- Kinh nghiệm với các khung tuân thủ bảo mật (CIS AWS Foundations Benchmark)

#### Sản phẩm bàn giao cụ thể
- Tài liệu baseline lỗ hổng để tái lập lab
- Sổ tay gia cố hoàn chỉnh với các lệnh từng bước
- Báo cáo đánh giá tuân thủ trước và sau khi gia cố
- So sánh trực quan về cải thiện bảo mật
- Quy trình gia cố có thể tái sử dụng cho môi trường sản xuất

#### Tác động nghề nghiệp
- Nền tảng cho vai trò Cloud Security Engineer hoặc SecOps
- Kinh nghiệm thực tế với các công cụ và quy trình bảo mật doanh nghiệp
- Hiểu về các thách thức và giải pháp bảo mật cloud thực tế
- Dự án hoàn chỉnh để đưa vào portfolio thể hiện chuyên môn bảo mật
- Khuôn khổ cho các chủ đề bảo mật nâng cao (threat modeling, incident response, compliance automation)

#### Giá trị dài hạn
- Môi trường lab có thể tái sử dụng để đào tạo người khác về bảo mật cloud
- Các thực hành tốt nhất đã được ghi nhận có thể áp dụng cho hạ tầng tổ chức
- Khuôn khổ để đánh giá và cải thiện môi trường AWS hiện có
- Hạ tầng cơ bản cho các dự án bảo mật nâng cao (threat hunting, automation, policy as code)
