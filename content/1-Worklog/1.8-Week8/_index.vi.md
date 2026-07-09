---
title: "Worklog Tuần 8"
date: 2024-01-01
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

## MỤC TIÊU & NHIỆM VỤ ĐƯỢC GIAO

* Hoàn thành các bài lab của Module 5. Vận dụng các chính sách IAM để kiểm soát truy cập và bảo vệ tài nguyên trên đám mây.
* Tìm hiểu về dịch vụ cơ sở dữ liệu của AWS thông qua nội dung hướng dẫn trong Module 6.

## QUÁ TRÌNH THỰC HIỆN & KIẾN THỨC TÍCH LŨY

Trong tuần này, việc kết hợp giữa rào chắn bảo mật và thiết lập các kho lưu trữ dữ liệu có cấu trúc đã giúp tôi hoàn thiện tư duy về một hệ thống backend an toàn và hiệu suất cao.

### Nghiệm thu Thực hành Bảo mật Định danh (Lab Module 5)
* **Quá trình thực hiện:** Tự tay triển khai các bài lab bảo mật, phân quyền trực tiếp cho các IAM Users và gán các IAM Roles cho máy chủ ảo.
* **Kiến thức tích lũy:** Nắm vững quy trình xử lý sự cố rò rỉ quyền truy cập và áp dụng triệt để nguyên tắc "Quyền tối thiểu" (Least Privilege). Việc hoàn thành các lab này giúp đảm bảo rằng hệ thống dữ liệu cốt lõi sau này sẽ được bảo vệ nghiêm ngặt khỏi các luồng truy cập trái phép.

### Kiến trúc Cơ sở dữ liệu Đám mây (AWS Databases - Module 6)
* **Quá trình thực hiện:** Nghiên cứu lý thuyết và phân tích kiến trúc của các loại hình cơ sở dữ liệu trên AWS, so sánh giữa việc tự quản lý cơ sở dữ liệu (Unmanaged) trên máy chủ ảo EC2 và sử dụng dịch vụ cơ sở dữ liệu được quản lý toàn diện (Managed Services).
* **Kiến thức tích lũy:**
  * **Amazon RDS (Relational Database Service):** Hiểu rõ cách AWS tự động hóa các tác vụ quản trị nặng nề như sao lưu (backup), vá lỗi phần mềm (patching) và cấu hình tính sẵn sàng cao (Multi-AZ). Điểm nhấn ở đây là trên môi trường RDS, các nghiệp vụ truy xuất dữ liệu có cấu trúc phức tạp sử dụng Stored Procedures và Triggers trên nền tảng SQL Server hoặc Oracle vẫn được hỗ trợ và vận hành với hiệu suất tối đa. Điều này vô cùng quan trọng khi thiết kế các luồng xử lý dữ liệu (ETL) để chuẩn bị đầu vào cho các thư viện Python (Pandas) trước khi trực quan hóa trên Power BI.
  * **Amazon DynamoDB:** Tiếp cận với hệ quản trị cơ sở dữ liệu NoSQL với độ trễ tính bằng mili-giây. Học cách tổ chức dữ liệu theo dạng Key-Value thay vì cấu trúc bảng quan hệ truyền thống, rất phù hợp để xử lý luồng dữ liệu khổng lồ từ các giao dịch thương mại điện tử hoặc bán lẻ.
  * **Amazon Redshift:** Có cái nhìn tổng quan về giải pháp Data Warehouse (Kho dữ liệu) của AWS, nơi tập trung dữ liệu quy mô Petabyte phục vụ cho các truy vấn phân tích (OLAP) và trí tuệ nhân tạo.
* **Video hướng dẫn:**
  * https://youtu.be/qbrobQZrokY?si=4cNW9UNTkpEOGlUJ
  * https://youtu.be/UvdiRW34aNI?si=DnAUArafHcvZbpoY