---
title: "Posted Blogs"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 3. </b> "
---
During the cloud computing learning and practice journey, three in-depth blog posts were compiled and shared with the community. These articles reflect real-world experiences in configuring infrastructure, troubleshooting system bugs, and researching application deployment models on AWS:

### [Blog 1 - Deploying a Backend to AWS EC2 and the Bug Caused by Capital Letters](3.1-blog1/)

This post analyzes the case-sensitivity differences in .env configuration files when running applications on a local Windows environment compared to an Ubuntu Linux environment on AWS EC2. It highlights how Boolean flags were misinterpreted, leading to silent logic bugs without throwing runtime errors, and shares key lessons on maintaining environment configuration consistency.

### [Blog 2 - AWS Cost & AI: When Running Cloud Becomes a Cost Management Problem](3.2-blog2/)

This post shares practical experiences regarding cloud operational cost optimization (FinOps) when integrating AI/ML services (Amazon Bedrock, SageMaker, Comprehend) on AWS. It emphasizes the importance of managing budgets early with AWS Budgets and establishing the habit of terminating testing resources after labs to prevent unexpected cost spikes.

### [Blog 3 - Deploying a Serverless Application with AWS Lambda and Amazon API Gateway](3.3-blog3/)

This post guides you through the migration from a traditional server-based architecture (EC2) to a serverless architecture using a combination of AWS Lambda and Amazon API Gateway. It analyzes the benefits of reducing system operational overhead, automatic scaling based on actual demand, and the cost-effective pay-as-you-go pricing model.
