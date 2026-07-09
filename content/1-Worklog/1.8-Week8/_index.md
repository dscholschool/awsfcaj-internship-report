---
title: "Week 8 Worklog"
date: 2024-01-01
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

## OBJECTIVES AND ASSIGNED TASKS

* Complete the labs of Module 5. Apply IAM policies to control access and protect cloud resources.
* Learn about AWS database services through the guidance in Module 6.

## IMPLEMENTATION PROCESS AND ACCUMULATED KNOWLEDGE

This week, combining security barriers with setting up structured data warehouses helped me perfect my mindset regarding a secure and high-performance backend system.

### Identity Security Practice (Lab Module 5)
* **Implementation process:** Manually deployed security labs, directly granting permissions to IAM Users, and assigning IAM Roles to virtual servers.
* **Accumulated knowledge:** Mastered the process of troubleshooting access right leakage and thoroughly applied the "Least Privilege" principle. Completing these labs ensures that the core data system will be strictly protected from unauthorized access flows.

### Cloud Database Architecture (AWS Databases - Module 6)
* **Implementation process:** Studied theory and analyzed the architecture of AWS database types, comparing self-managed databases (Unmanaged) on EC2 virtual servers versus using fully managed database services (Managed Services).
* **Accumulated knowledge:**
  * **Amazon RDS (Relational Database Service):** Clearly understood how AWS automates heavy administrative tasks such as backups, software patching, and High Availability (Multi-AZ) configuration. A key highlight is that in the RDS environment, complex structured data retrieval operations using Stored Procedures and Triggers on SQL Server or Oracle platforms are still supported and operated with maximum performance. This is extremely important when designing ETL data processing flows to prepare inputs for Python (Pandas) libraries before visualizing on Power BI.
  * **Amazon DynamoDB:** Approached NoSQL database management systems with millisecond latency. Learned how to organize data in Key-Value format instead of traditional relational table structures, which is very suitable for processing massive data streams from e-commerce or retail transactions.
  * **Amazon Redshift:** Gained an overview of AWS's Data Warehouse solution, concentrating Petabyte-scale data to serve analytical queries (OLAP) and artificial intelligence.
* **Tutorial Videos:**
  * https://youtu.be/qbrobQZrokY?si=4cNW9UNTkpEOGlUJ
  * https://youtu.be/UvdiRW34aNI?si=DnAUArafHcvZbpoY