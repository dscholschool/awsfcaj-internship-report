---
title: "Week 10 Worklog"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.10. </b> "
---

### Week 10 Objectives:

* Finalize and stabilize the core features of the DaiMarket system (auth, products, categories, purchasing, personal library).
* Test all existing features across the buyer/admin/seller flows at a realistic demo level.
* Deploy and test the AWS services following the current architecture diagram: EC2, RDS PostgreSQL, S3, and IAM Role.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| ---- | ---- | ---- | ---- | ----|
| 2   | - Review the core features: auth, product listing, search, product detail, admin dashboard <br> - Identify the features that must be stabilized before deployment                                                                                                      | 06/22/2026 | 06/22/2026      |
| 3   | - Test the user flow: buyer register/login, browse products, purchase, order history, personal library <br> - Fix the file download flow in order history (reuse the same download service as the Library) <br> - Test 3D preview and document preview/download          | 06/23/2026 | 06/23/2026      |
| 4   | - Finalize the admin/seller flow: categories by DOCUMENT/MODEL_3D group, product management, thumbnail/file/model upload <br> - Update `seed-required.js` safely (upsert only, no deletion of real data) <br> - Assign the admin role via SQL to test admin features        | 06/24/2026 | 06/24/2026      |
| 5   | - Deploy the backend to EC2 Ubuntu (Node.js, Git, PM2) <br> - Create RDS PostgreSQL db.t4g.micro Single-AZ, private access via Security Group <br> - Fix the SSL issue when Prisma 7 connects to RDS (`@prisma/adapter-pg`) <br> - Verify migration/seed and the public API | 06/25/2026 | 06/25/2026      | <https://docs.aws.amazon.com/rds/> |
| 6   | - Create the S3 bucket, use the `products/` prefix for product files <br> - Attach the IAM Role `marketplace-ec2-s3-role` to EC2 (least privilege) <br> - Test S3 upload/list/delete with the AWS CLI from EC2 <br> - Migrate product storage from the EC2 disk to S3 (memoryStorage + AWS SDK) | 06/26/2026 | 06/26/2026      | <https://docs.aws.amazon.com/s3/> |


### Week 10 Achievements:

* The system reached a cloud-deployable MVP state, sufficient for demos and as the foundation of the final Workshop report:
  * The React/Vite frontend runs online on Vercel (replacing CloudFront during the demo phase because the AWS account verification is not completed yet).
  * The Node.js + Express + Prisma backend runs on EC2 with PM2; the public API works through Vercel rewrite/proxy.
  * The database moved to Amazon RDS PostgreSQL: stores users, roles, products, categories, orders, payment methods, order items.
  * Product files, thumbnails, and preview models were migrated to Amazon S3 under the `products/` prefix; the backend reads/streams from S3 after checking permissions.
  * EC2 accesses S3 via the IAM Role `marketplace-ec2-s3-role` (PutObject/GetObject/DeleteObject/ListBucket limited to the `products/` prefix), with no access keys in `.env`.
  * The SePay webhook is integrated at the backend level: API key verification and `DAIM...` order code handling to update orders from PENDING → SUCCESS.

* Bugs found and successfully fixed:
  * Prisma seed threw `P1010/DatabaseAccessDenied` — the root cause was Node/Prisma not using SSL properly when connecting to RDS; debugged with the plain pg driver and configured SSL in the adapter.
  * The original `seed.js` was dangerous (cleared all tables) — created a separate `seed-required.js` that only upserts Role/PaymentMethod/Category.
  * Direct access to `/login` on Vercel returned 404 — added `vercel.json` rewriting every route to `index.html` (SPA routing).
  * Register/Login threw a Network Error — the frontend bundle still called `localhost:3000`; fixed to the relative path `/api/...` with a rewrite to the EC2 backend.
  * Admin `/api/admin/stats` returned 403 — assigned the admin role via SQL and logged out/in again so the new JWT carries the admin role.
  * Order history file download returned 404 — switched to `downloadProductFile` like the Library, calling the correct route `/api/library/:productId/file`.
  * Old product files returned 404 after git pull — restored/synced the needed files and moved long-term storage to S3.
  * Deleting a product with existing orders threw `P2003` (foreign key) — noted that the proper solution is soft delete instead of hard delete.

* Remaining work after week 10: test SePay with a real/properly formatted mock transaction, implement product soft delete, move secrets to SSM Parameter Store/Secrets Manager, configure CloudWatch Logs, and consider moving the frontend to CloudFront once the AWS account is unlocked.
