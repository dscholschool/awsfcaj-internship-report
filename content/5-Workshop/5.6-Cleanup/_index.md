---
title: "Cleanup, cost control, and next steps"
date: 2024-01-01
weight: 6
chapter: false
pre: " <b> 5.6. </b> "
---

#### Cost-aware design decisions

- No NAT Gateway, no ALB, no Multi-AZ RDS, no paid WAF, no RDS Proxy — the demo runs on the smallest viable footprint.
- AWS Budget alerts are enabled to catch unexpected spend.
- CloudFront, Route 53, and ACM are deferred until the account verification issue is resolved.

#### Monthly cost estimate

TODO: Insert AWS Billing / Cost Explorer screenshot and monthly estimated cost for EC2, RDS, S3, data transfer, and Vercel.

| Service | Estimated monthly cost |
| --- | --- |
| EC2 (backend) | [UPDATE COST from AWS Billing/Pricing Calculator] |
| RDS PostgreSQL | [UPDATE COST from AWS Billing/Pricing Calculator] |
| S3 (product storage) | [UPDATE COST from AWS Billing/Pricing Calculator] |
| Data transfer | [UPDATE COST from AWS Billing/Pricing Calculator] |
| Vercel (frontend) | [UPDATE COST from AWS Billing/Pricing Calculator] |

#### Cleanup after grading

- Stop or terminate the EC2 instance.
- Delete the RDS instance (take a final snapshot if the data is needed later).
- Empty and delete the S3 bucket, or keep only the `products/` objects that matter.
- Remove the IAM role and inline policy.
- Delete the Vercel project or pause deployments.

#### Next improvements

- HTTPS for the backend via a custom domain with a proxy, ALB, or API Gateway.
- Presigned URLs for direct, time-limited S3 downloads.
- Move secrets to SSM Parameter Store or Secrets Manager.
- CloudWatch logs, metrics, and alarms for the backend.
- Soft delete for products referenced by orders.
- CI/CD pipeline for backend and frontend deployments.
