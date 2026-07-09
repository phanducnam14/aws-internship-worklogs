---
title: "Week 6 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---
## FIRST CLOUD AI JOURNEY FCAJ

### 1. Weekly Goals

The sixth week focused on cloud security, cost optimization, and automation with Lambda.

The weekly objectives included:

Studying AWS Security Hub and common security findings.
Reviewing EC2 cost optimization methods.
Learning resource tagging for better management.
Using IAM Role for EC2 instead of hardcoded access keys.
Creating a Lambda function to automate EC2 start and stop actions.

### 2. Tasks Implemented During the Week

| Day / Date | Work Content         | Task Details                                                            | Results Achieved                          | Reference Sources     |
| ---------- | -------------------- | ----------------------------------------------------------------------- | ----------------------------------------- | --------------------- |
| Mon May 25 | Security Hub Study   | Learned AWS Security Hub and security benchmark concepts                | Understood automated security checking    | AWS Security Hub      |
| Tue May 26 | Security Review      | Reviewed common security findings such as open ports and missing MFA    | Improved security awareness               | AWS Security Guide    |
| Wed May 27 | EC2 Cost Study       | Studied right-sizing, stopping unused instances, and cost-saving habits | Understood EC2 cost control               | AWS Cost Optimization |
| Thu May 28 | Tagging and IAM Role | Applied project tags and studied IAM Role for EC2                       | Improved resource governance and security | AWS IAM               |
| Fri May 29 | Lambda Script Design | Designed logic to start or stop EC2 by tag                              | Understood serverless automation          | AWS Lambda            |
| Sat May 30 | EventBridge Schedule | Connected EventBridge rule with Lambda schedule                         | Practiced automatic resource control      | Amazon EventBridge    |
| Sun May 31 | Logs and Cleanup     | Checked CloudWatch logs and removed test rules                          | Completed automation review               | CloudWatch Logs       |

### 3. Results Achieved

This week gave me more understanding of security and automation in AWS. I learned how Security Hub can detect misconfigurations and help improve cloud security posture.

I also practiced tagging resources, which is a simple but important habit. Tags help identify the purpose, owner, and environment of each AWS resource. This is useful for both cost tracking and automation.

The Lambda and EventBridge practice was especially useful because it showed how serverless services can automate cloud operations. Instead of manually starting and stopping EC2 instances every day, Lambda can do it based on a schedule.
