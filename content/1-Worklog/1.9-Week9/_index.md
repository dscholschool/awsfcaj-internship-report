---
title: "Week 9 Worklog"
date: 2024-01-01
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

## OBJECTIVES AND ASSIGNED TASKS

* Conduct a comprehensive review and testing of the current prototype's main features before deploying to the cloud environment.
* Improve the user experience flow (registration/login, product search).
* Create a detailed project deployment plan to launch the website and optimize database queries.

## IMPLEMENTATION PROCESS AND ACCUMULATED KNOWLEDGE

This week serves as a critical stepping stone to transition from a locally running prototype to an architecture ready for deployment on AWS infrastructure.

### System Administration and User Experience Construction
* **Implementation process:** Reviewed the entire registration, login, and authentication flow.
* **Accumulated knowledge:** Mastered how to manage user session states.

### Optimal Database Design
* **Implementation process:** Designed and programmed at the system's database layer, focusing on ensuring retrieval performance and data integrity to support complex functions (such as payment, order management) integrated by other team members.
* **Accumulated knowledge:** Delved deep into database optimization techniques. Manually designed and wrote Stored Procedures to encapsulate complex business logic right at the data layer, created Triggers to catch events and automatically update order statuses instantly, and established a scientific Index system. These skills help increase query speed significantly, significantly reducing the processing logic load for the Application Layer, and ensuring absolute data consistency when the system operates with large transaction volumes.

### Infrastructure Architecture Planning
* **Implementation process:** Listed the features needed for completion (Seller Registration, Category Management) and outlined the infrastructure framework in preparation for pushing source code to the actual environment.
* **Accumulated knowledge:** Clearly understood the overall deployment flow. Identified necessary components on AWS (such as EC2 for Backend, S3 for storing 3D files/Digital documents, RDS for database) in preparation for drawing the complete architecture diagram in the following week.