---
title: "Week 4 Worklog"
date: 2024-01-01
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---
## FIRST CLOUD AI JOURNEY FCAJ

### 1. Weekly Goals

The fourth week focused on backup, notification, command-line operation, and larger-scale network architecture.

The weekly objectives included:

Studying AWS Backup and automated backup plans.
Learning how SNS can send notification emails.
Installing and practicing AWS CLI.
Studying AWS Transit Gateway for connecting multiple VPCs.
Applying cleanup habits after completing labs.

### 2. Tasks Implemented During the Week

| Day / Date | Work Content           | Task Details                                               | Results Achieved                               | Reference Sources     |
| ---------- | ---------------------- | ---------------------------------------------------------- | ---------------------------------------------- | --------------------- |
| Mon May 11 | Backup Study           | Learned AWS Backup, Backup Vault, and Backup Plan          | Understood automated data protection           | AWS Backup Guide      |
| Tue May 12 | SNS Notification       | Connected backup status with SNS email notification        | Learned how AWS sends system alerts            | AWS SNS               |
| Wed May 13 | AWS CLI Setup          | Installed AWS CLI and configured access credentials        | Practiced managing AWS resources from terminal | AWS CLI Documentation |
| Thu May 14 | Transit Gateway Theory | Studied Transit Gateway and compared it with VPC Peering   | Understood hub-and-spoke networking            | AWS Networking Guide  |
| Fri May 15 | TGW Practice           | Created Transit Gateway and connected multiple VPCs        | Built a centralized routing model              | AWS Console           |
| Sat May 16 | Routing Test           | Tested route tables and EC2 communication between networks | Verified traffic flow across VPCs              | AWS EC2 / VPC         |
| Sun May 17 | Cleanup and Review     | Removed test resources and summarized learning points      | Reduced unnecessary cloud cost                 | Personal Notes        |

### 3. Results Achieved

This week gave me a better understanding of cloud operations. I learned how AWS Backup can reduce the risk of data loss and how SNS can notify administrators when a backup job succeeds or fails.

I also practiced AWS CLI, which is useful for faster operations and future automation. Instead of only using the AWS Console, the CLI helps me understand commands more clearly and prepares me for DevOps-related work.

The most important networking concept this week was Transit Gateway. I understood that when the number of VPCs increases, Transit Gateway is easier to manage than creating many VPC Peering connections.
