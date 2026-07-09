---
title: "Blog 2"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---
# AWS Cost & AI: When Running Cloud Becomes a Cost Management Problem

Cloud computing is powerful because it allows developers to create infrastructure quickly, test ideas faster, and scale systems without buying physical servers. However, this flexibility also introduces a new challenge: cost management. When AI services are added to the system, the cost problem becomes even more important because model calls, testing loops, endpoint runtime, logs, and supporting resources can grow quietly in the background.

This blog shares practical experience about controlling AWS cost while learning and experimenting with cloud and AI services. It focuses on the mindset of FinOps, the habit of monitoring billing early, and the importance of cleaning up testing resources after each lab.

## Why Cost Became a Problem

At first, because the environment was still within AWS Free Tier, the team assumed that a small EC2 instance could run without much concern. But as testing time increased, several factors started affecting cost: EC2 running 24/7, growing logs, EBS storage usage, helper resources that were left enabled, and AI API calls that were made more often than expected.

![AWS cost management architecture for EC2 and AI services](/images/3-BlogsTranslated/blog2-cost-management.png)

The issue was not caused by one expensive service only. It came from many small resources running together for a long time. This is a common situation for students and new cloud learners: the technical lab is finished, but the infrastructure is still active.

## AI Services Increase Cost Awareness

AI/ML services such as Amazon Bedrock, Amazon SageMaker, and Amazon Comprehend are useful for building intelligent applications. They can summarize text, analyze sentiment, generate recommendations, classify data, or support agents in decision-making workflows.

However, AI services are different from traditional infrastructure. Cost may depend on tokens, inference requests, model runtime, endpoint hours, data processing, or experiment frequency. If the team tests prompts repeatedly or keeps an endpoint running longer than needed, the monthly bill can increase quickly.

For this reason, AI workloads should be designed with clear usage limits from the beginning. Before running many tests, the team should define which model is used, how many requests are expected, how logs are stored, and when resources must be stopped.

## Using AWS Budgets Early

One of the most important lessons is to configure AWS Budgets before starting experiments, not after cost has already increased. AWS Budgets helps track monthly spending and can send alerts when usage approaches a predefined threshold.

A simple budget setup can include:

- A monthly cost limit for the whole AWS account.
- Email alerts at 50%, 80%, and 100% of the budget.
- Separate attention for AI-related services such as Bedrock or SageMaker.
- Daily checking during active testing periods.

This does not prevent all cost issues automatically, but it helps the team detect abnormal spending earlier and respond before the bill becomes too high.

## Resource Cleanup Habit

Another important practice is cleaning up resources after every lab. In AWS, many services continue generating cost even when no one is actively using them.

Examples include:

- EC2 instances left running overnight.
- EBS volumes that remain after an instance is deleted.
- Load balancers or NAT Gateways created during testing.
- CloudWatch logs growing over time.
- SageMaker notebooks or endpoints left active.
- Test files stored in S3 without lifecycle rules.

A good habit is to create a cleanup checklist at the end of each practice session. The checklist should include compute, storage, networking, logging, and AI services.

## FinOps Mindset

FinOps means treating cloud cost as part of engineering responsibility. Developers should not only ask whether a system works, but also whether it runs efficiently and whether the cost is acceptable for its purpose.

For learning projects, the goal is not to eliminate all cost. The goal is to understand why cost appears, how to measure it, and how to control it. This mindset is especially important when building AI applications because experimentation can create many repeated requests.

## Lessons Learned

Several lessons were learned from this experience:

- Free Tier is helpful, but it does not mean every resource is free forever.
- EC2, EBS, logs, load balancers, and AI calls should be monitored together.
- AWS Budgets should be configured before running labs.
- AI experiments need request limits and cost awareness.
- Cleanup should become a repeated habit after every testing session.
- Cost management is part of cloud engineering, not only accounting.

## Conclusion

Running cloud infrastructure is not only a technical problem. It is also a cost management problem. AWS makes it easy to build and test systems quickly, but that convenience requires discipline. By using AWS Budgets, checking billing dashboards, limiting AI experiments, and cleaning up resources regularly, teams can learn and build on AWS without unexpected cost spikes.
