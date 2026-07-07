---
title: "Dọn dẹp, kiểm soát chi phí và hướng phát triển"
date: 2024-01-01
weight: 6
chapter: false
pre: " <b> 5.6. </b> "
---

#### Quyết định thiết kế tiết kiệm chi phí

- Không dùng NAT Gateway, ALB, Multi-AZ RDS, WAF trả phí hay RDS Proxy — bản demo chạy với footprint nhỏ nhất có thể.
- Bật AWS Budget alerts để phát hiện chi phí bất thường.
- CloudFront, Route 53 và ACM để lại sau khi giải quyết xong vấn đề xác minh tài khoản.

#### Ước tính chi phí hàng tháng

TODO: Chèn ảnh AWS Billing / Cost Explorer và chi phí ước tính hàng tháng cho EC2, RDS, S3, data transfer và Vercel.

| Dịch vụ | Chi phí ước tính/tháng |
| --- | --- |
| EC2 (backend) | [UPDATE COST from AWS Billing/Pricing Calculator] |
| RDS PostgreSQL | [UPDATE COST from AWS Billing/Pricing Calculator] |
| S3 (lưu trữ sản phẩm) | [UPDATE COST from AWS Billing/Pricing Calculator] |
| Data transfer | [UPDATE COST from AWS Billing/Pricing Calculator] |
| Vercel (frontend) | [UPDATE COST from AWS Billing/Pricing Calculator] |

#### Dọn dẹp sau khi chấm điểm

- Stop hoặc terminate EC2 instance.
- Xóa RDS instance (snapshot lần cuối nếu cần giữ dữ liệu).
- Empty và xóa S3 bucket, hoặc chỉ giữ các object `products/` cần thiết.
- Gỡ IAM role và inline policy.
- Xóa project Vercel hoặc tạm dừng deployment.

#### Hướng phát triển tiếp theo

- HTTPS cho backend qua custom domain với proxy, ALB hoặc API Gateway.
- Presigned URL để download trực tiếp từ S3 có giới hạn thời gian.
- Chuyển secrets sang SSM Parameter Store hoặc Secrets Manager.
- CloudWatch logs, metrics và alarms cho backend.
- Soft delete cho sản phẩm đã có trong đơn hàng.
- Pipeline CI/CD cho backend và frontend.
