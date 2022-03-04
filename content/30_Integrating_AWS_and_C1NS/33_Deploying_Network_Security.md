---
title: "Cloud One - Network Security Deploying AMI"
chapter: false
weight: 33
pre: "<b>4.3 </b>"
---

### Deploying Cloud One - Network Security Appliance 

Amazon Web Services (AWS) allows you to scale your network deployment as needed without investing in hardware appliances. Deploy Network Security in AWS by placing Network Security instances inline within your AWS Virtual Private Cloud (VPC).

---

#### 1. In the Cloud One Network Security console.
- **Select** the cloud account created previously
- Click on **Next: Select Asset**

![C1NS1](/images/deploy_protec_1.png) 

---

#### 2. Select the VPC that you will deploy the Network Security Appliance.

- Select the **VPC** with the Internet Gateway Name: **IGW - C1NS-labenvironment**
- Click on **Next: Select Availability Zones**
![C1NS1](/images/deploy_protec_2.png) 

---

#### 3. Here you can select the Availability Zone(s) that the Cloud One - Network Security Appliance will include in the deployment script. 
- Click on **Next: Finalize Parameters** 

{{% notice note %}}
<p style='text-align: left;'>
Leave as default with the one AZ selected for this workshop.
</p>
{{% /notice %}}

![C1NS1](/images/deploy_protec_3.png) 

---

#### 4. Verify Network Asset
This steo verifies that the selected network asset can support dep ovment for the Network Securitv virtual appliance.
- Click on **Next: Finalize Parameters** 

![C1NS1](/images/deploy_protec_4.png) 

---

#### 5. Finalize parameters
- Select the SSH Key Pair that we created before for this workshop
- Click on **Next: Use Deployment Script**

![C1NS1](/images/deploy_protec_5.png)

---

#### 6. Click on **Download** to get the CloudFormation template

{{% notice note %}}
<p style='text-align: left;'>
The CloudFormation template will create 2 new subnets for you, the Inspection and the Management subnets.
</p>
{{% /notice %}}

![C1NS1](/images/deploy_protec_6.png) 

---

#### 7. Edit the CloudFormation template (deploymentScript.yaml) downloaded previously from Cloud One console. 

You can use any text editor or IDE. In our example we are using [Visual Studio Code](https://code.visualstudio.com/download).

---

##### 7.1 Open the CloudFormation template that you downloaded called - **deploymentScript.yaml**

![C1NS1](/images/deploy_protec_10.png) 

---

##### 7.2 In the code, search for <code>END VTPS CLI</code>

![C1NS1](/images/deploy_protec_11.png) 

---

##### 7.3 Add the code snippet provided **above** the line string  with **END VTPS CLI**. 

These lines are to enable the event forwarding to AWS CloudWatch using the America EST timezone.

```
  edit
- |
  log
- |
  cloudwatch inspection-event enable
- |
  exit
- |
  commit
- |
  exit
- |
  save-config -y
- |
  edit
- |
  gen
- |
  timezone America New_York
- |
  exit
- |
  commit
- |
  exit
- |
  save-config -y
- |
```

---


##### 7.4  After making the changes, the code will be similar to the image below. 
The selection are the lines that I added. 

- Once changed, **save the file**.

{{% notice warning %}}
<p style='text-align: left;'>
<b>Be careful with the indention of the code, otherwise the template format may break.</b>
</p>
{{% /notice %}}

![C1NS1](/images/deploy_protec_12.png) 

---

#### 8. Navigate to the [AWS Console](https://aws.amazon.com/)
- Navigate to **CloudFormation**
- Click on **Create Stack with new resources**

![C1NS1](/images/deploy_protec_13.png) 

---

#### 9.  Create Stack
- Select the **Upload a template file** 
- Click on **Choose file** 
- Choose the CloudFormation template: **deploymentScript.yaml**
- Click on **Next**

![C1NS1](/images/deploy_protec_14.png) 

---

#### 10.  Specify Stack details.
- Stack Name: <code>Modernization-Workshop-Network-Security-Appliance</code>
- Click on **Next**

![C1NS1](/images/deploy_protec_15.png) 

---
#### 11. (Optional) Configure stack options
- Add **Tags** if desired 
- Click on **Next**

![C1NS1](/images/deploy_protec_16.png) 

---
#### 12. Review deployment. 
- Check the box "I acknowledge .."
- Click on **Create stack**

![C1NS1](/images/deploy_protec_17.png)
![C1NS1](/images/deploy_protec_18.png)
![C1NS1](/images/deploy_protec_19.png)

---

#### 13. Wait until the successful creation of the stack before you move to the next chapter.

![C1NS1](/images/deploy_protec_20.png) 

---
> **Et voila, we just generated completed the deployment of the Cloud One - Network Security Appliance in our AWS environment** 🤩 :cloud: 🤖 :rocket:
