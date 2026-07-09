---
title: "Blog 3"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---
# Deploying a Serverless Application with AWS Lambda and Amazon API Gateway

Blog post link: [Facebook - AWS Study Group FCJ](https://www.facebook.com/groups/awsstudygroupfcj/)

After deploying a backend on Amazon EC2 and learning how to optimize cloud operating costs, the team started asking a new question: is there a way to deploy an API without directly managing servers?

EC2 provides a high level of control. Users can configure the operating system, install runtimes, manage networking, storage, and security groups. However, this also comes with operational responsibilities such as monitoring instance health, updating software, patching the operating system, starting or stopping servers, and planning scalability.

While exploring other application deployment models on AWS, the team learned about Serverless Computing. The interesting part of this model is that developers can focus more on code and business logic, while AWS manages much of the underlying infrastructure.

## What Is Serverless?

Serverless does not mean that there are no servers. Servers still exist, but users do not manage them directly.

With a serverless model, AWS handles tasks such as:

- Allocating compute resources.
- Starting runtime environments.
- Scaling automatically based on traffic.
- Managing operating system and runtime updates behind the scenes.
- Handling availability and load.

As a result, developers can focus on features instead of infrastructure administration. This is why serverless is commonly used for REST APIs, mobile app backends, chatbots, IoT, event processing, and AI pipelines.

## Deployment Architecture

In a basic serverless model, the client sends an HTTP request to Amazon API Gateway. API Gateway acts as the entry point, receives the request, and forwards it to AWS Lambda. Lambda processes the business logic, reads or writes data to Amazon DynamoDB if needed, and returns the response through API Gateway.

![Serverless Lambda API Gateway architecture](/images/3-BlogsTranslated/blog3-serverless-architecture.png)

The main components include:

- Amazon API Gateway: receives HTTP/REST requests from clients.
- AWS Lambda: runs the function that handles business logic.
- Amazon DynamoDB: stores data using a NoSQL model.
- AWS IAM Role: grants Lambda permission to access required services.
- Amazon CloudWatch: collects logs, metrics, and supports observability.

Unlike EC2, users do not need to create or maintain always-running servers. The function is triggered only when a request or event occurs.

## Why Serverless Is Attractive

### No server management

This is the biggest difference compared with EC2. With EC2, users need to manage instances, CPU, memory, operating system updates, security patches, and scaling. With Lambda, AWS takes responsibility for most of these tasks.

### Automatic scaling

When an application receives many requests at the same time, Lambda can automatically create additional execution environments to handle them. When traffic decreases, resources are released. This reduces the need to predict the number of servers in advance.

### Pay-per-use pricing

With Lambda, cost is based on the number of function invocations and execution duration. If the function is not running, there is almost no compute cost. This is very different from EC2, where an instance continues to generate cost based on running time even if no requests are processed.

This model works well for systems with unpredictable traffic, experimental applications, MVPs, internal APIs, and learning projects.

## Limitations to Consider

### Cold start

When a Lambda function has not been used for a while, its execution environment may be released. The next request may take additional time to initialize the function. This behavior is called a cold start.

For APIs that require very fast and consistent response times, cold start should be considered during architecture design.

### Execution time limits

Lambda is designed for short, event-driven tasks. If an application needs to run continuously, process complex background jobs, or maintain long-lived connections, EC2 or ECS may be more suitable.

### Cloud service dependency

When using Lambda, the architecture is often closely connected with services such as API Gateway, IAM, CloudWatch, DynamoDB, and EventBridge. This makes AWS integration convenient, but also increases dependency on the cloud platform.

## Cost Perspective

After learning about AWS Cost Management, the team noticed that serverless provides a clear cost optimization perspective.

In the EC2 model:

- Servers run continuously.
- Cost is based on running time.
- Scaling needs to be managed manually or configured separately.

With Lambda:

- If there are no requests, there is almost no compute cost.
- The system scales automatically when needed.
- There is no need to keep a server running 24/7.

However, serverless is not always cheaper. If a system has very high traffic, long-running functions, or continuous API Gateway requests, the total cost of Lambda and API Gateway can become higher than EC2 or ECS. Therefore, architecture decisions should be based on the actual workload.

## Lessons Learned

Serverless does not completely replace EC2. It is another architecture option that fits a different set of problems.

If an application needs full operating system control, special configuration, long-running processes, or deep runtime customization, EC2 is still a reasonable choice.

On the other hand, if the goal is fast deployment, less infrastructure management, automatic scaling, and cost optimization for APIs with variable traffic, AWS Lambda combined with Amazon API Gateway is worth considering.

The most important lesson is not to think in terms of which service is always better. Each AWS service is designed to solve a specific group of problems. Understanding the characteristics of each service helps teams choose the right architecture from the beginning.

## Conclusion

By learning about the serverless model, the team gained a more modern view of building applications on AWS. Combining Amazon API Gateway with AWS Lambda can significantly reduce infrastructure management work while taking advantage of automatic scaling and pay-per-use pricing.

For learning projects, APIs with unstable traffic, MVPs, or applications that need fast deployment, this is an architecture worth exploring. In future work, the team can continue learning how to combine Lambda with Amazon DynamoDB, Amazon S3, and Amazon EventBridge to build more complete serverless systems.
