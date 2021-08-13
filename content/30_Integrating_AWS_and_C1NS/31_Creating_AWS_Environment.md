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

![C1NS1](/images/create_env_3.png) 

---

### 5. Specifying additional stack parameters

- **Stack Name:**  Name of your stack

- **InspectionVPCCIDR:** the CIDR that you want to use for the VPC. You don't need to change it, if you don't to change the default configuration.
    
- **KeyPair:** Your keypair Name

- **MyPublicIP:** Your public IP in CIDR. (e.g. 191.162.228.91/ 32 . You can grab it using a few tools or websites (https://ipinfo.io/ip). It will be use to only allow your IP to access the vulnerable application (DVWA))

- **ProtectedPrivateSubnetAZ:** the AZ what you want to use to your Private subnet

- **ProtectedPrivateSubnetCIDR:** the CIDR that you want to use for the Private. You don't need to change it, if you don't want.

- **ProtectedPublicSubnetAZ:** the AZ what you want to use to your Public subnet

- **ProtectedPublicSubnetCIDR:** the AZ what you want to use to your Public subnet. You don't need to change it, if you don't want to.

{{% notice info %}}
<p style='text-align: left;'>
Don't forget to create the Key Pair before creating the CloudFormation stack. Here is the link how to do it -> <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html#having-ec2-create-your-key-pair" target="_top">Create a key pair</a>
</p>
{{% /notice %}}


<details>
  <summary> -> <code>CLICK HERE</code> to see how to create key pair</summary>

**AWS Console -> EC2 -> Key Pairs -> Create key pair**

![C1NS1](/images/create_env_9.png) 

</details>
---

---

### 5.1. Stake details example:

![C1NS1](/images/create_env_4.png) 

---

### 6. Configure stack options

You could add some tags for this environment, but it's not mandatory. Or you can just click Next.

![C1NS1](/images/create_env_5.png) 

---

### 7. Review the parameters, mark the checkbox the "I acknowledge... " and click Create Stack

![C1NS1](/images/create_env_6.png) 

![C1NS1](/images/create_env_7.png) 

![C1NS1](/images/create_env_8.png) 

---

### 8. You can follow up the creattion of the stack thorugh the events in the CloudFormation:

![C1NS1](/images/create_env_10.png) 

---

### 9. Once it gives you the "Create Complete" in the stack view we are good to move for the next step that will be the deployment of the Cloud One Network Security.

![C1NS1](/images/create_env_11.png) 

---

> **Now it's time for us to deploy Cloud One Network Security Appliance in AWS :cloud: :laptop: :rocket:**