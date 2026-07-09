---
title: "Worklog Tuần 9"
date: 2024-01-01
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

## MỤC TIÊU & NHIỆM VỤ ĐƯỢC GIAO

* Rà soát và kiểm thử toàn diện các chức năng chính của bản mẫu (prototype) hiện tại trước khi đưa lên môi trường đám mây.
* Cải thiện luồng trải nghiệm người dùng (đăng ký/đăng nhập, tìm kiếm sản phẩm).
* Lập kế hoạch triển khai dự án chi tiết để deploy website và tối ưu truy vấn trong cơ sở dữ liệu.

## QUÁ TRÌNH THỰC HIỆN & KIẾN THỨC TÍCH LŨY

Tuần này là bước đệm cực kỳ quan trọng để chuyển đổi từ một bản mẫu chạy nội bộ (local) sang một kiến trúc sẵn sàng triển khai trên hạ tầng AWS.

### Xây dựng Quản trị Hệ thống và Trải nghiệm Người dùng
* **Quá trình thực hiện:** Rà soát lại toàn bộ luồng đăng ký, đăng nhập và xác thực (Authentication).
* **Kiến thức tích lũy:** Nắm bắt được cách quản lý trạng thái phiên làm việc của người dùng.

### Thiết kế Cơ sở dữ liệu Tối ưu
* **Quá trình thực hiện:** Thiết kế và lập trình tại tầng cơ sở dữ liệu của hệ thống, tập trung vào việc đảm bảo hiệu suất truy xuất và tính toàn vẹn dữ liệu để hỗ trợ các chức năng phức tạp (như thanh toán, quản lý đơn hàng) do các thành viên khác tích hợp.
* **Kiến thức tích lũy:** Đi sâu vào kỹ thuật tối ưu hóa cơ sở dữ liệu. Tự tay thiết kế và viết các Stored Procedures để đóng gói các logic tính toán nghiệp vụ phức tạp ngay tại tầng dữ liệu, tạo các Triggers nhằm bắt sự kiện và tự động cập nhật trạng thái đơn hàng một cách tức thời, và thiết lập hệ thống Indexes (chỉ mục) khoa học. Các kỹ năng này giúp tăng tốc độ truy vấn lên nhiều lần, giảm tải đáng kể việc xử lý logic cho phía ứng dụng (Application Layer), và đảm bảo tính nhất quán dữ liệu tuyệt đối khi hệ thống vận hành với khối lượng giao dịch lớn.

### Chuẩn bị Kiến trúc Hạ tầng (Architecture Planning)
* **Quá trình thực hiện:** Liệt kê những tính năng cần hoàn thiện (Seller Registration, Category Management) và lên khung sườn hạ tầng (Architecture) chuẩn bị cho quá trình đẩy mã nguồn lên môi trường thực tế.
* **Kiến thức tích lũy:** Nắm rõ được luồng triển khai tổng thể. Đã xác định được các thành phần cần thiết trên AWS (như EC2 cho Backend, S3 cho lưu trữ file 3D/Tài liệu số, RDS cho cơ sở dữ liệu) để chuẩn bị cho việc vẽ sơ đồ kiến trúc hoàn chỉnh ở tuần tiếp theo.