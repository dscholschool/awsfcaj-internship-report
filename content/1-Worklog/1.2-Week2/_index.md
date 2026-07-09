---
title: "Week 2 Worklog"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

## OBJECTIVES AND ASSIGNED TASKS

* Focus on completing all practical labs belonging to Module 1 to reinforce resource management and initial cost control skills.
* Study the theory and core architecture of Module 2, including the AWS Virtual Private Cloud (VPC) virtual network service, multi-tier security solutions (VPC Security), and secure private network connection mechanisms (VPN).

## IMPLEMENTATION PROCESS AND ACCUMULATED KNOWLEDGE

### Completing Module 1 Lab Series: Resource Management and Budget Control
* **Implementation process:** Deployed the actual configuration of AWS cloud financial monitoring tools including AWS Billing Dashboard, AWS Cost Explorer, and set up automatic alert thresholds via AWS Budgets.
* **Accumulated knowledge:** Mastered FinOps (Cloud Financial Management) mindset. Completing the labs helped master setting up Budget Alarms to send notifications via Email/SNS when actual or forecasted costs exceed thresholds (e.g., 80% or 100% of the free Credit account). Understood how to analyze resource consumption trend charts using Cost Explorer to early detect wasted resources (such as EBS volumes not attached to EC2) and knew how to professionally create technical support request Tickets via AWS Support Center.

### Building logical network architecture with AWS Virtual Private Cloud (VPC)
* **Implementation process:** Analyzed the components that make up an independent, secure network system on the AWS cloud and designed a logical network range division diagram.
* **Accumulated knowledge:**
  * **IP Address Range (CIDR Block):** Understood how to plan a network zone using the CIDR standard (e.g., 10.0.0.0/16 provides 65,536 IP addresses) as a foundation to allocate infrastructure for businesses without overlapping the internal network (On-premises).
  * **Network Partitioning (Subnets):** Grasped the multi-tier system design mindset (Multi-tier Architecture). Learned how to divide a VPC into Public Subnets (for outward-facing components to the Internet like Web Servers, Load Balancers) and Private Subnets (for core components requiring absolute security like Databases, App Servers/Backend). Engrained the rule that AWS always reserves 5 IP addresses in each Subnet for routing and internal management purposes.
  * **Routing Mechanism (Route Tables & Internet Gateway):** Knew how to set up an Internet Gateway (IGW) and attach it to the VPC to enable communication with the Internet. Mastered configuring the Route Table: the Public Route Table will have a route directing traffic (0.0.0.0/0) through the IGW, while the Private Route Table is completely isolated, helping to maximize data protection.
* **Tutorial Video:** https://youtu.be/O9Ac_vGHquM?si=BeFIVXXvxxdZSIXl

### Establishing multi-tier security barriers (VPC Security)
* **Implementation process:** Researched and compared two core AWS network protection layers to apply in controlling access traffic (Inbound/Outbound).
* **Accumulated knowledge:** Distinguished and mastered two complementary security tools:
  * **Security Groups (SG):** Acts as a virtual firewall at the Instance (EC2) level. This is a Stateful mechanism - meaning if configured to allow Inbound (incoming) traffic from a port, the system will automatically allow the corresponding Outbound (outgoing) response traffic without needing to open the Outbound port. The design mindset here complies with the "Least Privilege" principle, only opening strictly necessary ports (like port 80/443 for Web, port 22 for SSH).
  * **Network Access Control Lists (NACLs):** Acts as a firewall at the Subnet level. This is a Stateless mechanism - requiring explicit configuration of both Inbound and Outbound rules. NACLs process rules in numerical order (Rule Number) from lowest to highest and support both Allow and Deny rules - extremely useful when needing to block malicious IP ranges attacking the system.
* **Tutorial Video:** https://youtu.be/BPuD1l2hEQ4?si=KS3dLYLcKvWBX-6d

### Enterprise networking expansion solution (VPN)
* **Implementation process:** Researched a secure Hybrid Cloud network connection model between traditional data centers and the AWS cloud.
* **Accumulated knowledge:** Deeply understood the AWS Site-to-Site VPN architecture, a solution that helps establish a secure IPSec encrypted data transmission channel over the public Internet environment. Grasped the roles of two entities: Customer Gateway (CGW) located at the customer's office/factory side and Virtual Private Gateway (VGW) located at the AWS VPC side. This knowledge is extremely important for large systems needing continuous data synchronization between existing physical infrastructure and cloud data analytics services.
* **Tutorial Video:** https://youtu.be/CXU8D3kyxIc?si=gyatA4GN0EmhEwff