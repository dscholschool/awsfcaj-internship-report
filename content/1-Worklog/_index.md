---
title: "Week 11 Worklog"
date: 2024-01-01
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

## OBJECTIVES AND ASSIGNED TASKS

* Support the deployment of the entire project source code (Frontend, Backend) and Database from the development environment (Local) to the AWS cloud infrastructure based on the architecture diagram finalized in week 10[cite: 271].
* Participate in supporting team members to configure connections between services (Vercel, EC2, RDS, S3)[cite: 272].
* Perform end-to-end integration testing (End-to-End Testing), especially the payment flow and automatic order status updates[cite: 273].

## IMPLEMENTATION PROCESS AND ACCUMULATED KNOWLEDGE

This week is the most important "hands-on" phase, where all theories and architectural drawings are transformed into actual resources running smoothly on the cloud[cite: 275].

### Coordinating Deployment and Database Optimization (Amazon RDS)
* **Implementation process:** Supported the team in initializing the Amazon RDS PostgreSQL database cluster placed in the Private Subnet[cite: 277]. Directly took charge of migrating the entire table structure, Indexes, as well as pushing Stored Procedures and Triggers from local machines to the actual RDS environment[cite: 278].
* **Accumulated knowledge:** Mastered the process of configuring a Security Group (virtual firewall) to allow the Backend server (EC2) to communicate securely with RDS via port 5432[cite: 279]. Pushing the processing logic code directly down to the database layer helped me verify the actual load capacity and retrieval speed in the cloud[cite: 279].

### Supporting Backend (EC2) and Storage (Amazon S3) Configuration
* **Implementation process:** Participated with team members in setting up the Node.js environment on the EC2 server[cite: 281]. Concurrently, supported the initialization of the S3 Bucket to store 3D model files and PDF documents[cite: 282].
* **Accumulated knowledge:** Applied the core knowledge of Module 5 (IAM) to assign an IAM Role directly to the EC2 instance[cite: 283]. Instead of embedding security credentials (Access Keys) into the Backend source code which could easily cause leaks, the team's system can currently call APIs to upload/download files from S3 automatically and with absolute security thanks to the Role-based authorization mechanism[cite: 284].

### Payment Webhook Integration Testing (SePay)
* **Implementation process:** Joined the whole team in executing practical purchasing scenarios to test the payment feature[cite: 286]. Acted as a log monitor at the database layer[cite: 287].
* **Accumulated knowledge:** When SePay sends a Webhook notification of a successful transaction to the Backend, I directly monitored the activation of Triggers inside RDS[cite: 288]. The results showed that the reconciliation data matched perfectly, the order status was updated automatically in an instant, and file download permissions were successfully unlocked for users without any manual intervention[cite: 289].