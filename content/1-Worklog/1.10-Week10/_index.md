---
title: "Week 10 Worklog"
date: 2024-01-01
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

## OBJECTIVES AND ASSIGNED TASKS

* Use the draw.io tool to design the overall system architecture diagram for the entire project on the AWS environment.
* Consult with administrators (admins) for technical feedback, fine-tune, and finalize the diagram.
* Identify and standardize the communication workflows between Frontend, Backend, Database, and third-party services.

## IMPLEMENTATION PROCESS AND ACCUMULATED KNOWLEDGE

This week, designing the architecture was not just about placing icons but a deep process of system thinking. Through two rounds of submission and modification based on feedback from the admins, I finalized the architecture with 5 core processing workflows:

### 1. Building a Public Buffer for Frontend & API
* **Implementation process:** Set up the user access flow from the Frontend (hosted independently on Vercel). All API requests will pass through the Internet Gateway (IGW) and be controlled by the Application Load Balancer (ALB) located in the Public Subnet.
* **Accumulated knowledge:** Clearly understood how the ALB acts as a secure "buffer zone" (DMZ) to distribute network traffic before it goes deeper into the system.

### 2. Absolute Security for the Compute Block (Private Network)
* **Implementation process:** Designed the Backend server cluster (Node.js/Express) running on EC2 and automated with an Auto Scaling Group.
* **Accumulated knowledge:** The key point is that this entire block is completely hidden inside the Private Subnet with no direct connection to the Internet, ensuring maximum security for the core business logic hub (authentication, authorization, product management).

### 3. Optimizing Database Performance
* **Implementation process:** Allocated Amazon RDS PostgreSQL into a separate, independent Private Subnet, only allowing EC2 to communicate via an internal Security Group (port 5432).
* **Accumulated knowledge:** Instead of putting all the computation load on the Node.js Backend, the team fully leveraged the power of the database by designing Stored Procedures and Triggers directly on RDS. This approach helps automatically and rapidly process complex order status reconciliation logics.

### 4. Establishing an Internal Tunnel (VPC Endpoint) for Storage
* **Implementation process:** Selected Amazon S3 (Private mode) to store digital assets (PDF, DOCX, 3D Models).
* **Accumulated knowledge:** To allow the EC2 instance inside the Private Subnet to safely download files without incurring the costs of passing through the NAT Gateway, I configured an S3 Gateway Endpoint to create an internal network tunnel. Concurrently, strict IAM Roles were applied to the EC2 instance to limit access precisely to the required product directories.

### 5. Payment Webhook Flow Automation
* **Implementation process & knowledge:** Mapped the real-time communication flow for the SePay Webhook. When a customer successfully completes a payment, the signal from the third party penetrates the IGW, passes through the ALB into the EC2 instance to trigger the logic that updates the order status and automatically unlocks digital file download permissions for the buyer.

### Cloud Infrastructure Architecture Diagram (AWS Architecture)

![AWS Cloud Architecture](tuan10-arch.png)