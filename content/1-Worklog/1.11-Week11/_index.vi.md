---
title: "Worklog Tuần 11"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.11. </b> "
---

### Mục tiêu tuần 11:

* Ổn định ứng dụng đã deploy và tạo link demo frontend public sử dụng được.
* Kết nối frontend, backend, database và storage thành một hệ thống hoạt động hoàn chỉnh.
* Chuyển product asset storage từ ổ đĩa local EC2 sang Amazon S3 bằng quyền của IAM Role.
* Debug end-to-end các lỗi auth, quyền admin, download file sản phẩm, preview và truy cập S3.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2   | - Deploy React/Vite frontend lên Vercel và fix SPA routing cho các route trực tiếp như `/login`, `/products` <br> - Cấu hình Vercel rewrites để `/api/*` và `/webhook/*` forward về EC2 backend, tránh lỗi mixed content khi gọi API từ browser | 29/06/2026 | 29/06/2026 | <https://vercel.com/docs/rewrites> |
| 3   | - Sửa lỗi production frontend bundle còn gọi `localhost:3000` (chuyển sang relative path `/api/...`) <br> - Gắn IAM Role cho EC2 instance và tạo quyền S3 giới hạn ở prefix `products/*` trong bucket `marketplace-frontend-thao` | 30/06/2026 | 30/06/2026 | <https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_use_switch-role-ec2.html> |
| 4   | - Cài và test AWS CLI trên EC2, xác nhận các quyền PutObject, ListBucket và DeleteObject với S3 <br> - Refactor backend upload từ `multer.diskStorage` sang `memoryStorage`, thêm S3 helper dùng `@aws-sdk/client-s3` <br> - Cập nhật product/library controllers để upload, stream, preview và download file từ S3 | 01/07/2026 | 01/07/2026 | <https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/> |
| 5   | - Sync các file sản phẩm legacy từ ổ đĩa EC2 lên S3 <br> - Kiểm thử thumbnail sản phẩm, preview/download tài liệu và 3D model preview qua backend API <br> - Debug lỗi download ở order history bằng cách dùng lại library download service thay vì endpoint product download sai | 02/07/2026 | 02/07/2026 | <https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html> |
| 6   | - Cập nhật seed category và UI quản lý category phía admin để hỗ trợ group DOCUMENT và MODEL_3D <br> - Cập nhật sơ đồ kiến trúc thể hiện Vercel hoặc CloudFront là lựa chọn frontend hosting/CDN và S3 là nơi lưu product assets | 03/07/2026 | 03/07/2026 | <https://aws.amazon.com/architecture/> |


### Kết quả đạt được tuần 11:

* Frontend Vercel, backend EC2, RDS PostgreSQL và S3 product storage đã kết nối thành demo cloud hoạt động.
* Sản phẩm mới upload được lưu vào `s3://marketplace-frontend-thao/products/` thay vì `backend/storage/products` trên EC2.
* Backend kiểm tra quyền sở hữu trước khi stream file sản phẩm trả phí từ S3, giữ bucket ở chế độ private.
* Thumbnail sản phẩm, preview/download tài liệu và 3D preview đã được kiểm thử và hoạt động ổn sau khi chuyển sang S3.
* IAM Role được xác minh từ EC2 mà không cần lưu AWS access key dài hạn trong `.env` của backend.
* Giới hạn còn lại: CloudFront/Route 53/WAF vẫn là các thành phần thuộc kiến trúc mục tiêu; Vercel được dùng thay thế thực tế cho frontend hosting/CDN trong giai đoạn demo.
