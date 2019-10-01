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


------------------------------

###### AWS Edge Location
Is an AWS datacenter which does not contain AWS services. Instead it is used to deliver content to parts of the world. Similar to how CloundFront works, it catches items such as PDF files reducing the amount of space/time/latency required for a request to be resolved.

###### Regions
Greographically separated spaces. Each of them will have one or many Availability Zone. The location of the data centers are grouped by availability zones and their specific location is kept secret. If one availability zone is out of connection due to any incident, you can use another availability zone.
You would usually use a VPC (Virtual Private Cloud) to connect datacenters in different availability zones.
Groupings of independently separated data centers in a specific geographic regions known as "Ava
- High availability
- Fault tolerance

###### AWS Security model
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

