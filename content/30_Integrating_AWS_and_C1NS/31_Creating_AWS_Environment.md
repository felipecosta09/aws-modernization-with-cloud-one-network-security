---
title: "Creating the base AWS Environment"
chapter: false
weight: 31
pre: "<b>4.1 </b>"
---

Here is the base AWS environment that we will be building using CloudFormation template before deploying the Cloud One - Network Security:

![C1NS1](/images/C1NS_AWS_enviroment.png) 

{{% notice note %}}
<p style='text-align: left;'>
In this example you don't need to create the Inspection and Management subnet because the CloudFormation template suggested by the Cloud One - Network Security will create it for you.
</p>
{{% /notice %}}

----

## 1. Creating the base AWS environment using AWS CloudFormation Template

You can use the CloudFormation template bellow to create the infrastructure in same AZ with the 2 subnets, NAT Gateway, Internet Gateway, and the EC2 instances.

**Download** -> [CloudFormation Tempalte](/cft/CFT_Network_Security_Workshop.yml)

---

### 2. Go to the AWS Web Console and search for CloudFormation:

![C1NS1](/images/create_env.png) 

---

### 3. Select "Create stack"

![C1NS1](/images/create_env_2.png) 

---

### 4. Uploding the CloudFormation Template

- You will need to select the option "Upload a tempalte file"
- Click on "Choose the File" 
- Select the CloudFormation template that you Download in the step (1) from this page 
- Click on the button "Next"
