---
title: "Week 2 Worklog"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

## [cite_start]OBJECTIVES AND ASSIGNED TASKS [cite: 36]

* [cite_start]Focus on completing all practical labs belonging to Module 1 to reinforce resource management and initial cost control skills. [cite: 37]
* [cite_start]Study the theory and core architecture of Module 2, including the AWS Virtual Private Cloud (VPC) virtual network service, multi-tier security solutions (VPC Security), and secure private network connection mechanisms (VPN). [cite: 38]

## [cite_start]IMPLEMENTATION PROCESS AND ACCUMULATED KNOWLEDGE [cite: 39]

### [cite_start]Completing Module 1 Lab Series: Resource Management and Budget Control [cite: 40]
* [cite_start]**Implementation process:** Deployed the actual configuration of AWS cloud financial monitoring tools including AWS Billing Dashboard, AWS Cost Explorer, and set up automatic alert thresholds via AWS Budgets. [cite: 41]
* [cite_start]**Accumulated knowledge:** Mastered FinOps (Cloud Financial Management) mindset. [cite: 42] [cite_start]Completing the labs helped master setting up Budget Alarms to send notifications via Email/SNS when actual or forecasted costs exceed thresholds (e.g., 80% or 100% of the free Credit account). [cite: 43] [cite_start]Understood how to analyze resource consumption trend charts using Cost Explorer to early detect wasted resources (such as EBS volumes not attached to EC2) and knew how to professionally create technical support request Tickets via AWS Support Center. [cite: 44]

### [cite_start]Building logical network architecture with AWS Virtual Private Cloud (VPC) [cite: 45]
* [cite_start]**Implementation process:** Analyzed the components that make up an independent, secure network system on the AWS cloud and designed a logical network range division diagram. [cite: 46]
* [cite_start]**Accumulated knowledge:** [cite: 47]
  * [cite_start]**IP Address Range (CIDR Block):** Understood how to plan a network zone using the CIDR standard (e.g., 10.0.0.0/16 provides 65,536 IP addresses) as a foundation to allocate infrastructure for businesses without overlapping the internal network (On-premises). [cite: 48]
  * [cite_start]**Network Partitioning (Subnets):** Grasped the multi-tier system design mindset (Multi-tier Architecture). [cite: 49] [cite_start]Learned how to divide a VPC into Public Subnets (for outward-facing components to the Internet like Web Servers, Load Balancers) and Private Subnets (for core components requiring absolute security like Databases, App Servers/Backend). [cite: 50] [cite_start]Engrained the rule that AWS always reserves 5 IP addresses in each Subnet for routing and internal management purposes. [cite: 51]
  * [cite_start]**Routing Mechanism (Route Tables & Internet Gateway):** Knew how to set up an Internet Gateway (IGW) and attach it to the VPC to enable communication with the Internet. [cite: 52] [cite_start]Mastered configuring the Route Table: the Public Route Table will have a route directing traffic (0.0.0.0/0) through the IGW, while the Private Route Table is completely isolated, helping to maximize data protection. [cite: 53]
* [cite_start]**Tutorial Video:** https://youtu.be/O9Ac_vGHquM?si=BeFIVXXvxxdZSIXl [cite: 54]

### [cite_start]Establishing multi-tier security barriers (VPC Security) [cite: 55]
* [cite_start]**Implementation process:** Researched and compared two core AWS network protection layers to apply in controlling access traffic (Inbound/Outbound). [cite: 56]
* [cite_start]**Accumulated knowledge:** Distinguished and mastered two complementary security tools: [cite: 57]
  * [cite_start]**Security Groups (SG):** Acts as a virtual firewall at the Instance (EC2) level. [cite: 58] [cite_start]This is a Stateful mechanism - meaning if configured to allow Inbound (incoming) traffic from a port, the system will automatically allow the corresponding Outbound (outgoing) response traffic without needing to open the Outbound port. [cite: 59] [cite_start]The design mindset here complies with the "Least Privilege" principle, only opening strictly necessary ports (like port 80/443 for Web, port 22 for SSH). [cite: 60]
  * [cite_start]**Network Access Control Lists (NACLs):** Acts as a firewall at the Subnet level. [cite: 61] [cite_start]This is a Stateless mechanism - requiring explicit configuration of both Inbound and Outbound rules. [cite: 62] [cite_start]NACLs process rules in numerical order (Rule Number) from lowest to highest and support both Allow and Deny rules - extremely useful when needing to block malicious IP ranges attacking the system. [cite: 63]
* [cite_start]**Tutorial Video:** https://youtu.be/BPuD1l2hEQ4?si=KS3dLYLcKvWBX-6d [cite: 64]

### [cite_start]Enterprise networking expansion solution (VPN) [cite: 65]
* [cite_start]**Implementation process:** Researched a secure Hybrid Cloud network connection model between traditional data centers and the AWS cloud. [cite: 66]
* [cite_start]**Accumulated knowledge:** Deeply understood the AWS Site-to-Site VPN architecture, a solution that helps establish a secure IPSec encrypted data transmission channel over the public Internet environment. [cite: 67] [cite_start]Grasped the roles of two entities: Customer Gateway (CGW) located at the customer's office/factory side and Virtual Private Gateway (VGW) located at the AWS VPC side. [cite: 68] [cite_start]This knowledge is extremely important for large systems needing continuous data synchronization between existing physical infrastructure and cloud data analytics services. [cite: 69]
* [cite_start]**Tutorial Video:** https://youtu.be/CXU8D3kyxIc?si=gyatA4GN0EmhEwff [cite: 70]