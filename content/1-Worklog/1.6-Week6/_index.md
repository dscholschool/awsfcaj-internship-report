---
title: "Week 6 Worklog"
date: 2024-01-01
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

## OBJECTIVES AND ASSIGNED TASKS

* Completely finish the remaining labs of Module 3 regarding the EC2 compute service.
* Shift focus to Module 4 to delve into AWS storage services, creating a premise for building large-scale data warehouses.

## IMPLEMENTATION PROCESS AND ACCUMULATED KNOWLEDGE

This week serves as a hinge point, combining the computing power of EC2 with diverse storage solutions, helping to form a complete architecture for practical projects.

### Completing Advanced EC2 Configuration (Module 3)
* **Implementation process:** Processed the final labs of Module 3, focusing on creating backups (Snapshots) for virtual server hard drives and practicing data restoration from these backups.
* **Accumulated knowledge:** Deeply ingrained the system data integrity protection process. Mastering Snapshot creation operations ensures that server configurations can be quickly replicated or immediately restored when incidents occur, maintaining high availability for the application environment.

### Distinguishing Core Cloud Storage Types (Module 4)
* **Implementation process:** Researched and compared three foundational AWS storage services: Amazon EBS (Block Storage), Amazon EFS (File Storage), and Amazon S3 (Object Storage).
* **Accumulated knowledge:** Mastered technical characteristics to correctly apply the service for each specific problem:
  * **Amazon EBS (Elastic Block Store):** Understood this is a virtual hard drive attached directly to an EC2 instance. It is suitable for storing the OS or serving as physical storage for Database Management Systems requiring high Read/Write speed (IOPS) and ultra-low latency.
  * **Amazon S3 (Simple Storage Service):** Approached the Object Storage model. Unlike traditional directory architectures, S3 stores data as "Objects" within "Buckets". This is an ideal architecture for building massive Data Lakes, where raw and semi-structured data from transaction-heavy industries like retail, e-commerce, or banking transaction history are concentrated. This data can then be easily extracted and processed using tools like Python (Pandas) before being visualized on Power BI, or served directly for training K-means clustering models and decision trees.
* **Tutorial Video:** https://youtu.be/_yunukwcAwc?si=JVG6PhQaUkZ-xG-A

### Storage Cost Optimization (Storage FinOps)
* **Implementation process:** Researched Storage Classes within the Amazon S3 service.
* **Accumulated knowledge:** Applied flexible cost management thinking by classifying data lifecycles. Learned how to configure automatic transitions for infrequently used data from S3 Standard to S3 Standard-IA (Infrequent Access) to minimize storage costs per GB, or use Amazon Glacier for long-term archiving of reports and historical log files at highly optimal price points.
* **Tutorial Video:** https://youtu.be/mPBjB6Ltl_Q?si=wkVTH1muEnh_n4yC