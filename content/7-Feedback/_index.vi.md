---
title: "Chia sẻ, đóng góp ý kiến"
date: 2026-07-26
weight: 7
chapter: false
pre: " <b> 7. </b> "
---

> Tại đây tôi chia sẻ ý kiến cá nhân về trải nghiệm khi tham gia chương trình **First Cloud AI Journey (FCAJ)**, để team FCAJ có thể phát huy những điểm đã tốt và cải thiện những điểm còn thiếu sót.

### Đánh giá chung

**1. Môi trường làm việc**
FCAJ vận hành chủ yếu theo hình thức remote, tự học theo lộ trình, xoay quanh nền tảng **AWS Study Group** và cộng đồng cohort, với learning path được tổ chức tại `cloudjourney.awsstudygroup.com`. Tôi thấy hình thức này thực sự phù hợp với công việc cloud - tôi có tài khoản AWS riêng, region riêng (`ap-southeast-1`) và được tự do làm hỏng rồi tự sửa mà không ảnh hưởng tới môi trường của người khác. Kênh cohort khá sôi nổi, câu hỏi hiếm khi bị bỏ lửng lâu. Đánh đổi lớn nhất của mô hình remote-first là nhịp độ phụ thuộc rất nhiều vào tính tự kỷ luật: những tuần tôi tự đặt lịch làm việc hằng ngày thì tiến độ đều đặn, còn những tuần không làm vậy thì tiến độ trở nên thất thường.

**2. Sự hỗ trợ của mentor / team admin**
Phong cách hướng dẫn là điều tôi đánh giá cao nhất ở chương trình. Ngay trong buổi orientation Tuần 1, kỳ vọng, định dạng báo cáo và lộ trình học đã được trình bày rõ ràng nên tôi không phải đoán thế nào là "hoàn thành". Sau đó, khi tôi chia sẻ các bài blog về **AWS Security Hub** và **Amazon GuardDuty Tester** ([3-BlogsPosted](../3-BlogsPosted/)) với cohort ở Tuần 6, và khi báo cáo cuối kỳ được review ở Tuần 8, phản hồi tôi nhận được đều cụ thể và có thể hành động được, chứ không chỉ là một lời duyệt qua loa. Tôi đặc biệt trân trọng việc mentor để tôi tự xử lý vấn đề - khi finding trên Security Hub không cập nhật sau khi khắc phục, tôi được gợi ý tìm hiểu chu kỳ đánh giá thay vì được đưa thẳng đáp án, và việc tự hiểu ra độ trễ 15-30 phút đó hữu ích hơn nhiều so với việc chỉ được bảo "cứ đợi đi".

**3. Sự phù hợp giữa công việc và chuyên ngành học**
Là sinh viên Khoa học Máy tính, tôi thấy mức độ phù hợp rất cao. Ở trường tôi có nền tảng - mạng máy tính, hệ điều hành, lý thuyết kiểm soát truy cập - và FCAJ biến chúng thành thứ vận hành được: subnet và route table của VPC thay vì topology trừu tượng, IAM policy và least privilege thay vì mô hình access control trong sách, các control của CIS AWS Foundations Benchmark thay vì "best practice bảo mật" chung chung. Những mảng như phát hiện mối đe dọa trên cloud, kiểm toán tuân thủ và các dịch vụ bảo mật managed thì hoàn toàn mới với tôi và không có trong chương trình học.

**4. Cơ hội học hỏi & phát triển kỹ năng**
Độ dốc học tập trong tám tuần khá lớn, theo hướng tích cực. Tôi đi từ việc tạo tài khoản AWS đầu tiên ở Tuần 1 đến việc chạy trọn một vòng đời vận hành bảo mật - bật CloudTrail, GuardDuty, AWS Config, Security Hub; triển khai môi trường chứa lỗ hổng; phát hiện các cấu hình sai; khắc phục; và chứng minh S3.2, IAM.1, EC2.19 đều chuyển từ FAILED sang PASSED. Việc triển khai **Amazon GuardDuty Tester** bằng CDK và phân tích hơn 50 loại finding thuộc sáu nhóm là bài học giá trị nhất, vì nó cho phép tôi kiểm chứng khả năng phát hiện thay vì mặc định là nó hoạt động. Chương trình cũng rèn các kỹ năng ngoài kỹ thuật thuần: viết tài liệu kỹ thuật song ngữ, đăng blog cho người đọc công khai, và tham dự **Agentic AI Build Week (AABW)** — hackathon tại AWS Event Hall ở tòa nhà Bitexco, nơi các đội xây dựng ứng dụng agentic AI sử dụng Amazon Bedrock AgentCore, Strands Agent và SageMaker, trình bày ba sản phẩm hoạt động được (S.H.E.P.H.E.R.D, Signal Scout, SA Professional Native App) kèm kiến trúc và bảng chi phí chi tiết.

**5. Văn hóa cộng đồng & tinh thần đồng đội**
Văn hóa của cohort FCAJ là cởi mở và mặc định chia sẻ kiến thức. Việc đăng bài lên AWS Study Group biến những ghi chú lẽ ra chỉ để riêng thành thứ mà mọi người có thể góp ý, và phản hồi tôi nhận được đã thực sự giúp bài viết tốt hơn. Việc tham dự AABW tại tòa Bitexco cùng các bạn khác — chứng kiến các đội xây dựng sản phẩm thật, nghe trực tiếp từ diễn giả AWS và thảo luận về kiến trúc, chi phí trong phần hỏi đáp — khiến chương trình có cảm giác gắn với hệ sinh thái AWS tại Việt Nam chứ không phải một khóa học online tách biệt.

**6. Cấu trúc & chính sách chương trình**
Cấu trúc tám tuần được cân đối tốt: khoảng năm tuần làm lab thực hành, một tuần dành riêng cho viết bài kỹ thuật, một tuần tham dự workshop của AWS và tuần cuối cho tài liệu và bàn giao. Việc bắt buộc nộp proposal từ đầu và viết worklog mỗi tuần giúp tôi trung thực với tiến độ của chính mình. AWS Free Tier cùng hướng dẫn dọn dẹp rõ ràng giúp tôi làm việc trên hạ tầng thật mà không lo chi phí, và tôi kết thúc chương trình mà không còn tài nguyên tính phí nào tồn đọng.

---

### Một số câu hỏi khác

**Điều tôi hài lòng nhất?**
Khoảnh khắc nhìn cả ba control CIS chuyển từ **FAILED** sang **PASSED** trên Security Hub sau khi khắc phục, và có thể chứng minh sự thay đổi đó bằng bằng chứng trước-sau chứ không phải chỉ nói suông. Ngay sau đó là lúc thấy hơn 50 finding của GuardDuty xuất hiện từ GuardDuty Tester và nhận ra mình đã đọc hiểu được những dữ liệu tấn công mà tám tuần trước còn hoàn toàn vô nghĩa với mình.

**Điều chương trình nên cải thiện cho các bạn tham gia sau?**
- **Đưa auto-remediation vào nội dung chính thức.** Lab hiện dừng ở khắc phục thủ công. Một module hướng dẫn **EventBridge + Lambda** tự động khắc phục dựa trên finding của Security Hub sẽ là bước tiếp theo tự nhiên và đúng với cách làm trong môi trường production.
- **Giới thiệu Infrastructure as Code sớm hơn.** Phần lớn lab dùng CLI tuần tự. Bổ sung nhánh CloudFormation hoặc Terraform song song sẽ giúp môi trường tái lập được và dạy một kỹ năng mà mọi vị trí cloud đều yêu cầu.
- **Cảnh báo trước về độ trễ đánh giá.** Chu kỳ quét 15-30 phút của Security Hub và GuardDuty không hiển nhiên với người mới và đã làm tôi mất thời gian lập kế hoạch. Chỉ cần một ghi chú trong phần prerequisites là đủ.
- **Thêm các mốc checkpoint có cấu trúc.** Những buổi sync trực tiếp hằng tuần (không bắt buộc) sẽ hỗ trợ các bạn remote khó tự quản lý nhịp độ, mà vẫn giữ được sự linh hoạt vốn là ưu điểm của mô hình này.

**Nếu giới thiệu cho bạn bè, tôi có khuyên họ tham gia không?**
Có, chắc chắn - với một điều kiện. Chương trình phù hợp với người sẵn sàng tự chủ động về thời gian và làm vượt mức tối thiểu. FCAJ cho bạn một tài khoản AWS thật, một bài toán bảo mật thật và sự tự do thật; bạn nhận lại được bao nhiêu tỉ lệ thuận với mức độ bạn chịu đi xa hơn phạm vi được giao.

---

### Đề xuất & mong muốn

- **Đề xuất:** Bổ sung một nhánh nâng cao tùy chọn sau phần lab cốt lõi - auto-remediation với EventBridge và Lambda, tổng hợp Security Hub đa tài khoản, và kiểm toán CIS toàn bộ benchmark thay vì chỉ ba control.
- **Đề xuất:** Khuyến khích các bạn tham gia ghép cặp để review chéo workshop của nhau. Tái hiện lại lab của người khác là cách nhanh nhất để phát hiện lỗ hổng trong tài liệu.
- **Mong muốn trong tương lai:** Tôi muốn tiếp tục gắn bó với cộng đồng AWS Study Group sau kỳ thực tập, duy trì việc viết bài về bảo mật cloud, và hướng tới chứng chỉ **AWS Certified Security - Specialty** dựa trên nền tảng đã tích lũy được ở đây.
- **Góp ý khác:** Cảm ơn team FCAJ và các mentor vì một chương trình được tổ chức bài bản và vì đã luôn chọn cách hướng dẫn thay vì đưa sẵn đáp án. Học được cách tự debug môi trường của mình - thay vì được "cứu" khỏi nó - là thói quen giá trị nhất tôi mang theo sau tám tuần này.
