---
title: "Deploy Cloud One - Network Security"
chapter: false
weight: 30
pre: "<b>4. </b>"
---

### Architecture for the lab

---

To simulate a real customer environment, we will use a pre-built CloudFormation template that will create the following resources all in the same Availibility Zone (AZ):

- 2 - Subnets
- 1 - NAT Gateway
- 1 - Internet Gateway
- 5 - EC2 instances
- 1 - Cloud One - Network Security Instance

As a recommended deployment method in the Cloud One - Network Security documentation, we will use the follow topology on the AWS environment for our lab.

![Edge_Deployment](/images/C1NS_Edge_Deployment.png) 


