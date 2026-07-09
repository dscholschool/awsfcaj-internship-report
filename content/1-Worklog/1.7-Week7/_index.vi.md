---
title: "Worklog Tuần 7"
date: 2024-01-01
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

## MỤC TIÊU & NHIỆM VỤ ĐƯỢC GIAO

* Hoàn thành dứt điểm toàn bộ các bài thực hành (lab) của Module 4, tập trung vào thao tác trực tiếp với Amazon S3 và Amazon EBS.
* Bước sang Module 5 để nghiên cứu lý thuyết nền tảng về hệ thống bảo mật của AWS, đặc biệt là dịch vụ quản lý định danh và truy cập (IAM - Identity and Access Management).

## QUÁ TRÌNH THỰC HIỆN & KIẾN THỨC TÍCH LŨY

Tuần thực tập này mang lại giá trị thực tiễn rất cao khi tôi có thể kết nối kiến thức hạ tầng lưu trữ với các phương pháp bảo mật cốt lõi, chuẩn bị sẵn sàng cho việc triển khai các luồng xử lý dữ liệu (data pipelines) an toàn trên đám mây.

### Thực hành Lưu trữ dữ liệu với Amazon S3 và EBS (Lab Module 4)
* **Quá trình thực hiện:** Trực tiếp tạo các S3 Bucket, tải tệp tin lên và tinh chỉnh các quyền truy cập (Bucket Policies). Thực hành tạo ổ cứng ảo EBS, gắn (attach) vào một máy chủ EC2 đang chạy và định dạng phân vùng (format volume) bằng các lệnh Linux để có thể lưu trữ dữ liệu.
* **Kiến thức tích lũy:** Khắc sâu khả năng ứng dụng của Amazon S3 như một Data Lake thực thụ. Đây là giải pháp lý tưởng để lưu trữ an toàn khối lượng lớn dữ liệu thô, dữ liệu bán cấu trúc từ các ngành có lưu lượng giao dịch cao như bán lẻ, thương mại điện tử hay ngân hàng. Việc thành thạo S3 giúp tôi hiểu rõ luồng luân chuyển dữ liệu: từ việc tập trung dữ liệu tại Bucket, cho đến khi trích xuất và biến đổi (transform) bằng Python (Pandas) để chuẩn bị cho việc xây dựng các dashboard trực quan trên Power BI.

### Kiến trúc Quản lý Định danh và Truy cập (AWS IAM)
* **Quá trình thực hiện:** Nghiên cứu kiến trúc của dịch vụ IAM, cách AWS kiểm soát ai (Identity) được phép làm gì (Access) trên hệ thống đám mây.
* **Kiến thức tích lũy:** Nắm vững 4 thành phần cốt lõi của IAM:
  * **IAM Users & Groups:** Phân quyền quản trị cho con người. Học cách cấp thông tin đăng nhập Console cho người dùng và nhóm họ lại (ví dụ: nhóm Admin, nhóm Data, nhóm Developer) để dễ dàng quản lý quyền hạn tập trung.
  * **IAM Roles (Vai trò):** Đây là một khái niệm mang tính đột phá. Thay vì nhúng tĩnh các thông tin đăng nhập (như Access Key) vào trong mã nguồn của ứng dụng, tôi học được cách cấp một IAM Role cho máy chủ EC2. Khi EC2 có Role này, nó có thể truy cập an toàn vào S3 hoặc các dịch vụ khác một cách tự động thông qua cơ chế cấp phát token tạm thời. Kỹ thuật này cực kỳ quan trọng để bảo vệ thông tin xác thực khi xây dựng các hệ thống dữ liệu phân tán nhiều điểm (như các hệ thống CRM hay quản lý giao dịch liên miền) hoặc khi gọi các Stored Procedures và Triggers từ cơ sở dữ liệu đám mây.
  * **IAM Policies (Chính sách):** Nắm vững cấu trúc khai báo JSON của một Policy bao gồm: Effect (Allow/Deny), Action (Hành động được phép, ví dụ: s3:GetObject), và Resource (Tài nguyên đích).
* **Video hướng dẫn:** https://youtu.be/N_vlJGAqZxo?si=-suE6TTdzW4aCqXX

### Tư duy Bảo mật "Quyền tối thiểu" (Least Privilege)
* **Quá trình thực hiện:** Đọc hiểu và tự tay viết các đoạn JSON IAM Policy để cấp quyền truy cập chính xác vào một thư mục cụ thể trong S3 Bucket thay vì toàn bộ Bucket.
* **Kiến thức tích lũy:** Thấm nhuần triết lý Zero Trust và nguyên tắc Least Privilege (cấp quyền vừa đủ để làm việc). Trong môi trường doanh nghiệp thực tế, việc siết chặt quyền hạn bằng IAM Policy giúp ngăn chặn rủi ro rò rỉ hoặc mất mát dữ liệu nhạy cảm do lỗi thao tác của người dùng.