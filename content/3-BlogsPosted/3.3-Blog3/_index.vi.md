---
title: "Blog 3"
date: 2026-07-22
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# AWS Cloud Security & Compliance — Tìm hiểu về Rủi ro và Sự tuân thủ trên môi trường Cloud

Chào mọi người, trong quá trình thực tập tại AWS FCAJ, mình có hứng thú với chủ đề Cloud Security và đã tìm hiểu nhiều tài liệu AWS. Mình có lướt qua whitepaper **AWS Risk and Compliance** nói về nền tảng cơ bản để đưa hệ thống lên Cloud một cách chuẩn chỉnh.

## Mô hình trách nhiệm chung (Shared Responsibility Model)

Điểm cốt lõi nhất mà tài liệu này nhấn mạnh chính là **Mô hình trách nhiệm chung**. Nhiều người hay nhầm tưởng đưa mọi thứ lên đám mây là AWS sẽ lo hết từ A-Z. Nhưng thực tế, AWS chỉ chịu trách nhiệm bảo mật cho bản thân hạ tầng đám mây như an ninh vật lý tại data center, phần cứng, mạng và lớp ảo hóa. Còn phần bảo mật bên trong đám mây từ dữ liệu, phân quyền IAM, hệ điều hành cho đến cấu hình firewall lại hoàn toàn thuộc về phía người dùng.

## Quản trị tuân thủ (Compliance Governance)

Ngoài ra tài liệu cũng làm rõ cách người dùng AWS phải tự chủ động quản lý và đảm bảo tính tuân thủ (Compliance Governance) trên môi trường của mình ra sao. Một quy trình quản trị tuân thủ tốt thường qua các bước:

1. **Tìm hiểu và nắm rõ các mục tiêu cần tuân thủ** bằng cách đối chiếu tài liệu về AWS Shared Responsibility Model, AWS Security Documentation, các báo cáo trên AWS Artifact.
2. **Thiết kế và triển khai các bộ kiểm soát (controls)** đáp ứng đúng tiêu chuẩn đề ra theo mô hình trách nhiệm chung.
3. **Xác định và ghi nhận rõ ràng các phần kiểm soát do bên thứ ba nắm giữ.**
4. **Liên tục kiểm tra, xác minh** xem các cơ chế bảo mật có thực sự hoạt động hiệu quả như thiết kế đã đặt ra hay không.

## Về phía AWS

Ở chiều ngược lại, về phía AWS, để xây dựng niềm tin cho khách hàng, họ cũng tích hợp sẵn hàng loạt cơ chế quản lý rủi ro và tuân thủ chặt chẽ như triển khai các công cụ tự động hóa và bộ kiểm soát bảo mật đa dạng. Thêm vào đó, AWS được định kì trải qua những cuộc **third-party audits** để duy trì các chứng chỉ uy tín nhằm duy trì tính đảm bảo của môi trường kiểm soát của AWS, qua đó mang lại lợi ích trực tiếp đến khách hàng của họ.

## Kết luận

Đọc xong whitepaper này giúp mình có góc nhìn thực tế hơn khi thiết kế và làm lab trên cloud. Bảo mật không chỉ dừng lại ở việc bật công cụ quét hay viết code, mà còn là việc hiểu rõ ranh giới trách nhiệm và xây dựng quy trình kiểm soát liên tục để hệ thống luôn vận hành an toàn.

## Tài liệu tham khảo

- [AWS Risk and Compliance Whitepaper](https://docs.aws.amazon.com/whitepapers/latest/aws-risk-and-compliance/welcome.html)

**Tags:** `#AWS` `#CloudSecurity` `#Compliance` `#SharedResponsibility` `#FCAJ` `#AWSStudyGroup`
