---
title: "Tự đánh giá"
date: 2026-07-26
weight: 6
chapter: false
pre: " <b> 6. </b> "
---

Trong suốt thời gian thực tập tại **Công ty TNHH Amazon Web Services Việt Nam** - chương trình **Workforce Bootcamp: First Cloud AI Journey (FCAJ)** - từ **15/06/2026** đến **14/08/2026**, tôi đã có cơ hội chuyển từ kiến thức thuần lý thuyết ở trường sang quy trình làm việc thực tế của một kỹ sư cloud, thao tác trực tiếp trên tài khoản AWS thật tại region `ap-southeast-1`.

Sản phẩm chính của tôi là workshop **"AWS Security Operations & Hardening Lab: Insecure-by-Design to Managed Remediation"**. Tôi đã dựng một môi trường cố tình chứa lỗ hổng (S3 bucket public, IAM user gắn policy `WildcardFullAccess`, EC2 instance mở SSH ra `0.0.0.0/0`), đưa môi trường đó vào giám sát liên tục bằng **CloudTrail**, **GuardDuty**, **AWS Config** và **Security Hub** với chuẩn **CIS AWS Foundations Benchmark v1.4.0**, sau đó khắc phục và chứng minh mức cải thiện. Cả ba control mục tiêu - **S3.2**, **IAM.1** và **EC2.19** - đều chuyển từ **FAILED** sang **PASSED**. Song song đó, tôi triển khai **Amazon GuardDuty Tester** bằng **AWS CDK** và phân tích **hơn 50 loại finding** thuộc sáu nhóm của GuardDuty (Recon, UnauthorizedAccess, Impact, CryptoCurrency, Policy, Trojan).

Ngoài phần lab, tôi đã đăng các bài blog kỹ thuật trên cộng đồng **AWS Study Group** về **AWS Security Hub** và **Amazon GuardDuty Tester** (cả hai được liệt kê tại [3-BlogsPosted](../3-BlogsPosted/)); đồng thời tham dự **Agentic AI Build Week (AABW)** — hackathon tại AWS Event Hall ở tòa nhà Bitexco, nơi các đội xây dựng ứng dụng agentic AI sử dụng Amazon Bedrock AgentCore, Strands Agent và SageMaker, trình bày ba sản phẩm hoạt động được (S.H.E.P.H.E.R.D, Signal Scout, SA Professional Native App) kèm kiến trúc và bảng chi phí chi tiết.

Qua quá trình này, tôi đã cải thiện các kỹ năng về **vận hành bảo mật trên cloud, thiết kế IAM theo nguyên tắc least privilege, networking với VPC, sử dụng AWS CLI, triển khai hạ tầng bằng CDK, kiểm toán tuân thủ theo CIS và viết tài liệu kỹ thuật song ngữ**.

Về tác phong, tôi duy trì worklog hằng ngày trong suốt tám tuần, hoàn thành đúng tiến độ từng giai đoạn của dự án, kiểm chứng mọi thay đổi bằng bằng chứng cụ thể (output CLI và ảnh chụp console) thay vì phỏng đoán, và dọn dẹp toàn bộ tài nguyên tính phí sau khi kết thúc lab.

Để phản ánh một cách khách quan quá trình thực tập, tôi xin tự đánh giá bản thân dựa trên các tiêu chí dưới đây:

| STT | Tiêu chí                            | Mô tả                                                                                            | Tốt | Khá | Trung bình |
| --- | ----------------------------------- | ------------------------------------------------------------------------------------------------ | --- | --- | ---------- |
| 1   | **Kiến thức và kỹ năng chuyên môn** | Hiểu biết về ngành, áp dụng kiến thức vào thực tế, kỹ năng sử dụng công cụ, chất lượng công việc | X   | -   | -          |
| 2   | **Khả năng học hỏi**                | Tiếp thu kiến thức mới, học hỏi nhanh                                                            | X   | -   | -          |
| 3   | **Chủ động**                        | Tự tìm hiểu, nhận nhiệm vụ mà không chờ chỉ dẫn                                                  | X   | -   | -          |
| 4   | **Tinh thần trách nhiệm**           | Hoàn thành công việc đúng hạn, đảm bảo chất lượng                                                | X   | -   | -          |
| 5   | **Kỷ luật**                         | Tuân thủ giờ giấc, nội quy, quy trình làm việc                                                   | -   | X   | -          |
| 6   | **Tính cầu tiến**                   | Sẵn sàng nhận feedback và cải thiện bản thân                                                     | X   | -   | -          |
| 7   | **Giao tiếp**                       | Trình bày ý tưởng, báo cáo công việc rõ ràng                                                     | -   | X   | -          |
| 8   | **Hợp tác nhóm**                    | Làm việc hiệu quả với đồng nghiệp, tham gia nhóm                                                 | -   | X   | -          |
| 9   | **Ứng xử chuyên nghiệp**            | Tôn trọng đồng nghiệp, đối tác, môi trường làm việc                                              | X   | -   | -          |
| 10  | **Tư duy giải quyết vấn đề**        | Nhận diện vấn đề, đề xuất giải pháp, sáng tạo                                                    | -   | X   | -          |
| 11  | **Đóng góp vào dự án/tổ chức**      | Hiệu quả công việc, sáng kiến cải tiến, ghi nhận từ team                                         | -   | X   | -          |
| 12  | **Tổng thể**                        | Đánh giá chung về toàn bộ quá trình thực tập                                                     | X   | -   | -          |

### Những điều đã làm tốt

* **Hoàn thành trọn vẹn vòng đời bảo mật** - Enable → Deploy → Detect → Harden → Re-validate → Clean-up - với kết quả đo lường được (S3.2, IAM.1, EC2.19 đều FAILED → PASSED), không dừng lại ở lý thuyết.
* **Kiểm chứng dựa trên bằng chứng.** Với mỗi bước khắc phục, tôi đều chạy lại quét Security Hub, lưu output CLI và ảnh chụp console, rồi so sánh điểm tuân thủ với baseline trước khi hardening thay vì mặc định là đã sửa xong.
* **Làm vượt phạm vi được giao.** Việc triển khai Amazon GuardDuty Tester bằng CDK và viết và đăng blog kỹ thuật về AWS Security Hub và Amazon GuardDuty Tester trên AWS Study Group đều do tôi tự đề xuất, không nằm trong proposal ban đầu.
* **Tài liệu song ngữ.** Mọi bước của workshop được viết bằng cả tiếng Anh và tiếng Việt, kèm hướng dẫn song song theo Console và CLI, để người khác có thể tái hiện lại lab.
* **Ý thức về chi phí.** Tôi đã xoá toàn bộ tài nguyên sau khi kết thúc lab và xác nhận qua Cost Explorer rằng không còn tài nguyên nào phát sinh phí.

### Cần cải thiện

* **Tự động hoá thay vì khắc phục thủ công.** Toàn bộ các bước sửa lỗi được tôi thực hiện bằng tay qua Console và CLI. Trong môi trường vận hành thật, cách này không mở rộng được - lẽ ra tôi nên xây dựng auto-remediation bằng **EventBridge + Lambda** dựa trên finding của Security Hub để giảm MTTR.
* **Infrastructure as Code.** Tôi dựng lab bằng các lệnh CLI tuần tự thay vì **CloudFormation** hoặc **Terraform**, khiến môi trường khó tái lập chính xác và khó quản lý phiên bản. Tôi mới chỉ tiếp xúc IaC một cách gián tiếp qua CDK stack đi kèm GuardDuty Tester.
* **Độ phủ tuân thủ.** Tôi mới xử lý ba control CIS trong khi bộ benchmark rộng hơn rất nhiều. Một đợt kiểm toán đầy đủ hơn - gồm mã hoá dữ liệu at-rest, thời gian lưu log và các control cho root account - sẽ phản ánh đúng hơn tình trạng bảo mật của tài khoản.
* **Kỷ luật về thời gian và phạm vi.** Tôi đã đánh giá thấp độ trễ 15-30 phút của chu kỳ đánh giá Security Hub và GuardDuty, dẫn tới phải sắp xếp lại một phần công việc trong Tuần 4. Tôi cần tính sẵn độ trễ kiểm chứng vào kế hoạch thay vì phát hiện giữa chừng.
* **Giao tiếp và trình bày.** Khả năng viết tài liệu của tôi tốt hơn khả năng báo cáo trực tiếp. Tôi muốn tự tin hơn khi trình bày kết quả kỹ thuật trước người nghe và khi giải thích các đánh đổi về bảo mật cho người không chuyên.
* **Tư duy giải quyết vấn đề sâu hơn.** Tôi có xu hướng đi theo hướng dẫn khắc phục có sẵn thay vì tự lập luận *vì sao* một control tồn tại và kẻ tấn công sẽ làm gì tiếp theo. Rèn luyện tư duy threat modeling là bước cải thiện rõ ràng nhất của tôi.
