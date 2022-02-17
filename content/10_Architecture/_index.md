---
title: "Network Security Architecture"
chapter: true
weight: 10
pre: "<b>2. </b>"
---

## Deployment Options 

Network Security is offered as an Amazon Machine Image (AMI). When you decide how to deploy Network Security in your network, we recommend that you choose one of the following deployment options.

Each deployment option is a reference architecture created for different common AWS environments. Choose the option that best suits your existing network structure and inspection needs. These deployment recommendations can also be modified to suit the individual requirements for your network.

The arrows in the images indicate the flow of network traffic through the VPCs and the Network Security instance.

---

#### Option 1 - Edge Protection Deployment

This deployment is designed to protect servers that primarily receive connections from the internet and is best suited to environments that require the following:

* A simple network design that protects web servers.
* Deployment of multiple virtual appliances.
* Inspection between the VPC and the Internet as well as between the VPC and a VPN gateway.
* A single VPC — this deployment option does not require Transit Gateways.
* Third party appliance integration that follows AWS best practices.

This deployment option does not indicate an IP address for the true source instance when a NAT Gateway is used for outbound internet traffic.

![Option1](/images/option1.png)

{{% notice info %}}
<p style='text-align: left;'>
This is the deployment that we will be using in our workshop :blush:
</p>
{{% /notice %}}

---

#### Option 2 - Centralized Network Appliance with Gateway Load Balancer for Inbound Traffic

This deployment is designed to protect servers that primarily receive connections from the internet.

This deployment option is best suited to environments that require the following:

* An environment that requires centralized security inspection for multiple VPCs across different AWS accounts.
* An environment that includes one or multiple Workload VPCs.
* A separate VPC (referred to as the Security VPC in the image below) where the Network Security virtual appliance and the Gateway Load Balancer are located.
* Traffic that flows through the Gateway Load Balancer VPC endpoint, located in a Workload VPC, without leaving the AWS network.

Refer to the image below for details on the environment structure and routing for this deployment. The numbered arrows represent the order of the flow of traffic through the environment. Green represents the request and orange represents the response.

![Option2](/images/option2.png)

{{% notice info %}}
<p style='text-align: left;'>
Dynamic auto-scaling and Inspection Bypass mode are not yet supported for Gateway Load Balancer in Network Security.
</p>
{{% /notice %}}

---

#### Option 3 - Centralized Network Appliance with Gateway Load Balancer for Outbound or Lateral Traffic:

This deployment is designed for AWS architectures that primarily send traffic from EC2 instances to the internet and/or between EC2 instances in different Workload VPCs.

This deployment option is best suited to environments that require the following:

* More than one Workload VPC that needs protection at the same time by a centralized Security VPC
* Environments that use Transit Gateways.

Refer to the image below for details on the environment structure and routing for this deployment. The numbered arrows represent the order of the flow of traffic through the environment. Green represents the request and orange represents the response.

![Option3](/images/option3.png)

{{% notice info %}}
<p style='text-align: left;'>
This topology does not inspect inbound connections.
</p>
{{% /notice %}}

---

#### Awesome that you got here already. :clap: Now that you understand the deployment options, let's see what resources you will need to get started with Cloud One Network Security.
