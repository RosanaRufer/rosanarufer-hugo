---
title: "Aws Security Groups"
date: 2019-10-01T11:30:47+01:00
draft: false
author: "Rosana"
---

Security groups in AWS are a set of rules that describe which conditions must be met for an AWS machine to accept connections.
The available rules are:

* Protocol
* Port
* IP address

In normal firewalls we also have *action* and *destination* rules, but in AWS all rules are created with the following constant values:

* Action: Allow
* Destination: "Me" as the AWS machine.

We configure *security groups* with these rules and we can assign an instance with **one or more** security groups. 


