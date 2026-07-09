---
title: "Worklog Tuần 11"
date: 2024-01-01
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

## MỤC TIÊU & NHIỆM VỤ ĐƯỢC GIAO

* Hỗ trợ triển khai toàn bộ mã nguồn của dự án (Frontend, Backend) và Cơ sở dữ liệu từ môi trường phát triển (Local) lên hạ tầng đám mây AWS dựa trên sơ đồ kiến trúc đã chốt ở tuần 10.
* Tham gia hỗ trợ các thành viên trong nhóm cấu hình kết nối giữa các dịch vụ (Vercel, EC2, RDS, S3).
* Kiểm thử tích hợp toàn hệ thống (End-to-End Testing), đặc biệt là luồng thanh toán và tự động cập nhật trạng thái đơn hàng.

## QUÁ TRÌNH THỰC HIỆN & KIẾN THỨC TÍCH LŨY

Tuần này là giai đoạn "thực chiến" quan trọng nhất, mọi lý thuyết và bản vẽ kiến trúc đều được chuyển hóa thành các tài nguyên thực tế hoạt động trơn tru trên đám mây.

### Phối hợp Triển khai và Tối ưu Cơ sở dữ liệu (Amazon RDS)
* **Quá trình thực hiện:** Hỗ trợ nhóm khởi tạo cụm cơ sở dữ liệu Amazon RDS PostgreSQL đặt tại Private Subnet. Trực tiếp đảm nhận việc migration (chuyển đổi) toàn bộ cấu trúc bảng, Indexes, cũng như đưa các Stored Procedures và Triggers từ máy cá nhân lên môi trường RDS thực tế.
* **Kiến thức tích lũy:** Nắm vững quy trình cấu hình Security Group (tường lửa ảo) để cho phép máy chủ Backend (EC2) có thể giao tiếp an toàn với RDS thông qua cổng 5432. Việc đưa trực tiếp các đoạn mã xử lý logic xuống tầng database giúp tôi kiểm chứng được khả năng chịu tải và tốc độ truy xuất thực tế trên đám mây.

### Hỗ trợ Cấu hình Backend (EC2) và Lưu trữ (Amazon S3)
* **Quá trình thực hiện:** Tham gia cùng các thành viên thiết lập môi trường Node.js trên máy chủ EC2. Đồng thời, hỗ trợ khởi tạo S3 Bucket để lưu trữ các tệp mô hình 3D và tài liệu PDF.
* **Kiến thức tích lũy:** Vận dụng lại kiến thức cốt lõi của Module 5 (IAM) để gán IAM Role trực tiếp cho EC2. Thay vì nhúng khóa bảo mật (Access Key) vào mã nguồn Backend dễ gây rò rỉ, hệ thống của nhóm hiện tại có thể gọi API upload/download file từ S3 một cách tự động và bảo mật tuyệt đối nhờ cơ chế cấp quyền theo Role.

### Kiểm thử Tích hợp Webhook Thanh toán (SePay)
* **Quá trình thực hiện:** Cùng cả nhóm thực hiện các kịch bản mua hàng thực tế để kiểm tra tính năng thanh toán. Đóng vai trò giám sát log tại tầng cơ sở dữ liệu.
* **Kiến thức tích lũy:** Khi SePay gửi Webhook thông báo giao dịch thành công về Backend, tôi theo dõi trực tiếp sự kích hoạt của các Triggers trong RDS. Kết quả cho thấy dữ liệu đối soát trùng khớp, trạng thái đơn hàng được cập nhật tự động trong tíc tắc, và quyền tải file được mở khóa thành công cho người dùng mà không cần bất kỳ sự can thiệp thủ công nào.