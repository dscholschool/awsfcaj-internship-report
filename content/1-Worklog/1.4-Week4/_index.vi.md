---
title: "Worklog Tuần 4"
date: 2024-01-01
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

## MỤC TIÊU VÀ NHIỆM VỤ ĐƯỢC GIAO

* Hoàn thành dứt điểm toàn bộ các bài lab còn lại của Module 2 để đóng gói phần kiến thức hạ tầng mạng.
* Chuyển giao giai đoạn sang Module 3: Nghiên cứu lý thuyết, kiến trúc cốt lõi và các tham số cấu hình của dịch vụ điện toán đám mây mũi nhọn AWS EC2 (Elastic Compute Cloud).

## QUÁ TRÌNH THỰC HIỆN VÀ KIẾN THỨC TÍCH LŨY

Trong tuần này, việc hoàn thành chặng đường mạng ảo và bắt đầu tiếp cận tài nguyên tính toán (Compute) đã giúp tôi hình thành tư duy hệ thống mạch lạc hơn.

### Nghiệm thu Module 2 và Bài học dọn dẹp tài nguyên (FinOps Cleanup)
* **Quá trình thực hiện:** Tiến hành kiểm tra lại toàn bộ các luồng định tuyến cuối cùng trong mạng VPC, đảm bảo các kết nối giữa Public/Private Subnet hoạt động trơn tru, sau đó thực hiện giải phóng tài nguyên.
* **Kiến thức tích lũy:** Khắc sâu một nguyên tắc sống còn khi làm việc trên Cloud: **Xóa bỏ tài nguyên khi không sử dụng**. Các thành phần như NAT Gateway hay Elastic IP (IP tĩnh) của AWS sẽ tính phí theo giờ ngay cả khi máy chủ không chạy dữ liệu. Việc chủ động terminate (hủy) và delete các tài nguyên này sau khi hoàn thành chuỗi bài lab Module 2 giúp tôi rèn luyện kỹ năng quản lý ngân sách cực kỳ nghiêm túc, tránh việc lãng phí Credit vô ích.

### Làm chủ khái niệm Máy chủ ảo đám mây (AWS EC2 Fundamentals)
* **Quá trình thực hiện:** Phân tích kiến trúc của một thực thể EC2 (Instance) và cách nó thay thế các máy chủ vật lý truyền thống trong doanh nghiệp nhờ khả năng co giãn linh hoạt.
* **Kiến thức tích lũy:**
  * **Amazon Machine Image (AMI):** Hiểu rõ AMI đóng vai trò như một "khuôn đúc" (template) chứa sẵn Hệ điều hành (như Ubuntu, Amazon Linux, Windows Server) và các cấu hình phần mềm nền tảng. Thay vì mất hàng giờ cài OS cho máy chủ vật lý, AMI giúp nhân bản hàng trăm máy chủ có cấu hình giống hệt nhau chỉ trong vài phút.
  * **Tư duy phân loại máy chủ (Instance Types):** Nắm vững cách AWS đặt tên để lựa chọn tài nguyên tối ưu nhất. Ví dụ, hiểu cấu trúc tên như `t3.micro` (trong đó `t` là dòng General Purpose - đa mục đích, tiết kiệm chi phí; `3` là thế hệ phần cứng; `micro` là kích cỡ tài nguyên CPU/RAM). Tôi đã phân biệt được khi nào cần dùng dòng `C` (Compute Optimized - tối ưu tính toán cho thuật toán), dòng `R` (Memory Optimized - tối ưu bộ nhớ cho xử lý Big Data/Database), và dòng `T` để chạy thử nghiệm hoặc làm web server nhỏ.
* **Video hướng dẫn:** https://youtu.be/e7XeKdOVq40?si=DS2_HgBf6vSKbDkP

### Cơ chế Bảo mật và Xác thực nâng cao trên EC2
* **Quá trình thực hiện:** Nghiên cứu sâu về cách thiết lập rào chắn an toàn cho máy chủ trước khi nó được "phơi" ra môi trường Internet.
* **Kiến thức tích lũy:**
  * **Cơ chế Key Pairs:** Hiểu sâu về mã hóa bất đối xứng (Asymmetric Cryptography). AWS sẽ giữ Public Key trên máy chủ ảo, còn tôi nắm giữ Private Key (file .pem hoặc .ppk). Việc SSH vào máy chủ bắt buộc phải dùng cặp khóa này thay vì mật khẩu truyền thống, giúp loại bỏ hoàn toàn nguy cơ bị tấn công dò mật khẩu (Brute-force).
  * **Tường lửa lớp máy chủ (Security Groups):** Nhận thức rõ Security Group hoạt động như một bộ lọc giao thông ngay tại "cửa nhà" của từng con EC2. Tôi đã học được cách thiết kế phân lớp: Chỉ cho phép cổng 22 (SSH) nhận tín hiệu từ IP tĩnh của máy mình, và cổng 80/443 (HTTP/HTTPS) mở cho toàn mạng toàn cầu để người dùng truy cập web.
* **Video hướng dẫn:** https://youtu.be/yAR6QRT3N1k?si=03jBeqI5BH_Jq0ud