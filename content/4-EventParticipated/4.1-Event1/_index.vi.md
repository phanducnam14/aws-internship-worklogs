---
title: "Event 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---
# Report: AWS Vietnam Community Day 2026

| Event Information | Details |
| ----------------- | ------- |
| Event Name | AWS Vietnam Community Day 2026 (Saturday Meetup) |
| Date & Time | May 23, 2026 (09:00 - 12:00) |
| Location | 26th Floor, Bitexco Financial Tower, Ho Chi Minh City |
| Role | Attendee |

## Event Objectives

AWS Vietnam Community Day 2026 was an important community event that I attended during my internship period. The event took place at Bitexco Financial Tower and brought together students, cloud learners, AWS Community Builders, engineers, and speakers from different companies.

The objective of the event was to provide practical sharing about AWS, AI, cloud architecture, and real production experience. Instead of only introducing theoretical concepts, the speakers shared how cloud services and AI solutions are applied in actual business systems. This helped me understand the difference between learning AWS in labs and using AWS in real enterprise environments.

For me, the event was also a good opportunity to expand my view of cloud computing. Before attending, I mainly understood AWS services individually. After the event, I had a clearer idea of how services such as CloudFront, Lambda@Edge, AI assistants, and multi-agent systems can be combined to solve real problems.

## Speakers

| No. | Speaker | Role | Topic |
| --- | ------- | ---- | ----- |
| 1 | Tinh Truong | Platform Engineer @GoTymeX | Context Is Everything - Making AI Actually Work for You |
| 2 | Pham Ng Hai Anh | AWS Community Builder @G-AsiaPacificVietnam | Friendly AI Assistant with Amazon Quick |
| 3 | Nguyen Tuan Thinh | AWS Champion Instructor, 12x AWS Certified | From Edge To Origin: CloudFront as Your Foundation |
| 4 | Team VIB | AWS Track Winner @LotusHacks2026 | 36 Hours with LotusHacks - Building UTMorpho |
| 5 | Duc Dao | Solution Architect @CloudKinetics | Non-Determinism of "Deterministic" LLM Settings |
| 6 | Vy Lam | Sr. Business Systems Analyst @VPBank | Enterprise-Grade Multi-Agent System |

## Key Highlights

### Understanding the Problems of Traditional Systems

One of the first lessons I gained from the event was that many traditional systems still face limitations in performance, scalability, and security. For example, if a web application serves users directly from a single origin server without using a CDN, users located far from the server may experience higher latency and slower response time.

This helped me understand why services such as Amazon CloudFront are important. CloudFront does not only cache static content, but also helps reduce the load on the origin server and improves the user experience by serving content from edge locations closer to users.

The AI-related sessions also showed that building AI applications is not only about calling an LLM API. If the system does not provide enough context, memory, or output control, the AI may return general, inconsistent, or inaccurate responses. This made me realize that AI integration requires proper system design, not just prompt writing.

### Modern Architecture and Microservice Thinking

Another topic that impressed me was the transition from large monolithic systems to more modular architectures. In a modern system, each component should have a clear responsibility and communicate with other parts through APIs or events.

This idea was also connected to the multi-agent system shared in the event. Instead of letting one AI model handle all tasks, the system can be divided into smaller agents, with each agent responsible for a specific function such as collecting information, analyzing data, checking rules, or supporting decisions.

From this session, I learned that the microservice mindset can also be applied to AI systems. Dividing responsibilities clearly can make the system easier to maintain, debug, and improve later.

### Domain-Driven Design and MVP Mindset

Through the LotusHacks sharing session, I learned more about the importance of defining the project scope clearly before implementation. In a short hackathon period, the team had to focus on the most important features first instead of trying to build everything at once.

This is similar to the MVP mindset. A project should first have a working core flow, then improve step by step based on feedback. This lesson is useful for my final group project because our team also needs to divide tasks clearly and avoid expanding the scope too much.

The event also helped me understand that technical design should follow the business problem. If developers do not understand the users and the real requirement, the system can become complicated but not truly useful.

### Event-Driven and Serverless Architecture

The event also mentioned event-driven architecture and serverless computing. In an event-driven system, services do not need to depend too tightly on each other. When an event happens, such as a user uploading data or a scheduled task being triggered, other services can process it automatically.

This reminded me of AWS services I have been learning, such as EventBridge, Lambda, S3, and CloudWatch. These services can be combined to build automated workflows without maintaining servers all the time.

I also learned that serverless architecture helps reduce operational work. Developers can focus more on business logic while AWS handles scaling, server management, and runtime execution.

### CloudFront and Edge Computing

The CloudFront session helped me understand CloudFront more clearly. Previously, I only thought of CloudFront as a CDN for caching static files. After the session, I learned that it can also support security, origin protection, request handling, and performance optimization.

I also learned the basic difference between CloudFront Functions and Lambda@Edge. CloudFront Functions are suitable for lightweight tasks such as redirects or header changes, while Lambda@Edge can handle more complex processing closer to users.

This knowledge is useful for my project because I can apply S3 and CloudFront to host and deliver the frontend more efficiently.

### AI Assistant Tools and Developer Productivity

The event also introduced how AI assistant tools can support developers and business users. Tools such as Amazon Q Developer can help with code explanation, code generation, debugging, and documentation.

This gave me a better view of how AI can support the software development process. Instead of replacing developers, these tools can help developers work faster, reduce repetitive tasks, and focus more on solving the main problem.

## Key Takeaways

### Technical Takeaways

After attending the event, I understood more about the role of CloudFront in modern cloud architecture. It can improve performance, reduce traffic to the origin server, and provide a better access layer for web applications.

I also learned that AI systems need context, memory, and control mechanisms to work effectively in real business cases. A simple prompt is not enough for production-level AI applications.

In addition, I gained more understanding of serverless and event-driven architecture. Services such as Lambda and EventBridge can help automate workflows and reduce the need to maintain traditional servers.

### Project-Related Takeaways

The knowledge from this event can be applied to my internship project. For example, when deploying the frontend, I can use Amazon S3 with CloudFront to create a more realistic cloud deployment model.

For backend and data processing, I can think about using API Gateway, Lambda, EventBridge, DynamoDB, and CloudWatch to build a system that is easier to monitor and extend.

For AI processing, the event helped me understand that using AI services such as Bedrock should go together with clear input data, context design, and output validation.

### Personal Takeaways

This event helped me become more motivated to continue learning AWS. Listening to real engineers and community speakers made me realize that cloud computing is not only about knowing service names, but also about understanding how to design systems that are secure, scalable, and useful.

I also learned that communication, teamwork, and problem-solving are very important in real projects. Technical knowledge is necessary, but the ability to explain ideas, work with others, and adjust the solution based on real problems is equally important.

## Event Experience

### Learning from Real-World Speakers

The presentations were useful because they were based on real situations instead of only theory. I was especially interested in the CloudFront topic because it helped me understand how edge services improve performance and protect backend systems.

The speaker explained the concept in a clear way, which made it easier for me as a student and intern to follow the technical content.

### Observing Practical Project Experience

The LotusHacks sharing session was also meaningful because the team shared not only their final result, but also the difficulties they faced during the building process. This helped me understand that in real projects, bugs, time pressure, and changing ideas are normal.

From that, I learned that a team should focus on the core feature first, test early, and improve gradually.

### Connecting the Event to My Internship

After the event, I could connect several topics to what I was learning in the internship, especially S3, CloudFront, Lambda, EventBridge, AI integration, and system architecture.

This helped me prepare better for the next phase of the internship, where my team started discussing and building the final AWS-based project.

## Lessons Learned & Personal Engagement

### Lessons Learned

I learned that cloud architecture should balance performance, security, scalability, and cost.

I learned that CloudFront is not only a caching service, but also an important part of system performance and origin protection.

I learned that AI applications need proper context and system design to produce useful results.

I learned that building an MVP first is a practical way to test ideas and avoid overcomplicating the project.

### Personal Engagement

During the event, I actively listened to the technical sessions and took notes on topics related to CloudFront, AI application design, serverless architecture, and project development mindset.

I also used this event as an opportunity to observe how experienced engineers present technical ideas and how the AWS community shares knowledge. This gave me more motivation to improve my AWS skills and apply what I learned to the final internship project.

## Photo

![AWS Vietnam Community Day 2026](/images/4-EventParticipated/event1-community-day-photo.png)
