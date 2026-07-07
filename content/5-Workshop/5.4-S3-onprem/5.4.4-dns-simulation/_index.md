---
title: "Testing S3 upload, preview, and download"
date: 2024-01-01
weight: 4
chapter: false
pre: " <b> 5.4.4 </b> "
---

#### Backend API tests

```bash
curl http://localhost:5000/health
curl http://localhost:5000/api/products
curl -I http://localhost:5000/api/products/<product-id>/thumbnail
# Expected: 200 with Content-Type image/png or image/jpeg
curl -I http://localhost:5000/api/products/<product-id>/preview
curl -I http://localhost:5000/api/products/<product-id>/model
```

#### Web flow tests

- Admin uploads a new document product and a new 3D product — files land in S3 under `products/`.
- Buyer flow: purchase, search, order history, and library all work end to end.
- Download is only allowed after the ownership check passes.
- The Order History download button reuses the library download service — there is no separate `/api/products/:id/download` endpoint.

#### Verify objects in S3

```bash
aws s3 ls s3://marketplace-frontend-thao/products/ --region us-east-1 | tail -20
```

<!-- INSERT FIGURE 5.9: Screenshot of the S3 console listing new objects under products/ after uploading via the web app. -->

<!-- INSERT FIGURE 5.10: Screenshot of the browser showing product thumbnail, 3D preview, and a successful download from the library. -->
