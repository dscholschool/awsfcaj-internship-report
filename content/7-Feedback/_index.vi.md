---
title: "Chia sẻ, đóng góp ý kiến"
date: 2024-01-01
weight: 7
chapter: false
pre: " <b> 7. </b> "
---
### Đánh giá chung

**1. Môi trường làm việc** Chương trình mang lại một môi trường học tập và thực hành mang tính kết nối cao, cởi mở và đậm chất kỹ thuật. Hệ thống quản lý tiến độ và phân chia lộ trình các bài lab được thiết kế rất khoa học, rõ ràng, giúp tôi dễ dàng theo dõi và hoàn thành các mục tiêu đề ra một cách tập trung nhất.

**2. Sự hỗ trợ của mentor / team admin** Đội ngũ mentor và các anh chị quản trị viên (admin) hỗ trợ cực kỳ chất lượng. Mỗi khi tôi gặp phải các nút thắt kỹ thuật khó trong quá trình làm lab — như cấu hình bảng định tuyến phức tạp cho VPC, tối ưu hóa chính sách bảo mật IAM, hay siết chặt tường lửa Security Group cho cụm database — các anh chị luôn đưa ra những phản hồi và định hướng rất chuẩn xác. Tôi đặc biệt đánh giá cao việc mentor không đưa sẵn đáp án mà luôn hướng dẫn tư duy logic phân tích lỗi để tôi tự học cách debug hạ tầng.

**3. Sự phù hợp giữa công việc và chuyên ngành học** Là một sinh viên ngành Công nghệ thông tin định hướng chuyên sâu về triển khai hệ thống và kiến trúc dữ liệu, nội dung của bootcamp hoàn toàn trùng khớp với lộ trình phát triển của tôi. Chương trình đã giúp tôi xóa nhòa khoảng cách giữa lý thuyết lập trình cơ sở dữ liệu thông thường (như Stored Procedures, Triggers nội bộ) với việc vận hành thực tế các luồng dữ liệu an toàn trên đám mây (Amazon RDS, Data Lake trên S3, cụm EC2 phân tầng).

**4. Cơ hội học hỏi & phát triển kỹ năng** Cơ hội phát triển bản thân qua chương trình là vô cùng lớn. Việc đi qua chuỗi bài lab chuyên sâu đã giúp tôi chuyển đổi từ tư duy viết code local sang tư duy thiết kế hệ thống quy mô lớn. Tôi đã làm chủ được các kiến thức cốt lõi về FinOps (quản trị chi phí đám mây), quy hoạch phân vùng mạng an toàn (VPC, NAT Gateway) và tự động hóa hạ tầng (EC2 User Data). Việc đệ trình và bảo vệ sơ đồ kiến trúc trước các admin cũng giúp tôi nâng cao kỹ năng viết tài liệu kỹ thuật và thuyết trình bài bản.

**5. Văn hóa & tinh thần đồng đội** Văn hóa làm việc tại đây rất chuyên nghiệp nhưng không kém phần gắn kết. Các buổi rà soát và đánh giá bản mẫu hệ thống luôn được thực hiện nghiêm túc theo tiêu chuẩn doanh nghiệp, nhưng tinh thần của mọi người đều rất tích cực và hỗ trợ lẫn nhau. Sự đồng hành sát sao của các thành viên trong nhóm và các admin tạo ra một môi trường thúc đẩy sự tiến bộ liên tục.

**6. Chính sách / phúc lợi cho thực thực tập sinh** Việc ban tổ chức hỗ trợ tài khoản tài khoản AWS Credit miễn phí ($100 credits) là một chính sách cực kỳ tuyệt vời. Phúc lợi này giúp tôi hoàn toàn thoải mái thực hành các bài lab cấu hình tài nguyên lớn, thử nghiệm các kịch bản co giãn hệ thống và dọn dẹp tài nguyên thực tế mà không gặp áp lực về mặt chi phí.

---

### Khảo sát và Nhìn nhận lại kỳ thực tập

* **Điều bạn hài lòng nhất trong thời gian thực tập?** Điều tôi hài lòng nhất là đã tự tay chuyển hóa thành công một bản mẫu chạy nội bộ (local) thành một kiến trúc mạng đám mây hoàn chỉnh hoạt động trơn tru trên AWS. Khoảnh khắc kiểm thử luồng Webhook thanh toán từ bên thứ ba (SePay) xuyên qua Internet Gateway, gọi trúng cụm EC2Backend trong Private Subnet, kích hoạt tự động các Triggers xử lý logic trong RDS PostgreSQL và mở khóa quyền tải file số an toàn qua đường hầm S3 Gateway Endpoint thực sự là một trải nghiệm "thực chiến" vô giá đối với tôi.

* **Điều bạn nghĩ công ty cần cải thiện cho các thực tập sinh sau?** Khối lượng kiến thức hạ tầng mạng và chính sách IAM trong những tuần đầu tương đối nặng và có độ dốc cao đối với những bạn mới tiếp cận. Ban tổ chức có thể cân nhắc bổ sung một vài buổi workshop ngắn chuyên về "Hướng dẫn đọc log và Xử lý sự cố mạng cơ bản" ở giai đoạn khởi động để các bạn thực tập sinh khóa sau dễ dàng bắt nhịp hơn.

* **Nếu giới thiệu cho bạn bè, bạn có khuyên họ thực tập ở đây không? Vì sao?** Chắc chắn là có. Tôi sẽ khuyên tất cả các bạn sinh viên IT muốn theo đuổi mảng hạ tầng hoặc kỹ thuật dữ liệu tham gia chương trình này. Tư duy siết chặt bảo mật (Zero Trust, Least Privilege) và tối ưu hóa tài chính (FinOps) được dạy tại đây chính là những kỹ năng cốt lõi mà mọi doanh nghiệp lớn hiện nay đều tìm kiếm.

---

### Đề xuất & mong muốn

* **Đề xuất cải thiện trải nghiệm:** Tôi đề xuất có thể tổ chức các buổi rà soát sơ đồ kiến trúc draw.io sớm hơn một chút trong tiến độ dự án. Việc này giúp các bạn thực tập sinh chốt được khung sườn hạ tầng chuẩn xác ngay từ đầu, tránh việc cấu hình sai hệ thống mạng ở các bước sau.
* **Mong muốn trong tương lai:** Tôi rất mong muốn có cơ hội tiếp tục đồng hành cùng cộng đồng hoặc các dự án mở rộng của hệ sinh thái này, đặc biệt là ở các vị trí liên quan đến kỹ thuật dữ liệu, xây dựng pipeline tự động hoặc quản trị kiến trúc dữ liệu đám mây.
* **Lời kết:** Xin gửi lời cảm ơn chân thành nhất tới đội ngũ FCJ, các anh chị mentor và admin. Hành trình này không chỉ giúp tôi vững vàng hơn về mặt kỹ thuật đám mây mà còn thay đổi hoàn toàn cách tôi tư duy khi xây dựng một hệ thống phân tán: an toàn hơn, tối ưu hơn và hiệu quả hơn về mặt chi phí.