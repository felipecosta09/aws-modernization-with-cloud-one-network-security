---
title: "Creating the base AWS Environment"
chapter: false
weight: 31
pre: "<b>4.1 </b>"
---

---

## 1. Creating the base AWS environment using AWS CloudFormation Template

You can use the CloudFormation template below to create the infrastructure in same AZ with the 2 subnets, NAT Gateway, Internet Gateway, and the EC2 instances.

**Download** -> [CloudFormation Template](/cft/CFT_Network_Security_Workshop.yml)

---

#### Here is the architectural diagram of the cloudformation template.

![C1NS1](/images/C1NS_AWS_enviroment.png) 

{{% notice note %}}
<p style='text-align: left;'>
In this example, you don't need to create the Inspection and Management subnets because the CloudFormation template suggested by the Cloud One - Network Security documentation will create them for you.
</p>
{{% /notice %}}


---

### 2. Go to the [AWS Console](https://aws.amazon.com/) and search for **CloudFormation**:

![C1NS1](/images/create_env.png) 

---

### 3. Select **Create stack**

![C1NS1](/images/create_env_2.png) 

---

### 4. Uploading the CloudFormation Template

- Select the option to **Upload a template file**
- Click on **Choose the File** 
- Select the CloudFormation template that you downloaded in Step 1 above.
- Click on **Next**

![C1NS1](/images/create_env_3.png) 

---

### 5. Specifying additional stack parameters

{{% notice info %}}
<p style='text-align: left;'>
A Key Pair is required before continuing this CloudFormation deployment. If you need help creating a Key Pair -> <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html#having-ec2-create-your-key-pair" target="_top">Create a key pair</a>
</p>
{{% /notice %}}


<details>
  <summary> -> <code>CLICK HERE</code> to see how to create key pair</summary>

**AWS Console -> EC2 -> Key Pairs -> Create key pair**

![C1NS1](/images/create_env_9.png) 

</details>
<br>

- **Stack Name:**  <code>Network-Security-Workshop</code>

- **InspectionVPCCIDR:** the CIDR that you want to use for the VPC. You don't need to change it, if you don't want to change the default configuration.
    
- **KeyPair:** Your KeyPair name

- **MyPublicIP:** Your public IP in CIDR. (e.g. 191.162.228.91/32 . You can grab it using a few tools or websites (https://ipinfo.io/ip). It will be use to only allow your IP to access the vulnerable application (DVWA))

- **ProtectedPrivateSubnetAZ:** the AZ what you want to use to your Private subnet.

- **ProtectedPrivateSubnetCIDR:** the CIDR that you want to use for the Private. You don't need to change it, if you don't want.

- **ProtectedPublicSubnetAZ:** the AZ what you want to use to your Public subnet.

- **ProtectedPublicSubnetCIDR:** the AZ what you want to use to your Public subnet. You don't need to change it, if you don't want to.

---

### 5.1. Stack details example:

![C1NS1](/images/create_env_4.png) 

---

### 6. Configure stack options

Leave as fields as default and click **Next**, or optionally define tags to the environment if desired.

![C1NS1](/images/create_env_5.png) 

---

### 7. Review the template parameters 
- Mark the checkbox the **"I acknowledge... "**
- Click on **Create Stack**

![C1NS1](/images/create_env_6.png) 

![C1NS1](/images/create_env_7.png) 

![C1NS1](/images/create_env_8.png) 

---

### 8. Follow up the events during creation of the stack.
- Select the **Events** tab
- Click **Refresh**

![C1NS1](/images/create_env_10.png) 

---

### 9. Ensure the stack status has reached **Create_Complete**. 
- Select the **Stack info** tab

![C1NS1](/images/create_env_11.png) 

---

> **Now it's time for us to integrate Cloud One Network Security with AWS :cloud: :laptop: :rocket:**
