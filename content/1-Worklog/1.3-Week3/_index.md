---
title: "Week 3 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---
## FIRST CLOUD AI JOURNEY FCAJ

### 1. Weekly Goals

The third week focused on expanding AWS networking knowledge and studying how multiple cloud networks can communicate with each other.

The weekly objectives included:

Understanding VPC Peering and its use cases.
Practicing route table updates between different VPCs.
Studying DNS resolution in connected cloud environments.
Learning about hybrid cloud concepts.
Improving understanding of centralized identity management.

### 2. Tasks Implemented During the Week

| Day / Date | Work Content       | Task Details                                                      | Results Achieved                                     | Reference Sources      |
| ---------- | ------------------ | ----------------------------------------------------------------- | ---------------------------------------------------- | ---------------------- |
| Mon May 04 | Roadmap Review     | Reviewed internship learning path and technical goals             | Clarified weekly direction                           | FCAJ Materials         |
| Tue May 05 | VPC Peering Theory | Studied VPC Peering and non-overlapping CIDR requirements         | Understood private connection between VPCs           | AWS Documentation      |
| Wed May 06 | Peering Practice   | Configured VPC Peering connection and updated route tables        | Enabled communication between two VPCs               | AWS Console            |
| Thu May 07 | Network Security   | Adjusted Security Group and NACL rules for testing                | Improved network access control                      | AWS VPC                |
| Fri May 08 | DNS Study          | Studied Route 53 Resolver and DNS behavior in AWS                 | Understood DNS support in hybrid architecture        | AWS Route 53           |
| Sat May 09 | DNS Flow Review    | Reviewed inbound and outbound DNS query flow                      | Understood cross-network name resolution             | AWS Architecture Guide |
| Sun May 10 | Identity Research  | Studied Active Directory and centralized user management concepts | Learned how enterprise identity can connect to cloud | AWS Directory Service  |

### 3. Results Achieved

During this week, I practiced connecting different AWS networks and understood how VPC Peering can allow private communication between resources without sending traffic through the public internet.

I also learned that when multiple networks are connected, routing must be configured carefully on both sides. If one route table is missing or the CIDR range overlaps, communication will fail.

Another important lesson was that DNS and identity management are important parts of real enterprise cloud systems. A system is not only about compute and storage, but also about how users, services, and network names are managed securely.
