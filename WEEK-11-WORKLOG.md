# Week 11 Worklog

## FIRST CLOUD AI JOURNEY FCAJ

### 1. Weekly Goals

The eleventh week focused on testing, troubleshooting, and improving the AWS service configuration for the final group project.

The weekly objectives included:

Testing the S3 and CloudFront frontend deployment.
Checking API Gateway and Lambda connection.
Debugging Lambda errors through CloudWatch Logs.
Reviewing IAM permissions for Lambda, S3, DynamoDB, and Bedrock.
Testing Cognito authentication direction.
Consolidating worklogs and preparing documentation for final submission.

### 2. Tasks Implemented During the Week

| Day / Date | Work Content                    | Task Details                                                           | Results Achieved                                               | Reference Sources    |
| ---------- | ------------------------------- | ---------------------------------------------------------------------- | -------------------------------------------------------------- | -------------------- |
| Mon Jun 29 | Frontend Deployment Check       | Verified S3 upload and CloudFront access behavior                      | Confirmed static frontend deployment flow                      | S3 / CloudFront      |
| Tue Jun 30 | API Connection Test             | Tested API Gateway route and Lambda trigger behavior                   | Identified issues in request and response handling             | API Gateway / Lambda |
| Wed Jul 01 | IAM and Permission Review       | Reviewed Lambda execution role and service permissions                 | Improved security and reduced access problems                  | AWS IAM              |
| Thu Jul 02 | Lambda Troubleshooting          | Checked Lambda test event, runtime logs, and integration errors        | Found issues related to payload, token, and service connection | CloudWatch Logs      |
| Fri Jul 03 | Cognito Review                  | Started reviewing Cognito authentication flow for protected API access | Prepared authentication layer for project demo                 | Amazon Cognito       |
| Sat Jul 04 | Service Cleanup and Cost Review | Checked unused resources and reviewed billing dashboard                | Reduced unnecessary cost risk                                  | AWS Billing          |
| Sun Jul 05 | Worklog Consolidation           | Compiled and polished weekly worklogs from Week 1 to Week 11           | Completed structured internship documentation                  | Personal Records     |

### 3. Results Achieved

During Week 11, I focused on testing and troubleshooting the AWS services that were configured for the project. I checked whether the frontend could be deployed through S3 and CloudFront, and reviewed how the frontend would connect to backend APIs through API Gateway and Lambda.

I also used CloudWatch Logs to identify errors during Lambda testing. This helped me understand that cloud debugging requires checking not only source code, but also permissions, payload format, environment variables, and service integration settings.

Another important task was reviewing IAM permissions. Since Lambda needs to access services such as S3, DynamoDB, Bedrock, and CloudWatch, the execution role must be configured properly. However, the permissions should still follow the principle of least privilege.

By the end of the week, I had a clearer understanding of how to deploy and connect AWS services for a real project. I also consolidated my personal worklogs to prepare for internship reporting and final evaluation.
