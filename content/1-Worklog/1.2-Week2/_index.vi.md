---
title: "Worklog Tuần 2"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

## MỤC TIÊU VÀ NHIỆM VỤ ĐƯỢC GIAO

* Tập trung hoàn thành toàn bộ các bài thực hành (lab) thuộc Module 1 nhằm củng cố kỹ năng quản lý tài nguyên và kiểm soát chi phí ban đầu.
* Nghiên cứu lý thuyết và kiến trúc cốt lõi của Module 2, bao gồm dịch vụ mạng ảo AWS Virtual Private Cloud (VPC), các giải pháp bảo mật phân tầng (VPC Security) và cơ chế kết nối mạng riêng an toàn (VPN).

## QUÁ TRÌNH THỰC HIỆN VÀ KIẾN THỨC TÍCH LŨY

### Hoàn thiện chuỗi bài Lab Module 1: Quản trị tài nguyên và Kiểm soát ngân sách
* **Quá trình thực hiện:** Triển khai cấu hình thực tế các công cụ giám sát tài chính đám mây của AWS bao gồm AWS Billing Dashboard, AWS Cost Explorer và thiết lập các ngưỡng cảnh báo tự động thông qua AWS Budgets.
* **Kiến thức tích lũy:** Nắm vững tư duy FinOps (Quản trị tài chính trên mây). Việc hoàn thành các bài lab giúp thành thạo cách thiết lập hạn mức chi phí (Budget Alarms) gửi thông báo qua Email/SNS khi chi phí thực tế hoặc chi phí dự báo vượt ngưỡng (ví dụ: 80% hoặc 100% tài khoản Credit miễn phí). Hiểu cách phân tích biểu đồ xu hướng tiêu thụ tài nguyên bằng Cost Explorer để phát hiện sớm các tài nguyên lãng phí (như các ổ đĩa EBS không gắn vào EC2) và biết cách tạo Ticket yêu cầu hỗ trợ kỹ thuật một cách chuyên nghiệp qua AWS Support Center.

### Xây dựng kiến trúc mạng logic với AWS Virtual Private Cloud (VPC)
* **Quá trình thực hiện:** Phân tích các thành phần cấu thành một hệ thống mạng độc lập, an toàn trên AWS đám mây và thiết kế sơ đồ phân chia dải mạng logic.
* **Kiến thức tích lũy:**
  * **Dải địa chỉ IP (CIDR Block):** Hiểu cách quy hoạch vùng mạng sử dụng chuẩn CIDR (ví dụ: 10.0.0.0/16 cung cấp 65,536 địa chỉ IP) để làm nền tảng phân bổ hạ tầng cho doanh nghiệp mà không bị trùng lặp hệ thống mạng nội bộ (On-premises).
  * **Phân vùng mạng (Subnets):** Nắm rõ tư duy thiết kế hệ thống nhiều lớp (Multi-tier Architecture). Học cách chia nhỏ VPC thành Public Subnet (dành cho các thành phần hướng ra ngoài Internet như Web Server, Load Balancer) và Private Subnet (dành cho các thành phần cốt lõi cần bảo mật tuyệt đối như Database, App Server/Backend). Khắc sâu quy tắc AWS luôn giữ lại 5 địa chỉ IP đầu tiên và cuối cùng trong mỗi Subnet cho các mục đích định tuyến và quản lý nội bộ.
  * **Cơ chế định tuyến (Route Tables & Internet Gateway):** Biết cách thiết lập Internet Gateway (IGW) và gắn (attach) vào VPC để kích hoạt khả năng giao tiếp với Internet. Thành thạo việc cấu hình Bảng định tuyến (Route Table): Public Route Table sẽ có một route hướng lưu lượng (0.0.0.0/0) đi qua IGW, trong khi Private Route Table cô lập hoàn toàn, giúp bảo vệ dữ liệu tối đa.
* **Video hướng dẫn:** https://youtu.be/O9Ac_vGHquM?si=BeFIVXXvxxdZSIXl

### Thiết lập rào chắn bảo mật phân tầng (VPC Security)
* **Quá trình thực hiện:** Nghiên cứu và so sánh hai tầng bảo vệ mạng cốt lõi của AWS để áp dụng vào việc kiểm soát lưu lượng truy cập (Inbound/Outbound).
* **Kiến thức tích lũy:** Phân biệt và làm chủ hai công cụ bảo mật có tính chất bù trừ cho nhau:
  * **Security Groups (SG):** Hoạt động như một tường lửa ảo ở cấp độ Instance (EC2). Đây là cơ chế Stateful (có nhớ trạng thái) – nghĩa là nếu cấu hình cho phép lưu lượng Inbound (đi vào) từ một cổng, hệ thống sẽ tự động cho phép lưu lượng Outbound (đi ra) tương ứng phản hồi mà không cần mở cổng Outbound. Tư duy thiết kế tại đây tuân thủ nguyên tắc "Least Privilege" (Quyền tối thiểu), chỉ mở các cổng thực sự cần thiết (như cổng 80/443 cho Web, cổng 22 cho SSH).
  * **Network Access Control Lists (NACLs):** Hoạt động như một tường lửa ở cấp độ Subnet. Đây là cơ chế Stateless (không nhớ trạng thái) – đòi hỏi phải cấu hình tường minh cả luật Inbound và Outbound. NACLs xử lý các quy tắc theo thứ tự số hiệu (Rule Number) từ thấp đến cao và hỗ trợ cả luật Allow (Cho phép) lẫn Deny (Từ chối) – cực kỳ hữu ích khi cần chặn các dải IP độc hại tấn công vào hệ thống.
* **Video hướng dẫn:** https://youtu.be/BPuD1l2hEQ4?si=KS3dLYLcKvWBX-6d

### Giải pháp kết nối mở rộng doanh nghiệp (VPN)
* **Quá trình thực hiện:** Nghiên cứu mô hình kết nối mạng lai (Hybrid Cloud) an toàn giữa trung tâm dữ liệu truyền thống và đám mây AWS.
* **Kiến thức tích lũy:** Hiểu sâu về kiến trúc AWS Site-to-Site VPN, giải pháp giúp thiết lập một kênh truyền dữ liệu mã hóa IPSec an toàn đi qua môi trường Internet công cộng. Nắm rõ vai trò của hai thực thể: Customer Gateway (CGW) đặt tại phía văn phòng/nhà máy của khách hàng và Virtual Private Gateway (VGW) đặt tại phía AWS VPC. Kiến thức này cực kỳ quan trọng đối với các hệ thống lớn cần đồng bộ dữ liệu liên tục giữa hạ tầng vật lý sẵn có và các dịch vụ phân tích dữ liệu trên đám mây.
* **Video hướng dẫn:** https://youtu.be/CXU8D3kyxIc?si=gyatA4GN0EmhEwff