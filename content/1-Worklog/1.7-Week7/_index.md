---
title: "Week 7 Worklog"
date: 2024-01-01
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

## OBJECTIVES AND ASSIGNED TASKS

* Finish all remaining practical labs of Module 4, focusing on hands-on operations with Amazon S3 and Amazon EBS.
* Move to Module 5 to study the foundational theory of AWS security systems, specifically the Identity and Access Management (IAM) service.

## IMPLEMENTATION PROCESS AND ACCUMULATED KNOWLEDGE

This internship week provided high practical value, allowing me to connect storage infrastructure knowledge with core security methods, preparing for the deployment of secure data pipelines on the cloud.

### Practicing Data Storage with Amazon S3 and EBS (Lab Module 4)
* **Implementation process:** Directly created S3 Buckets, uploaded files, and fine-tuned access permissions (Bucket Policies). Practiced creating virtual EBS hard drives, attaching them to a running EC2 instance, and formatting partitions using Linux commands to enable data storage.
* **Accumulated knowledge:** Deepened the understanding of Amazon S3's application as a true Data Lake. This is an ideal solution for safely storing large volumes of raw and semi-structured data from transaction-heavy industries like retail, e-commerce, or banking. Mastering S3 helps me clearly understand the data flow: from centralizing data in Buckets to extracting and transforming it using Python (Pandas) to prepare for building visual dashboards on Power BI.

### Identity and Access Management Architecture (AWS IAM)
* **Implementation process:** Researched the IAM service architecture, how AWS controls who (Identity) is allowed to do what (Access) on the cloud system.
* **Accumulated knowledge:** Mastered the 4 core components of IAM:
  * **IAM Users & Groups:** Human administration authorization. Learned how to provide Console login credentials for users and group them (e.g., Admin group, Data group, Developer group) for centralized privilege management.
  * **IAM Roles:** This is a breakthrough concept. Instead of statically embedding credentials (like Access Keys) into application source code, I learned to assign an IAM Role to an EC2 instance. When an EC2 instance has this Role, it can safely access S3 or other services automatically via a temporary token issuance mechanism. This technique is extremely important for protecting credentials when building distributed data systems (like CRM or cross-domain transaction management systems) or when calling Stored Procedures and Triggers from cloud databases.
  * **IAM Policies:** Mastered the JSON declaration structure of a Policy, including: Effect (Allow/Deny), Action (e.g., s3:GetObject), and Resource (target resource).
* **Tutorial Video:** https://youtu.be/N_vlJGAqZxo?si=-suE6TTdzW4aCqXX

### "Least Privilege" Security Mindset
* **Implementation process:** Read, understood, and manually wrote JSON IAM Policy snippets to grant precise access to a specific folder within an S3 Bucket instead of the entire Bucket.
* **Accumulated knowledge:** Imbued with the Zero Trust philosophy and the "Least Privilege" principle (granting just enough permissions to work). In a real-world enterprise environment, tightening permissions via IAM Policy helps prevent risks of data leakage or loss due to user operational errors.