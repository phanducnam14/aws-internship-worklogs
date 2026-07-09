---
title: "Blog 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---
# Deploying a Backend to AWS EC2 and the Bug Caused by Capital Letters

Blog post link: [Facebook - AWS Study Group FCJ](https://www.facebook.com/groups/awsstudygroupfcj/permalink/2184227519008875/)

When deploying a backend application from a local environment to AWS EC2, not every issue appears as a clear runtime error. The application may start successfully and the server may keep running, while some internal logic behaves incorrectly. In this case, the root cause came from a very small detail: uppercase and lowercase values in environment variables.

On a local Windows environment, the Node.js application read the .env file and handled configuration normally. However, after the source code was deployed to an EC2 instance running Ubuntu/Linux, several Boolean flags were no longer interpreted correctly. Some automated features stopped working, conditions returned false, and debugging took longer because the application did not throw an obvious error.

## Environment Variables in Backend Applications

In backend projects, environment variables are commonly used to separate configuration from source code. Instead of hard-coding regions, secret keys, database passwords, or runtime modes into the application, developers can store them in a .env file.

Example:

```env
ENV=development
REGION=ap-southeast-1
ENVIRONMENT_AUTO=True
```

This approach makes it easier to switch between development and production, reduces source code changes during deployment, and keeps configuration in a more manageable place. When deploying to EC2, the .env file is often copied to or manually created on the server so the application can read it at runtime.

## Initial Deployment Model

The first deployment model was simple: the developer pushed the source code and .env file from local machine to EC2 through SSH or Git, then ran the Node.js backend directly on the instance.

![Initial EC2 backend deployment with .env file](/images/3-BlogsTranslated/blog1-ec2-env-file.png)

The deployment flow included:

- Uploading source code to EC2.
- Creating or editing the .env file directly on the server.
- Starting the backend server with Node.js.
- Letting the application read environment variables from .env.

Everything seemed fine until the application started processing Boolean values.

## The Issue After Deploying to EC2

Locally, this flag worked as expected:

```env
ENVIRONMENT_AUTO=True
```

However, when running on EC2 Ubuntu/Linux, some condition checks stopped working correctly. For example:

```js
if (process.env.ENVIRONMENT_AUTO === "true") {
  // run auto configuration
}
```

In this case, "True" and "true" are not the same value. If the code only compares against the lowercase string "true", the condition fails even though the .env file was intended to enable the feature.

This type of bug is easy to miss because the application does not crash. Instead, it causes business logic to behave incorrectly, such as:

- Reading the wrong environment state.
- Skipping automated features.
- Treating Boolean configuration values incorrectly.
- Running with unexpected behavior but without a clear stack trace.

## Main Causes

### 1. Linux and runtime behavior are strongly case-sensitive

When moving from Windows to Linux, developers need to pay closer attention to case sensitivity. Environment variable values, file names, strings, and framework-level .env parsing can all create differences.

For Boolean values in .env, True, TRUE, and true are usually just different strings. If the application does not normalize the value before comparison, the logic can easily fail.

### 2. Manually managing .env files on EC2 is error-prone

Creating a .env file with nano .env on the server is quick, but it does not scale well as the system grows. This approach can lead to issues such as:

- Typing the wrong variable name or format.
- Missing variables across environments.
- Difficulty keeping development, staging, and production synchronized.
- Risk of exposing secrets if the instance is accessed improperly.

Values such as database passwords, API tokens, and secret keys should not be managed long-term through a plain file stored directly on the server.

## Quick Fix

The first fix was to standardize all Boolean values in .env as lowercase:

```env
ENVIRONMENT_AUTO=true
```

In the application code, the value should be normalized before comparison:

```js
const autoEnv = process.env.ENVIRONMENT_AUTO?.toLowerCase() === "true";
```

After updating the format and making the type conversion explicit, the application correctly recognized the environment state and the automated features worked more reliably.

## AWS Best Practice Direction

In the long term, storing .env directly on EC2 is not the best security practice. A better direction is to move configuration and secrets into a centralized service such as AWS Systems Manager Parameter Store or AWS Secrets Manager.

![EC2 retrieving secure configuration from Parameter Store](/images/3-BlogsTranslated/blog1-parameter-store.png)

With this model:

- The EC2 instance is assigned an appropriate IAM Role.
- The application uses the AWS SDK to retrieve configuration at runtime.
- Secrets do not need to live directly in source code or in a .env file on the server.
- Access is controlled through IAM policies.

Example flow:

```text
EC2 Instance -> IAM Role -> AWS Systems Manager Parameter Store
```

This approach makes environment configuration more centralized, improves security, scales better, and is more suitable for production workloads.

## Lessons Learned

A small uppercase/lowercase mismatch can cause an application to behave incorrectly after deployment. From this experience, several lessons stand out:

- Cloud Linux environments differ from local Windows environments more than expected.
- Small issues such as case mismatch, wrong data types, or invalid .env format can take a long time to debug.
- Environment variables are not just configuration; they affect security, operations, and scalability.
- Secrets should be managed by dedicated services instead of being stored long-term in files on the server.

## Conclusion

Deploying a backend to AWS EC2 is not only about running the application in the cloud. It is also about managing configuration consistently and securely. For small projects, a .env file may be enough to get started. However, as a system moves closer to production, AWS Systems Manager Parameter Store or AWS Secrets Manager should be considered for safer configuration and secret management.
