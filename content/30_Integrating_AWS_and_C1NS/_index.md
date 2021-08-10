---
title: "Deploy Cloud One Network Security"
chapter: false
weight: 50
pre: "<b>4. </b>"
---

### Create the Environment

To simulate a real customer environment, we will use a pre-built Cloud Formation template that will create 2 subnets, NAT Gateway, Internet Gateway, and the EC2 instances, all in the same AZ.

As a recommended deployment method in the C1NS documentation, we will use 2 subnets in this scenario. Bellow you can see the topology of the AWS environment before the C1NS deployment.

![Edge_Deployment](/images/C1NS_Edge_Deployment.png) 

Note: In this example you don't need to create the Inspection and Management subnet because the CloudFormation template suggested by the C1NS will create for you these 2 subnets.