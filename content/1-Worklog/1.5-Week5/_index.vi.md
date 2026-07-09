---
title: "Worklog Tuần 5"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

## MỤC TIÊU & NHIỆM VỤ ĐƯỢC GIAO

* Bắt tay vào thực hành chuỗi bài lab cốt lõi của Module 3 về dịch vụ điện toán đám mây AWS EC2.
* Hoàn thành cuốn chiếu các bài thực hành, với mục tiêu tiến độ đạt đến Lab 57 trong tuần này.
* Vận dụng lý thuyết đã học để tự tay khởi tạo, cấu hình và quản trị vòng đời của các máy chủ ảo.

## QUÁ TRÌNH THỰC HIỆN & KIẾN THỨC TÍCH LŨY

Tuần này đánh dấu bước chuyển mình quan trọng từ việc thiết lập hạ tầng mạng sang trực tiếp vận hành các tài nguyên tính toán. Việc làm chủ EC2 giúp mở ra khả năng triển khai các kiến trúc dữ liệu phân tán phức tạp trên môi trường đám mây.

### Khởi tạo và Truy cập Máy chủ ảo (EC2 Provisioning & SSH)
* **Quá trình thực hiện:** Tiến hành thực hành các bước chọn Amazon Machine Image (AMI), xác định Instance Type phù hợp và thiết lập bộ nhớ (EBS).
* **Kiến thức tích lũy:** Nắm vững kỹ năng sử dụng công cụ Terminal/PuTTY kết hợp với Private Key (.pem) để thiết lập kết nối SSH an toàn vào máy chủ Linux. Việc cấu hình Security Groups chuẩn xác là yếu tố quyết định để kết nối thành công mà không tạo ra lỗ hổng bảo mật.

### Tự động hóa Cấu hình với EC2 User Data
* **Quá trình thực hiện:** Đây là một kỹ thuật cực kỳ mạnh mẽ được áp dụng trong các bài lab. Thay vì SSH vào từng máy để gõ lệnh cài đặt thủ công, việc sử dụng kịch bản (shell script) trong trường User Data giúp máy chủ tự động cài đặt web server (Apache/Nginx) hoặc các thư viện cần thiết ngay khi vừa khởi động.
* **Kiến thức tích lũy:** Kỹ năng này rất hữu ích khi cần thiết lập nhanh chóng một môi trường máy chủ chuẩn hóa để triển khai các hệ quản trị cơ sở dữ liệu mạnh mẽ, sẵn sàng cho việc lập trình các logic xử lý dữ liệu phức tạp bằng Stored Procedures hoặc Triggers trực tiếp trên mây.

### Quản trị Vòng đời Máy chủ (Instance Lifecycle)
* **Quá trình thực hiện:** Thực hành các thao tác Start, Stop, Reboot và Terminate máy chủ.
* **Kiến thức tích lũy:** Quá trình này giúp củng cố tư duy quản trị tài chính đám mây (FinOps). Nắm rõ nguyên lý tính tiền của AWS: khi máy chủ ở trạng thái Stop, CPU/RAM sẽ ngừng tính phí, nhưng không gian lưu trữ (EBS volume) đi kèm vẫn tiếp tục tiêu tốn ngân sách. Điều này hình thành thói quen kiểm soát tài nguyên chặt chẽ, đảm bảo hiệu quả chi phí cho các hệ thống quy mô lớn.

### Phân tích siêu dữ liệu máy chủ (Instance Metadata)
* **Quá trình thực hiện:** Thực hành truy vấn các thông tin nội tại của máy chủ (như Public IP, Private IP, Instance ID) bằng cách sử dụng địa chỉ IP đặc biệt 169.254.169.254 trực tiếp từ bên trong EC2.
* **Kiến thức tích lũy:** Đây là nền tảng để tự động hóa các ứng dụng có khả năng tự nhận thức môi trường đang chạy.