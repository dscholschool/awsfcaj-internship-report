---
title: "Week 4 Worklog"
date: 2024-01-01
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

## OBJECTIVES AND ASSIGNED TASKS

* Completely finish all remaining labs of Module 2 to wrap up the network infrastructure knowledge.
* Transition to Module 3: Study the theory, core architecture, and configuration parameters of AWS's flagship cloud computing service, AWS EC2 (Elastic Compute Cloud).

## IMPLEMENTATION PROCESS AND ACCUMULATED KNOWLEDGE

This week, completing the virtual network journey and starting to approach Compute resources helped me form a more coherent systems mindset.

### Module 2 Acceptance and FinOps Cleanup
* **Implementation process:** Re-checked all final routing flows in the VPC network, ensuring connections between Public/Private Subnets operate smoothly, then proceeded to release resources.
* **Accumulated knowledge:** Deeply ingrained a vital principle when working on the Cloud: **Delete resources when not in use**. Components like AWS NAT Gateway or Elastic IP (static IP) charge hourly even when the server isn't processing data. Proactively terminating and deleting these resources after completing the Module 2 lab series helped me practice extremely serious budget management skills, avoiding wasteful Credit consumption.

### Mastering Cloud Virtual Server Concepts (AWS EC2 Fundamentals)
* **Implementation process:** Analyzed the architecture of an EC2 entity (Instance) and how it replaces traditional physical servers in enterprises thanks to its flexible scalability.
* **Accumulated knowledge:**
  * **Amazon Machine Image (AMI):** Understood clearly that AMI acts as a "template" pre-loaded with the Operating System (like Ubuntu, Amazon Linux, Windows Server) and foundational software configurations. Instead of spending hours installing an OS for a physical server, AMI helps clone hundreds of identically configured servers in just a few minutes.
  * **Server Classification Mindset (Instance Types):** Mastered how AWS names instances to select the most optimal resources. For example, understanding a name structure like `t3.micro` (where `t` is the General Purpose family - cost-effective; `3` is the hardware generation; `micro` is the CPU/RAM resource size). I distinguished when to use the `C` family (Compute Optimized - for algorithms), the `R` family (Memory Optimized - for Big Data/Database processing), and the `T` family for testing or small web servers.
* **Tutorial Video:** https://youtu.be/e7XeKdOVq40?si=DS2_HgBf6vSKbDkP

### Advanced Security and Authentication Mechanism on EC2
* **Implementation process:** Deeply researched how to set up secure barriers for the server before it is "exposed" to the Internet environment.
* **Accumulated knowledge:**
  * **Key Pairs Mechanism:** Deeply understood Asymmetric Cryptography. AWS keeps the Public Key on the virtual server, while I hold the Private Key (.pem or .ppk file). SSH-ing into the server strictly requires this key pair instead of a traditional password, completely eliminating the risk of Brute-force password guessing attacks.
  * **Server-level Firewall (Security Groups):** Clearly perceived that Security Groups act as a traffic filter right at the "front door" of each EC2 instance. I learned how to design in layers: Only allowing port 22 (SSH) to receive signals from my machine's static IP, and opening port 80/443 (HTTP/HTTPS) to the global network for users to access the web.
* **Tutorial Video:** https://youtu.be/yAR6QRT3N1k?si=03jBeqI5BH_Jq0ud