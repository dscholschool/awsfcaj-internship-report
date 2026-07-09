---
title: "Week 3 Worklog"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

## OBJECTIVES AND ASSIGNED TASKS

* Start practicing Module 2 labs on the actual AWS environment.
* Translate all the network architecture (VPC) theory learned last week into operational skills on the AWS Management Console.
* Complete the progress of the labs (currently up to Lab 03), focusing on manually building an isolated network environment, configuring routing, and setting up security layers.

## IMPLEMENTATION PROCESS AND ACCUMULATED KNOWLEDGE

With a large amount of practice this week, I went deep into each step of configuring the network infrastructure. The accumulated knowledge did not stop at theory but became practical problem-solving skills:

### Initialization and Network Resource Allocation (VPC & Subnet Allocation)
* **Implementation process:** Manually created a completely new VPC instead of using AWS's Default VPC. Calculated and divided the IP range (CIDR) into different Subnets placed in multiple Availability Zones (AZs) to ensure High Availability.
* **Accumulated knowledge:** Deeply ingrained the skill of network address planning. I learned how to allocate IPs economically and logically: creating Public Subnets with small IP ranges for resources like Load Balancers or Bastion Hosts, and creating Private Subnets with much larger IP ranges to provide ample space for Application Servers (App Servers) or databases. Clearly perceived the principle of resource isolation right from the virtual physical network design step.

### Traffic Routing and Internet Access Handling
* **Implementation process:** Attached an Internet Gateway (IGW) to the VPC and configured Route Tables to direct packets. Specifically, set up a mechanism so that servers deep inside the internal network (Private) can still download updates from the Internet without exposing their real IP addresses.
* **Accumulated knowledge:** Mastered the operation of "mapping" Subnets to the correct corresponding Route Table. Clearly understood the flow of packets: from internal server -> Route Table -> Internet Gateway -> Internet.
* **Core knowledge about NAT Gateway / NAT Instance:** This was a highlight during the practice. I learned how to deploy a NAT Gateway located in a Public Subnet, acting as a "middleman" receiving Internet access requests from servers in Private Subnets, fetching data on their behalf, and returning it. This helps the internal system connect to the outside world (to update patches/software) while completely blocking unauthorized active connections initiated from the Internet targeting the system.

### Practical Security Configuration Deployment (Security Implementation)
* **Implementation process:** Directly wrote and applied rules for Security Groups (SG) and Network Access Control Lists (NACL) to the newly created resources in Lab 03.
* **Accumulated knowledge:** Built a Defense in Depth mindset. Practiced the "Least Privilege" principle by only opening port 22 (SSH) from a single IP address (personal computer IP or Bastion Host), denying all other access sources. Mastered the Security Group referencing technique: Instead of allowing a static IP range to access the Database, I learned how to configure the Database Security Group to only accept connections from the App Server Security Group. This circular referencing feature of AWS helps the system automatically scale extremely flexibly and with absolute security.

### Testing and Troubleshooting Skills
* **Implementation process:** Tested network connections (Ping, SSH) between virtual machines in different subnets and from the outside Internet. Read logs and found errors when connections failed.
* **Accumulated knowledge:** Practiced infrastructure network debugging mindset. When a connection is unsuccessful, I learned how to check sequentially from bottom to top: Check if the server has a Public IP -> Check if the Security Group has opened the port -> Check if the Route Table has a path out to the IGW -> Check if the NACL accidentally blocks the subnet.