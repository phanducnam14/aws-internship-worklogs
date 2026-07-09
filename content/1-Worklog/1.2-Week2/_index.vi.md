---
title: "Worklog Tuần 2"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.2. </b> "
---
## FIRST CLOUD AI JOURNEY FCAJ

### 1. Weekly Goals

The second week focused on basic network design in AWS and understanding how cloud resources communicate securely.

The weekly objectives included:

Studying VPC, IP address, CIDR, subnet, route table, and Internet Gateway.
Learning the difference between Public Subnet and Private Subnet.
Understanding Security Group and Network ACL.
Practicing Custom VPC design.
Continuing to monitor AWS costs during lab practice.

### 2. Tasks Implemented During the Week

| Day / Date | Work Content            | Task Details                                                        | Results Achieved                                      | Reference Sources       |
| ---------- | ----------------------- | ------------------------------------------------------------------- | ----------------------------------------------------- | ----------------------- |
| Fri Apr 24 | Internship Information  | Completed basic registration and reviewed onboarding instructions   | Finished administrative preparation                   | FCAJ Guidelines         |
| Sat Apr 25 | VPC Theory              | Studied VPC, CIDR block, subnet, and IP allocation                  | Understood the basic structure of AWS networking      | AWS Documentation       |
| Sun Apr 26 | Network Planning        | Drafted a simple network layout with public and private areas       | Visualized how cloud resources are separated          | Personal Notes          |
| Mon Apr 27 | Budget Review           | Checked billing dashboard and budget notification                   | Improved awareness of AWS cost control                | AWS Billing             |
| Tue Apr 28 | Custom VPC Setup        | Created a Custom VPC and divided it into public and private subnets | Built an isolated network environment                 | AWS Console             |
| Wed Apr 29 | Routing Configuration   | Configured Route Table and Internet Gateway for public subnet       | Enabled internet access for public resources          | AWS VPC Guide           |
| Thu Apr 30 | Security Layer Study    | Compared Security Group and Network ACL                             | Understood instance-level and subnet-level protection | AWS Security Guide      |
| Fri May 01 | High Availability Study | Studied the idea of deploying subnets across multiple AZs           | Understood the importance of fault tolerance          | AWS Architecture Center |
| Sat May 02 | EC2 Verification        | Launched EC2 instances to test public and private subnet behavior   | Verified the network design in practice               | AWS EC2                 |
| Sun May 03 | Weekly Summary          | Wrote weekly notes and reviewed mistakes during practice            | Completed Week 2 documentation                        | Personal Records        |

### 3. Results Achieved

This week helped me understand the foundation of AWS networking. I learned how to design a VPC, create subnets, configure routing, and protect resources with security rules.

The key takeaway was that a good AWS system should not place all resources in the public internet. Public subnets should be used for resources that need external access, while backend services and databases should be placed in private subnets for better security.

I also understood that Security Groups and Network ACLs are different layers of protection. Security Groups protect EC2 instances, while Network ACLs protect traffic at the subnet level.
