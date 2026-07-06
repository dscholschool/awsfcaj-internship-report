---
title: "Week 11 Worklog"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.11. </b> "
---

### Week 11 Objectives:

* Stabilize the deployed application and make the web demo usable through a public frontend URL.
* Connect the frontend, backend, database, and storage layers into one complete working system.
* Move product asset storage from the EC2 local disk to Amazon S3 using IAM Role permissions.
* Debug end-to-end issues in authentication, admin access, product file download, preview, and S3 access.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| ---- | ---- | ---- | ---- | ----|
| 2   | - Deploy the React/Vite frontend to Vercel and fix SPA routing so direct URLs such as `/login` and `/products` work <br> - Configure Vercel rewrites so `/api/*` and `/webhook/*` are forwarded to the EC2 backend, avoiding mixed-content API calls from the browser | 06/29/2026 | 06/29/2026 | <https://vercel.com/docs/rewrites> |
| 3   | - Fix the frontend API base URL issue where the production bundle still called `localhost:3000` (switch to relative `/api/...` paths) <br> - Assign the IAM Role to the EC2 instance and create limited S3 permissions for the `products/*` prefix in the bucket `marketplace-frontend-thao` | 06/30/2026 | 06/30/2026 | <https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_use_switch-role-ec2.html> |
| 4   | - Install and test the AWS CLI on EC2, confirming PutObject, ListBucket, and DeleteObject permissions to S3 <br> - Refactor backend upload from `multer.diskStorage` to `memoryStorage`, add an S3 helper using `@aws-sdk/client-s3` <br> - Update product/library controllers to upload, stream, preview, and download files from S3 | 07/01/2026 | 07/01/2026 | <https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/> |
| 5   | - Sync legacy product files from the EC2 disk to S3 <br> - Verify product thumbnails, document preview/download, and 3D model preview through backend APIs <br> - Debug buyer order history download by reusing the library download service instead of the incorrect product download endpoint | 07/02/2026 | 07/02/2026 | <https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html> |
| 6   | - Update category seed data and the admin category UI to support the DOCUMENT and MODEL_3D category groups <br> - Update the architecture diagram to show Vercel or CloudFront as frontend hosting/CDN options and S3 as product asset storage | 07/03/2026 | 07/03/2026 | <https://aws.amazon.com/architecture/> |


### Week 11 Achievements:

* The Vercel frontend, EC2 backend, RDS PostgreSQL, and S3 product storage were connected into a working cloud demo.
* New product uploads are stored under `s3://marketplace-frontend-thao/products/` instead of `backend/storage/products` on EC2.
* The backend verifies ownership before streaming paid product files from S3, keeping the bucket private.
* Product thumbnail loading, document preview/download, and 3D preview were tested and confirmed after the migration to S3.
* IAM Role access was verified from EC2 without storing long-term AWS access keys in the backend environment (`.env`).
* Known limitation: CloudFront/Route 53/WAF were kept as target architecture items; Vercel is used as the practical frontend hosting/CDN substitute for the demo.
