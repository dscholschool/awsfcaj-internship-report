---
title: "Worklog Tuần 3"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

## MỤC TIÊU VÀ NHIỆM VỤ ĐƯỢC GIAO

* Bắt tay vào thực hành các bài lab của Module 2 trên môi trường AWS thực tế.
* Chuyển hóa toàn bộ lý thuyết về kiến trúc mạng (VPC) đã học ở tuần trước thành các kỹ năng thao tác trên AWS Management Console.
* Hoàn thiện tiến độ các bài lab (hiện đang làm đến Lab 03), tập trung vào việc tự tay xây dựng một môi trường mạng cô lập, cấu hình định tuyến và thiết lập các lớp bảo mật.

## QUÁ TRÌNH THỰC HIỆN VÀ KIẾN THỨC TÍCH LŨY

Với khối lượng thực hành lớn trong tuần này, tôi đã đi sâu vào từng bước cấu hình hạ tầng mạng. Những kiến thức tích lũy được không chỉ dừng lại ở lý thuyết mà đã trở thành kỹ năng giải quyết bài toán thực tế:

### Khởi tạo và Quy hoạch tài nguyên mạng (VPC & Subnet Allocation)
* **Quá trình thực hiện:** Tự tay tạo một VPC hoàn toàn mới thay vì dùng Default VPC của AWS. Tính toán và chia nhỏ dải IP (CIDR) thành các Subnet khác nhau đặt tại nhiều Availability Zones (AZs) để đảm bảo tính sẵn sàng cao (High Availability).
* **Kiến thức tích lũy:** Khắc sâu được kỹ năng quy hoạch địa chỉ mạng. Tôi học được cách phân bổ IP một cách tiết kiệm và hợp lý: tạo các Public Subnet với dải IP nhỏ cho các tài nguyên như Load Balancer hay Bastion Host, và tạo các Private Subnet với dải IP lớn hơn nhiều để làm không gian rộng rãi chứa các máy chủ ứng dụng (App Servers) hoặc cơ sở dữ liệu. Nhận thức rõ nguyên lý cô lập tài nguyên ngay từ bước thiết kế mạng vật lý ảo.

### Định tuyến luồng giao thông (Routing) và Xử lý Internet Access
* **Quá trình thực hiện:** Gắn Internet Gateway (IGW) cho VPC và cấu hình các bảng định tuyến (Route Tables) để điều hướng các gói tin. Đặc biệt, thiết lập cơ chế để các máy chủ nằm sâu trong mạng nội bộ (Private) vẫn có thể tải các bản cập nhật từ Internet mà không bị lộ địa chỉ IP thật.
* **Kiến thức tích lũy:** Thành thạo thao tác "map" (gắn kết) các Subnet vào đúng Route Table tương ứng. Hiểu rõ luồng đi của gói tin: từ máy chủ nội bộ -> Route Table -> Internet Gateway -> Internet.
* **Kiến thức cốt lõi về NAT Gateway / NAT Instance:** Đây là điểm sáng trong quá trình thực hành. Tôi học được cách triển khai NAT Gateway nằm ở Public Subnet, đóng vai trò như một "người trung gian" nhận yêu cầu truy cập Internet từ các máy chủ trong Private Subnet, thay mặt chúng lấy dữ liệu về rồi trả lại. Điều này giúp hệ thống nội bộ vừa kết nối được với thế giới bên ngoài (để update patch/software) vừa chặn đứng hoàn toàn các kết nối chủ động trái phép khởi tạo từ Internet nhắm vào hệ thống.

### Triển khai cấu hình Bảo mật thực tế (Security Implementation)
* **Quá trình thực hiện:** Trực tiếp viết và áp dụng các luật cho Security Groups (SG) và Network Access Control Lists (NACL) lên các tài nguyên vừa tạo trong Lab 03.
* **Kiến thức tích lũy:** Xây dựng được tư duy phòng thủ theo chiều sâu (Defense in Depth). Thực hành nguyên tắc "Quyền tối thiểu" (Least Privilege) thông qua việc chỉ mở port 22 (SSH) từ một địa chỉ IP duy nhất (IP của máy tính cá nhân hoặc Bastion Host), từ chối toàn bộ các nguồn truy cập khác. Nắm vững kỹ thuật tham chiếu Security Group: Thay vì cho phép một dải IP tĩnh truy cập vào Database, tôi học được cách cấu hình để Database Security Group chỉ chấp nhận kết nối đến từ App Server Security Group. Tính năng tham chiếu vòng này của AWS giúp hệ thống tự động co giãn cực kỳ linh hoạt và bảo mật tuyệt đối.

### Kỹ năng Kiểm thử và Xử lý sự cố (Troubleshooting)
* **Quá trình thực hiện:** Thử nghiệm kết nối mạng (Ping, SSH) giữa các máy ảo trong các subnet khác nhau và từ ngoài Internet vào. Đọc log và tìm lỗi khi kết nối thất bại.
* **Kiến thức tích lũy:** Rèn luyện tư duy debug mạng hạ tầng. Khi một kết nối không thành công, tôi học được cách kiểm tra tuần tự từ dưới lên trên: Kiểm tra máy chủ có Public IP chưa -> Kiểm tra Security Group đã mở port chưa -> Kiểm tra Route Table có đường đi ra IGW không -> Kiểm tra NACL có vô tình block subnet không.