---
title: "Worklog Tuần 9"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.9. </b> "
---
## FIRST CLOUD AI JOURNEY FCAJ

### 1. Weekly Goals

The ninth week focused on finalizing the AWS architecture design and preparing for implementation.

My role was mainly related to cloud infrastructure planning and AWS service configuration for the group project.

The weekly objectives included:

Joining the study session on June 15 to review the project architecture.
Finalizing the AWS service diagram.
Preparing IAM roles and permissions needed for Lambda and other services.
Planning the data flow from ingestion to storage and AI processing.
Reviewing security and cost control before deployment.

### 2. Tasks Implemented During the Week

| Day / Date | Work Content                          | Task Details                                                                            | Results Achieved                                                  | Reference Sources |
| ---------- | ------------------------------------- | --------------------------------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------- |
| Mon Jun 15 | Study Session and Architecture Review | Joined study session and reviewed the final project architecture with the team          | Improved understanding of the full AWS service flow               | Study Group       |
| Tue Jun 16 | Data Flow Design                      | Designed the data flow between frontend, API Gateway, Lambda, S3, DynamoDB, and Bedrock | Visualized the system processing pipeline                         | Draw.io           |
| Wed Jun 17 | Architecture Finalization             | Updated the AWS diagram and clarified service connections                               | Completed a cleaner architecture version for project presentation | AWS Icon Set      |
| Thu Jun 18 | AI Service Research                   | Studied AI processing options on AWS, especially Bedrock integration                    | Understood how AI results can be generated and stored             | AWS Bedrock       |
| Fri Jun 19 | IAM Planning                          | Prepared IAM permission direction for Lambda, S3, DynamoDB, and Bedrock access          | Applied least privilege thinking to project services              | AWS IAM           |
| Sat Jun 20 | Monitoring Planning                   | Planned CloudWatch logs for Lambda execution and error tracking                         | Prepared debugging method for implementation phase                | CloudWatch        |
| Sun Jun 21 | Weekly Review                         | Consolidated architecture notes and prepared Week 10 implementation tasks               | Ready to begin AWS service setup                                  | Personal Records  |

### 3. Results Achieved

During Week 9, I focused on making the AWS architecture more practical and ready for implementation. I finalized the main service flow of the project and defined how each AWS service would communicate with others.

The planned data flow was: user accesses the frontend through CloudFront and S3 static website, authenticates through Cognito, sends requests to API Gateway, API Gateway triggers Lambda, Lambda reads or writes data to S3 and DynamoDB, EventBridge triggers ingestion tasks, and Bedrock supports AI analysis. CloudWatch is used to monitor logs and troubleshoot errors.

The study session on June 15 helped me review the architecture with a clearer mindset. I understood that my part was not only drawing the diagram, but also preparing actual AWS services, permissions, and monitoring so the system could run correctly during the demo.
