---
title: "Worklog Tuần 10"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.10. </b> "
---
## FIRST CLOUD AI JOURNEY FCAJ

### 1. Weekly Goals

The tenth week focused on beginning the actual deployment and AWS service configuration for the final project.

My main responsibility was setting up AWS services for the project, especially the cloud infrastructure components used by the frontend, backend, ingestion process, and AI processing flow.

The weekly objectives included:

Joining the study session on June 22 to review implementation steps.
Setting up S3 bucket for frontend hosting and raw data storage.
Preparing CloudFront distribution for web access.
Configuring API Gateway and Lambda for backend connection.
Preparing EventBridge scheduled trigger for ingestion Lambda.
Reviewing Bedrock and DynamoDB integration direction.
Testing the initial AWS service connections.

### 2. Tasks Implemented During the Week

| Day / Date | Work Content                          | Task Details                                                                         | Results Achieved                                                      | Reference Sources        |
| ---------- | ------------------------------------- | ------------------------------------------------------------------------------------ | --------------------------------------------------------------------- | ------------------------ |
| Mon Jun 22 | Study Session and Deployment Planning | Joined study session to confirm AWS service setup plan and team responsibilities     | Understood the implementation order and AWS tasks to complete         | Study Group              |
| Tue Jun 23 | Frontend Hosting Setup                | Prepared S3 bucket configuration for static website hosting                          | Created the basic frontend hosting environment                        | Amazon S3                |
| Wed Jun 24 | CloudFront Configuration              | Configured CloudFront distribution to serve frontend content from S3                 | Improved access performance and prepared for production-like delivery | Amazon CloudFront        |
| Thu Jun 25 | API Layer Planning                    | Reviewed API Gateway routes and Lambda connection requirements                       | Prepared backend connection structure                                 | API Gateway / Lambda     |
| Fri Jun 26 | Lambda and EventBridge Setup          | Prepared Lambda deployment flow and EventBridge scheduled trigger for data ingestion | Built the foundation for automatic data collection                    | AWS Lambda / EventBridge |
| Sat Jun 27 | Database and AI Service Review        | Reviewed DynamoDB table design and Bedrock processing flow                           | Clarified how processed results would be stored and analyzed          | DynamoDB / Bedrock       |
| Sun Jun 28 | Initial Connection Test               | Checked service configuration, permissions, and logs                                 | Confirmed the initial AWS setup direction for the project             | CloudWatch Logs          |

### 3. Results Achieved

During Week 10, I started configuring the actual AWS services for the final project. This was an important phase because the project moved from design to deployment.

My main work was related to AWS infrastructure setup. I prepared the S3 bucket for frontend hosting and planned another storage area for raw data. I also configured CloudFront so the frontend could be accessed more efficiently and closer to a real deployment environment.

I reviewed the API Gateway and Lambda structure to make sure the frontend could call backend functions correctly. I also prepared the EventBridge and Lambda direction for scheduled data ingestion. For the AI processing part, I reviewed how Lambda could connect with Bedrock and store results in DynamoDB.

The study session on June 22 was useful because it helped the team confirm who would handle frontend, backend, testing, and AWS integration tasks. My responsibility was clearly focused on setting up and connecting AWS services for the system.
