---
title: "Worklog Tuần 10"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.10. </b> "
---

### Mục tiêu tuần 10:

* Hoàn thiện và ổn định các chức năng cốt lõi của hệ thống DaiMarket (auth, sản phẩm, danh mục, mua hàng, thư viện cá nhân).
* Kiểm thử toàn bộ chức năng hiện có theo các luồng buyer/admin/seller ở mức demo thực tế.
* Triển khai và kiểm thử các dịch vụ AWS theo sơ đồ kiến trúc hiện tại: EC2, RDS PostgreSQL, S3 và IAM Role.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2   | - Rà soát các chức năng cốt lõi: auth, product listing, search, product detail, admin dashboard <br> - Xác định các chức năng cần ổn định trước khi deploy                                                                                                          | 22/06/2026   | 22/06/2026      |
| 3   | - Kiểm thử user flow: buyer đăng ký/đăng nhập, xem sản phẩm, mua hàng, lịch sử mua hàng, thư viện cá nhân <br> - Sửa lỗi tải file trong lịch sử mua hàng (dùng chung service download với Library) <br> - Kiểm thử 3D preview và preview/download tài liệu             | 23/06/2026   | 23/06/2026      |
| 4   | - Hoàn thiện admin/seller flow: category theo group DOCUMENT/MODEL_3D, product management, upload thumbnail/file/model <br> - Cập nhật `seed-required.js` theo hướng an toàn (upsert, không xóa dữ liệu thật) <br> - Gán role admin bằng SQL để kiểm thử chức năng quản trị | 24/06/2026   | 24/06/2026      |
| 5   | - Deploy backend lên EC2 Ubuntu (Node.js, Git, PM2) <br> - Tạo RDS PostgreSQL db.t4g.micro Single-AZ, kết nối private qua Security Group <br> - Xử lý lỗi SSL khi Prisma 7 kết nối RDS (`@prisma/adapter-pg`) <br> - Kiểm tra migration/seed và API public               | 25/06/2026   | 25/06/2026      | <https://docs.aws.amazon.com/rds/> |
| 6   | - Tạo S3 bucket, dùng prefix `products/` lưu file sản phẩm <br> - Attach IAM Role `marketplace-ec2-s3-role` cho EC2 (least privilege) <br> - Test upload/list/delete S3 bằng AWS CLI từ EC2 <br> - Chuyển product storage từ ổ đĩa EC2 sang S3 (memoryStorage + AWS SDK)   | 26/06/2026   | 26/06/2026      | <https://docs.aws.amazon.com/s3/> |


### Kết quả đạt được tuần 10:

* Hệ thống đạt trạng thái MVP deploy được trên cloud, đủ phục vụ demo và làm nền tảng cho báo cáo Workshop cuối:
  * Frontend React/Vite chạy online trên Vercel (thay CloudFront trong giai đoạn demo vì tài khoản AWS chưa xác minh xong).
  * Backend Node.js + Express + Prisma chạy trên EC2 bằng PM2, API public hoạt động qua rewrite/proxy từ Vercel.
  * Database chuyển sang Amazon RDS PostgreSQL: lưu user, role, product, category, order, payment method, order item.
  * File sản phẩm, thumbnail, preview model đã chuyển sang Amazon S3 prefix `products/`; backend đọc/stream từ S3 sau khi kiểm tra quyền.
  * EC2 truy cập S3 bằng IAM Role `marketplace-ec2-s3-role` (PutObject/GetObject/DeleteObject/ListBucket giới hạn trong prefix `products/`), không cần access key trong `.env`.
  * SePay webhook tích hợp ở mức backend: xác thực API key, xử lý mã đơn `DAIM...` để cập nhật order PENDING → SUCCESS.

* Các lỗi đã phát hiện và fix thành công:
  * Prisma seed báo `P1010/DatabaseAccessDenied` — nguyên nhân gốc là Node/Prisma kết nối RDS chưa dùng SSL đúng cách; debug bằng pg thuần và cấu hình SSL trong adapter.
  * `seed.js` gốc nguy hiểm (clear all tables) — tạo `seed-required.js` riêng chỉ upsert Role/PaymentMethod/Category.
  * Truy cập trực tiếp `/login` trên Vercel bị 404 — thêm `vercel.json` rewrite mọi route về `index.html` (SPA routing).
  * Register/Login bị Network Error — frontend bundle còn gọi `localhost:3000`, sửa về relative path `/api/...` và rewrite tới backend EC2.
  * Admin `/api/admin/stats` trả 403 — gán role admin bằng SQL, logout/login lại để JWT mới có role admin.
  * Order history tải file 404 — sửa dùng `downloadProductFile` giống Library, gọi đúng route `/api/library/:productId/file`.
  * File product cũ 404 sau git pull — restore/sync file và chuyển hướng lưu trữ dài hạn sang S3.
  * Xóa product đã có order bị `P2003` (foreign key) — ghi nhận hướng xử lý chuẩn là soft delete thay vì hard delete.

* Việc còn lại sau tuần 10: kiểm thử SePay với giao dịch thật/mock đúng format, soft delete product, đưa secret vào SSM Parameter Store/Secrets Manager, cấu hình CloudWatch Logs và cân nhắc chuyển frontend sang CloudFront khi tài khoản AWS được mở.
