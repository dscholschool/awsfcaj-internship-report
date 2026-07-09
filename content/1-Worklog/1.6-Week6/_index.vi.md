---
title: "Worklog Tuần 6"
date: 2024-01-01
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

## MỤC TIÊU & NHIỆM VỤ ĐƯỢC GIAO

* Hoàn thành dứt điểm các bài lab còn lại của Module 3 về dịch vụ tính toán EC2.
* Chuyển trọng tâm sang Module 4 để tìm hiểu sâu về các dịch vụ lưu trữ (Storage) của AWS, tạo tiền đề cho việc xây dựng các kho dữ liệu quy mô lớn.

## QUÁ TRÌNH THỰC HIỆN & KIẾN THỨC TÍCH LŨY

Tuần này đóng vai trò bản lề khi kết hợp sức mạnh tính toán của EC2 với các giải pháp lưu trữ đa dạng, giúp hình thành kiến trúc hoàn chỉnh cho các dự án thực tế.

### Hoàn thiện Cấu hình nâng cao cho EC2 (Module 3)
* **Quá trình thực hiện:** Xử lý các bài lab cuối của Module 3, tập trung vào việc tạo các bản sao lưu (Snapshots) cho ổ cứng máy chủ ảo và thực hành khôi phục dữ liệu từ các bản sao lưu này.
* **Kiến thức tích lũy:** Khắc sâu quy trình bảo vệ toàn vẹn dữ liệu hệ thống. Việc thành thạo thao tác tạo Snapshot giúp đảm bảo các cấu hình máy chủ có thể được nhân bản nhanh chóng hoặc phục hồi ngay lập tức khi xảy ra sự cố, duy trì tính sẵn sàng cao cho môi trường ứng dụng.

### Phân biệt các loại hình Lưu trữ Đám mây cốt lõi (Module 4)
* **Quá trình thực hiện:** Nghiên cứu và so sánh ba dịch vụ lưu trữ nền tảng của AWS: Amazon EBS (Block Storage), Amazon EFS (File Storage), và Amazon S3 (Object Storage).
* **Kiến thức tích lũy:** Nắm vững đặc tính kỹ thuật để áp dụng đúng dịch vụ cho từng bài toán:
  * **Amazon EBS (Elastic Block Store):** Hiểu rõ đây là ổ cứng ảo gắn trực tiếp vào máy chủ EC2. Nó phù hợp để lưu trữ hệ điều hành hoặc làm nơi lưu trữ vật lý cho các hệ quản trị cơ sở dữ liệu đòi hỏi tốc độ đọc/ghi (IOPS) cao và độ trễ cực thấp.
  * **Amazon S3 (Simple Storage Service):** Tiếp cận với mô hình Object Storage. Khác với kiến trúc thư mục truyền thống, S3 lưu trữ dữ liệu dưới dạng "Object" (đối tượng) nằm trong các "Bucket". Đây là kiến trúc lý tưởng để xây dựng các Data Lake khổng lồ, nơi tập trung dữ liệu thô, dữ liệu bán cấu trúc từ các ngành có khối lượng giao dịch lớn như bán lẻ, thương mại điện tử hay lịch sử giao dịch ngân hàng. Dữ liệu này sau đó có thể dễ dàng được trích xuất (extract) và xử lý bằng các công cụ như Python (Pandas) trước khi đưa lên Power BI để trực quan hóa, hoặc phục vụ trực tiếp cho việc huấn luyện các mô hình phân cụm K-means và cây quyết định.
* **Video hướng dẫn:** https://youtu.be/_yunukwcAwc?si=JVG6PhQaUkZ-xG-A

### Tối ưu chi phí Lưu trữ (Storage FinOps)
* **Quá trình thực hiện:** Nghiên cứu các hạng lưu trữ (Storage Classes) bên trong dịch vụ Amazon S3.
* **Kiến thức tích lũy:** Áp dụng tư duy quản lý chi phí linh hoạt bằng cách phân loại vòng đời dữ liệu. Nắm được cách cấu hình chuyển tự động dữ liệu ít sử dụng từ S3 Standard sang S3 Standard-IA (Infrequent Access) để giảm thiểu chi phí lưu trữ trên mỗi GB, hoặc sử dụng Amazon Glacier để lưu trữ dài hạn (Archive) các báo cáo và tệp log lịch sử với mức giá cực kỳ tối ưu.
* **Video hướng dẫn:** https://youtu.be/mPBjB6Ltl_Q?si=wkVTH1muEnh_n4yC