---
title: "Aws Elastic Computing Cloud"
date: 2019-10-25T11:30:47+01:00
draft: false
author: "Rosana"
---

Elastc Computing Cloud or EC2 is one of the first Amazon Web Services you will want to use for working with machines in the cloud that will host your web application or execute some computing tasks.
With EC2 you can launch instances that will behave as if you had your own server and you will be able to manage it in different ways.

To start, before launching your EC2 instance you can choose an Amazon Machine Image (AMI), which contains basic software you will want your machine to have such as an operative system as well as some installed language interpreters like Python or machine learning applications like TensorFlow...etc 

After choosing the Amazon Machine Image (AMI) you can select the type of instance (t2, t3, m5..)


## EBS - Elastic Block Storage
Blocks of storage that you can connect with any EC2 instance, you can add as many EBS as you want to a EC2 instance but an Elastic Block Storage can only be connected with one instance at a time.

### Instance Store Volumes
Some EC2 instance types allow adding Instance Store Volumes, which are virtual devices that are phisically attached to the instance hardware and are completely ephimeral, meaning that if the machine is shut down, all the data stored in the Instance Store Volume will be lost.

### EFS - Elastic File System
It's a storage option that can be shared by multiple EC2 instances and can be created using any file system you want.