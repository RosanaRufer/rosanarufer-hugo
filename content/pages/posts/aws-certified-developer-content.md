---
title: "Aws Certified Developer Content"
date: 2019-10-01T11:50:11+01:00
draft: true
author: "Page author"
---

## Content
- AWS Store Service (S3)
- Amazon Simple Queue Service (SQS)
- Amazon Simple Notification Service (SNS)
- Amazon Simple Workflow Service SWF
- Amazon Elastic Compute Cloud (EC2)
- Amazon DynamoDB
- AWS Elastic Beanstalk
- AWS CloudFormation

- Amazon Elastic Container Service (ECS)


------------------------------

### AWS Edge Location
Is an AWS datacenter which does not contain AWS services. Instead it is used to deliver content to parts of the world. Similar to how CloundFront works, it catches items such as PDF files reducing the amount of space/time/latency required for a request to be resolved.

### Regions
Greographically separated spaces. Each of them will have one or many Availability Zone. The location of the data centers are grouped by availability zones and their specific location is kept secret. If one availability zone is out of connection due to any incident, you can use another availability zone.
You would usually use a VPC (Virtual Private Cloud) to connect datacenters in different availability zones.
Groupings of independently separated data centers in a specific geographic regions known as "Ava
- High availability
- Fault tolerance

### AWS Security model
- Your responsibility
> IAM
> Multy-factor authentication
> Password/key rotation
> Access advisor
> Security groups
> Resource-based policies
> Access control lists
> VPC
> Port scannir is forbidden 
> OSS-level patches (except for AWS Lambda)

- AWS's responsibility
> Physical server level and below
> ...
> DDOS Protection
...

### Services clasification
We can group AWS services into six groups:
1. Compute
2. Databases
3. Storage
4. Developer Tools
5. Management Tools
6. App Services

#### 1. Compute
- Elastic Beanstalk
- EC2 - Elastic Computing Cloud
- ECS - Elastic Container Service
- Lambda

#### 2. Databases
- RDS => Relational database
- DynamoDB => NoSQL database
- Elastic Cache => In-Memory Cache Engine
- RedShift => 

#### 3. Storage
- S3 -  AWS Storage service => Object storage service: Will store things like files to be used in the application
- Glacier
#### 4. Developer Tools
- X-Ray
- CodeCommit
- CodeDeploy
- CodeBuild
- CodePipeline
- CodeStar
#### 5. Management Tools
- CloudWatch
- Cloud Formation
- Systems Manager
#### 6. App Services
- SNS - "Simple" Notification Service
- SWF - "Simple" Workflow Service
- SQS - "Simple" Queue Service
- Step Functions 
- Apy Gateway

### IAM (Identity and Access management)
It's where you manage your AWS **users**, **groups** and **roles**, and their access to AWS accounts and services (through IAM Policies)
> IAM is global to all regions, creating a user account will apply to all the regions.
Every new user you create has *non-explicit deny* to access all services.

It's good practice to create a user to use instead of *root* user and use the non-root user for day-to-day work. When we create a user, they don't have any access to anything. You need to create a group.
-> Activate 2FA (two options: phisical or virtual)
-> Create user
-> Crete user group
-> Password policy
Configures the amount of characters, numbers, upper-cases...etc for, reset periods...etc for user passwords

=> Principle of Least Privilege: Give users the less amount of 

### IAM Policies

There are some prepared policy templates like 'admin' with allow all or 'new user' with deny all.
The policy templates have three main properties:
* Effect
* Action
* Resource

The JSON format of a policy template looks like this:
{
    "Version": "2019-02-12",
    "Statement": [
        {
            "Effect": "Allow",
            "Action" [
                "S3:Get*",
                "s3:List*"
            ],
            "Resource": "*"
        }
    ]
}

# Resource type: BUCKET VS. OBJECT




