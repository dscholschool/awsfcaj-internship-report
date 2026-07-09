---
title: "Week 5 Worklog"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

## OBJECTIVES AND ASSIGNED TASKS

* Start practicing the core lab series of Module 3 regarding the AWS EC2 cloud computing service.
* Complete the labs sequentially, aiming to reach Lab 57 by the end of this week.
* Apply learned theory to manually provision, configure, and manage the lifecycle of virtual servers.

## IMPLEMENTATION PROCESS AND ACCUMULATED KNOWLEDGE

This week marks a significant transition from establishing network infrastructure to directly operating compute resources. Mastering EC2 opens up the capability to deploy complex distributed data architectures on the cloud.

### EC2 Provisioning & SSH Access
* **Implementation process:** Practiced the steps of selecting an Amazon Machine Image (AMI), determining the appropriate Instance Type, and setting up storage (EBS).
* **Accumulated knowledge:** Mastered the skills of using Terminal/PuTTY combined with a Private Key (.pem) to establish secure SSH connections into Linux servers. Configuring Security Groups accurately is the decisive factor for successful connection without creating security vulnerabilities.

### Configuration Automation with EC2 User Data
* **Implementation process:** This is an extremely powerful technique applied in the labs. Instead of SSH-ing into each machine to type installation commands manually, using scripts (shell scripts) in the User Data field helps the server automatically install web servers (Apache/Nginx) or necessary libraries immediately upon startup.
* **Accumulated knowledge:** This skill is very useful when needing to quickly set up a standardized server environment to deploy powerful database management systems, ready for programming complex data processing logic using Stored Procedures or Triggers directly on the cloud.

### Instance Lifecycle Management
* **Implementation process:** Practiced operations such as Start, Stop, Reboot, and Terminate for servers.
* **Accumulated knowledge:** This process helps reinforce the FinOps (Cloud Financial Management) mindset. Understanding AWS billing principles: when the server is in a Stopped state, CPU/RAM fees stop, but the accompanying storage space (EBS volume) continues to consume budget. This forms a habit of strict resource control, ensuring cost-efficiency for large-scale systems.

### Instance Metadata Analysis
* **Implementation process:** Practiced querying internal server information (such as Public IP, Private IP, Instance ID) by using the special IP address 169.254.169.254 directly from inside the EC2 instance.
* **Accumulated knowledge:** This serves as a foundation for automating applications that are capable of self-awareness regarding the environment in which they are running.