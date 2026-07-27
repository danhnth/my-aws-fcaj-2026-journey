---
title: "Event 1"
date: 2026-07-27
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

# Bài thu hoạch “Agentic AI Build Week (AABW)”

### Mục Đích Của Sự Kiện

- Tạo sân chơi thực chiến để xây dựng ứng dụng **Agentic AI** trên nền tảng AWS trong thời gian giới hạn
- Giới thiệu bộ công cụ agentic của AWS: Amazon Bedrock AgentCore, Strands Agent, SageMaker
- Rèn kỹ năng thu hẹp phạm vi (scoping), làm việc nhóm và đưa ý tưởng thành MVP end-to-end
- Chia sẻ, phản biện kiến trúc và chi phí vận hành giữa các đội qua buổi demo day

### Thông Tin Sự Kiện

- **Tên sự kiện:** Agentic AI Build Week (AABW)
- **Thời gian:** ngày 25/07/2026
- **Địa điểm:** AWS Event Hall – Tầng 26, tòa nhà Bitexco, Quận 1, TP. Hồ Chí Minh
- **Vai trò:** Người tham dự

### Nội Dung Nổi Bật

#### Đội 3KA — S.H.E.P.H.E.R.D

*Smart Human-flow Evaluation, Prediction, Hazard Detection, Response, and Dispatch*

- **Bài toán:** nhân viên vận hành phải theo dõi cùng lúc nhiều lối vào, hàng chờ, gian hàng và luồng di chuyển của đám đông. Giám sát thủ công thì chậm, bị động, khó mở rộng và dễ bỏ sót sự cố.
- **Giải pháp:** phân tích camera trực tiếp để phát hiện và theo vết người, đo mật độ đám đông, ước lượng tình trạng hàng chờ, nhận diện dấu hiệu ùn tắc sớm, dự báo áp lực quá tải và đề xuất hành động cho nhân viên.
- **Công nghệ:** YOLO + ByteTrack, Amazon SageMaker, Amazon Bedrock AgentCore + Strands Agent, dashboard giám sát bằng React.
- **Lớp Agentic AI:** *Autonomous Monitor* liên tục theo dõi chỉ số và tự tạo cảnh báo chủ động; *Operator Copilot* cho phép nhân viên hỏi bằng ngôn ngữ tự nhiên và nhận câu trả lời ngắn gọn dựa trên số liệu trực tiếp.
- **Thách thức đội gặp phải:** giữ luồng video ổn định, giảm độ trễ inference, duy trì tracking giữa các frame, chọn vị trí camera hiệu quả, kiểm soát chi phí và giữ phạm vi khả thi trong 24 giờ.

#### Đội Signal Scout — Phát hiện sớm thay đổi chiến lược doanh nghiệp

- **Giá trị mang lại:** phát hiện sớm dấu hiệu tái cấu trúc, nối các tín hiệu rời rạc thành một câu chuyện rõ ràng, phân tích chỉ số và dựng kịch bản, hỗ trợ quyết định *Maintain – Adapt – Accelerate*.
- **Nguyên tắc thiết kế:** mọi kết luận đều phải có bằng chứng kiểm chứng được; phân tích minh bạch; con người giữ quyền quyết định cuối cùng.
- **Khách hàng mục tiêu:** đội chiến lược doanh nghiệp, quản trị rủi ro, competitive intelligence và quản lý tài khoản B2B.
- **Công nghệ và đối tác:** AWS (Bedrock, AgentCore, Lambda, DynamoDB, API Gateway, Amplify, Cognito, CloudWatch…), LangFuse, TinyFish, Apify.
- **Bài toán chi phí:** đội trình bày bảng bóc tách chi phí theo ba kịch bản — riêng AWS khoảng 17–130 USD/tháng, tổng chi phí kể cả dịch vụ bên thứ ba khoảng 81 – 94 – 359 USD/tháng — kèm một phương án kiến trúc tối ưu chi phí hơn.

#### Đội Plan V — SA Professional Native App

- **Bài toán:** Solution Architect thường xuyên bị ép tiến độ, phải tự làm bốn việc tốn thời gian nhất: trích xuất yêu cầu, phác thảo kiến trúc ban đầu, vẽ sơ đồ và ước tính chi phí cloud.
- **Giải pháp:** ứng dụng AI native phân tích yêu cầu dạng ngôn ngữ tự nhiên và dạng có cấu trúc; đề xuất các phương án kiến trúc high-level có nhận biết hybrid-cloud và tuân theo chuẩn công ty; sinh sơ đồ Draw.io cùng AWS Architecture Icons chính thức; ước tính chi phí AWS cho vùng *ap-southeast-1*; chỉ ra khuyến nghị, giả định và lỗ hổng trong yêu cầu; tinh chỉnh lặp qua chat sidebar với custom instruction theo từng dự án.
- **Tác động:** từ chỗ đọc BRD/PRD thủ công từng dòng, bắt đầu từ trang trắng, viết IaC bằng tay và ước tính theo cảm tính — nay chỉ cần upload tài liệu và trao đổi tự nhiên để có Requirements Catalogue trong vài phút, một bản nháp kiến trúc để phản biện, IaC sinh tự động và bản ước tính chi phí đi kèm.

### Những Gì Học Được

#### Tư Duy Sản Phẩm

- **Bắt đầu từ nỗi đau vận hành thật:** cả ba sản phẩm đều xuất phát từ một công việc thủ công tốn thời gian có thật, không phải từ công nghệ.
- **Scope nhỏ, làm cho xong:** một tính năng hoàn chỉnh có sức thuyết phục hơn nhiều ý tưởng lớn còn dang dở.
- **Con người giữ quyền quyết định:** AI đưa ra bằng chứng và khuyến nghị, người dùng mới là bên quyết định.

#### Kiến Trúc Kỹ Thuật

- **Agentic AI trên AWS:** cách dùng Amazon Bedrock AgentCore và Strands Agent để xây agent tự chủ, biết chủ động cảnh báo thay vì chỉ trả lời khi được hỏi.
- **Kết hợp nhiều lớp:** computer vision thời gian thực + object tracking + cloud inference + dashboard vận hành + lớp agent.
- **Tính chi phí ngay từ đầu:** bảng bóc tách chi phí theo dịch vụ và theo kịch bản min/mid/max là một phần bắt buộc của thiết kế, không phải việc làm sau.
- **Khả năng giải thích:** agent phải chủ động, giải thích được và hành động được thì mới dùng được trong vận hành thực tế.

#### Kỹ Năng Mềm

- **Phân vai rõ ràng:** ai code, ai thiết kế, ai pitch — quyết định sớm giúp tránh chồng chéo và tranh cãi giữa chừng.
- **Kể chuyện trong 3 phút:** luyện trước phần demo là yếu tố quyết định khi trình bày trước ban giám khảo.
- **Chuẩn bị trước không phải gian lận:** có mục tiêu rõ, template khởi tạo và tài khoản sẵn sàng giúp dành trọn thời gian cho việc xây dựng.

### Ứng Dụng Vào Công Việc

- **Thử nghiệm agentic pattern:** áp dụng mô hình *autonomous monitor + copilot* cho các tác vụ giám sát định kỳ thay vì dashboard thụ động.
- **Chuẩn hóa việc ước tính chi phí:** lập bảng chi phí theo kịch bản min/mid/max cho mọi kiến trúc đề xuất.
- **Bám nguyên tắc “có bằng chứng”:** mọi kết luận do AI sinh ra đều phải kèm nguồn để kiểm chứng.
- **Tăng tốc khâu tài liệu và sơ đồ:** dùng công cụ AI để sinh bản nháp kiến trúc và diagram, rồi con người phản biện và hoàn thiện.
- **Rèn thói quen scoping:** chia bài toán thành MVP có thể hoàn thành trong khung thời gian ngắn.

### Trải nghiệm trong event

Tham gia **Agentic AI Build Week** là một trải nghiệm rất khác so với các workshop thông thường: thay vì nghe trình bày, tôi được chứng kiến các đội đi trọn hành trình từ ý tưởng đến sản phẩm chạy được chỉ trong 24 giờ. Một số trải nghiệm nổi bật:

#### Chứng kiến quá trình xây dựng thật

- Các đội chia sẻ rất thẳng thắn về giai đoạn hoang mang lúc bắt đầu, khoảnh khắc ý tưởng “vỡ ra”, và cảm giác tự hào khi sản phẩm chạy được — một cung bậc cảm xúc mà slide kỹ thuật không thể hiện hết.
- Nhiều thành viên bắt đầu mà **không có nền tảng AI** và **lần đầu dùng AWS**, cho thấy rào cản thực sự không nằm ở kinh nghiệm mà ở việc dám bắt đầu.

#### Học từ kiến trúc và chi phí thật

- Được xem sơ đồ kiến trúc chi tiết của ba sản phẩm khác nhau, mỗi sản phẩm giải một lớp bài toán riêng: thị giác máy tính thời gian thực, tổng hợp tín hiệu doanh nghiệp, và tự động hóa công việc của Solution Architect.
- Bảng bóc tách chi phí AWS theo từng dịch vụ của đội Signal Scout là một tài liệu tham khảo rất thực tế cho việc ước tính chi phí dự án sau này.

#### Kết nối và trao đổi

- Phần hỏi đáp sau mỗi bài trình bày giúp hiểu rõ hơn các đánh đổi trong thiết kế: độ trễ so với độ chính xác, chi phí so với khả năng mở rộng, mức độ tự chủ của agent so với quyền kiểm soát của con người.
- Gặp gỡ nhiều bạn cùng mối quan tâm về Agentic AI, mở ra cơ hội trao đổi và học hỏi tiếp sau sự kiện.

#### Bài học rút ra

- **Việc xuất hiện và bắt tay vào làm đã là một nửa chặng đường** — không cần đợi đến khi cảm thấy đủ giỏi.
- **Một sản phẩm nhỏ chạy được có giá trị hơn một ý tưởng lớn còn dang dở.**
- **Những người mình gặp quan trọng hơn giải thưởng** — mạng lưới và kinh nghiệm ở lại lâu hơn kết quả cuộc thi.
- Agentic AI chỉ thực sự hữu ích khi agent **chủ động, giải thích được và hành động được**, đồng thời vẫn để con người giữ quyền quyết định cuối cùng.

#### Một số hình ảnh khi tham gia sự kiện
* Thêm các hình ảnh của các bạn tại đây
> Tổng thể, sự kiện không chỉ cung cấp kiến thức về Agentic AI và hệ sinh thái AWS, mà còn cho tôi thấy rõ cách một ý tưởng được thu hẹp, xây dựng và trình bày thành sản phẩm hoàn chỉnh trong điều kiện giới hạn về thời gian.