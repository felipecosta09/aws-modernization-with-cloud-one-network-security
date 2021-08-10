---
title: "Deploy Cloud One - Network Security"
chapter: false
weight: 50
pre: "<b>4. </b>"
---

### Architecture Base for the Lab

To simulate a real customer environment, we will use a pre-built Cloud Formation template that will create the following resources all in the same AZ:

- 2 - Subnets
- 1 - NAT Gateway
- 1 - Internet Gateway
- 5 - EC2 instances
- 1 - Cloud One - Network Security Instance

As a recommended deployment method in the Cloud One - Network Security documentation, we will use the follow topology on the AWS environment for our lab.

![Edge_Deployment](/images/C1NS_Edge_Deployment.png) 

{{% notice note %}}
<p style='text-align: left;'>
In this example you don't need to create the Inspection and Management subnet because the CloudFormation template suggested by the C1NS will create for you these 2 subnets.
</p>
{{% /notice %}}