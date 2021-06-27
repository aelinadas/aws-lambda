# AWS Lambda - Function As A Service

### PROJECT DESCRIPTION

FaaS is the concept of serverless computing via serverless architectures. 
Software developers can leverage FAAS to deploy a function
They are expected to start within milliseconds and process individual requests and then the process ends.


This repository contains password reset functionality that is utilized by webapp [Bookstore](https://github.com/aelinadas/bookstore).
The function is built and deployed on AWS Lambda, by leveraging CircleCI pipeline, for every commit.
Every time a request is published to `password_reset` topic on **Amazon Simple Notification Service(AWS SNS)**, the lambda function is triggered.
The Lambda function validates if user's email record is available on Dynamo DB, if present ensures that the user has expired the TTL of 15 mins else creates a unique reset link, using UUID, and sends it to requestor email leveraging **Amazon Simple Email Service(AWS SES)** and later update the record on **Dynamo DB** with new TTL  

---

### ARCHITECTURE

<img alt="Lambda" src="https://github.com/aelinadas/aws-lambda/blob/main/images/Lambda.png" />

---

### INFRASTRUCTURE

The infrastructure required by the Lambda function is built using **Terraform**. Find more information regarding infrastructure in this [file](https://github.com/aelinadas/aws-infrastructure/blob/main/lambda.tf)
