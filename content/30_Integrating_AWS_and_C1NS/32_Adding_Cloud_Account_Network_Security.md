---
title: "Cloud One - Network Security Adding Cloud Account"
chapter: false
weight: 32
pre: "<b>4.2 </b>"
---

### Integrating AWS with Cloud One- Network Security.

{{% notice info %}}
<p style='text-align: left;'>
A Cloud One Account is required to proceed. If you have not registered for a Cloud One account please go <a href="https://cloudone.trendmicro.com/register" target="_top">here.</a>
</p>
{{% /notice %}}

----

#### 1. Log in [Cloud One](https://cloudone.trendmicro.com/)
- Select the **Network Security** tile.

![C1NS1](/images/Login_C1.png) 

![C1NS2](/images/C1NS_Service.png) 

---

#### 2. Click on **Start Wizard**.

![C1NS3](/images/C1NS_Wizard.png)

---

#### 3. Create an IAM policy for Network Security in your AWS account

- Follow the step-by-step instructions as described in the Cloud One console.

![C1NS4](/images/Add_IAM_Policy.png) 

<details>
  <summary> -> <code>CLICK HERE</code> to see the steps by steps described in the console.</summary>

#### 3.1 Sign in to your [AWS account](aws.amazon.com/)
- Navigate to **IAM**
- From left-hand menu, select **Policies** under Access Management
- Click on **Create Policy**

![C1NS1](/images/create_net_sec_1.png) 

---

#### 3.2 Edit the policy.
- Select the tab **JSON** 
- Paste the JSON policy from Cloud One Network Security console
- Click on **Next: Tags**

![C1NS1](/images/create_net_sec_2.png) 

---

#### Here is the JSON policy from Cloud One - Network Security:

````
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "cloudconnectorEc2",
      "Effect": "Allow",
      "Action": [
        "ec2:DescribeImages",
        "ec2:DescribeInternetGateways",
        "ec2:DescribeInstances",
        "ec2:DescribeNetworkInterfaces",
        "ec2:DescribeAvailabilityZones",
        "ec2:DescribeVpcs",
        "ec2:DescribeRegions",
        "ec2:DescribeNatGateways",
        "ec2:DescribeSubnets",
        "ec2:DescribeKeyPairs",
        "ec2:DescribeRouteTables",
        "ec2:DescribeSecurityGroups"
      ],
      "Resource": "*"
    },
    {
      "Sid": "cloudconnectorIamPolicy",
      "Effect": "Allow",
      "Action": [
        "iam:GetPolicyVersion",
        "iam:GetPolicy"
      ],
      "Resource": "arn:aws:iam::*:policy/NetworkSecurityPolicy"
    },
    {
      "Sid": "cloudconnectorIamRole",
      "Effect": "Allow",
      "Action": [
        "iam:GetRole",
        "iam:ListAttachedRolePolicies"
      ],
      "Resource": "arn:aws:iam::*:role/NetworkSecurityRole"
    }
  ]
}
````
---

#### 3.3 Click on **Next: Review**

![C1NS1](/images/create_net_sec_3.png) 

---

#### 3.4 Add the Name for the policy
- **Name**: <code>NetworkSecurityPolicy</code>
- Click on **Create policy**

![C1NS1](/images/create_net_sec_4.png) 

---

#### 3.5 Policy created successfully

![C1NS1](/images/create_net_sec_5.png) 

</details>
---

---

#### 4. Create a IAM Role in your AWS account for cross-account access

- Follow the step-by-step instructions as described in the Cloud One console.

After doing the processes describe in the Cloud One console you will need to paste the **Role ARN** created from AWS console and paste here and then you will be able to click Create Account Name.

![C1NS1](/images/create_net_sec_6.png) 

<details>
  <summary> -> <code>CLICK HERE</code> to see the step by step instruction as described in the console to create an IAM Role.</summary>

---

#### 4.1 Sign in to [AWS](aws.amazon.com/)
- Navigate to **IAM**
- From the left-hand menu, select **Roles** under access management
- Click on **Create Role**
![C1NS1](/images/create_net_sec_7.png)

---

#### 4.2 Create IAM Role for Cloud One Network Security

-  **Select type of trusted entity**: Another AWS account
-  Paste the **Account ID** provided in the Cloud One console 
-  **Check** the Option Require external ID 
-  Paste the **External ID** provided in the Cloud One console. 
-  Click on **Next: Permissions**


![C1NS1](/images/create_net_sec_8.png) 

---

#### 4.3 Attach permissions policies 

- Search for the policy name that you created on the previous step, if you used our recommendation search for <code>NetworkSecurityPolicy</code>
- **Select** the role 
- Click on **Next: Tags**

![C1NS1](/images/create_net_sec_9.png) 

---

#### 4.4 Add the Role Name and (Optional - Add Tags)
- **Role Name**: <code>NetworkSecurityRole</code>
- Click on **Create Role**

![C1NS1](/images/create_net_sec_10.png) 

![C1NS1](/images/create_net_sec_11.png)

---

#### 4.5 After you successfully created the Role. 
- Search for the name of the role: <code>NetworkSecurityRole</code>
- Click on the **Role Name**
![C1NS1](/images/create_net_sec_12.png)

---

#### 4.6 Copy the Role ARN and navigate back to the Cloud One - Network Security console
![C1NS1](/images/create_net_sec_13.png) 

---

#### 4.7 Paste the Role ARN 
- Click on **Create Account Name**
![C1NS1](/images/create_net_sec_6.png) 

</details>
---

---

#### 5. Create a name for this AWS account in Cloud One
- **Account Name:** <code>Network Security Workshop</code>
- Click on **+ Add Cloud Account**
![C1NS1](/images/create_net_sec_14.png) 

#### 6. You have added your AWS account successfully.
- Click on **View Security Posture**

![C1NS1](/images/create_net_sec_15.png)

---

#### 7. The security posture page is to see how the outbound traffic in your environment is currently protected. 

To evaluate your security posture, Network Security looks at the VPCs across all of your AWS regions to determine if the Elastic Network Interfaces (ENIs) in those VPCs have outbound internet access.
Use this assessment to determine where to deploy Network Security for the assets in your environment that need outbound protection.

- Click on **Deploy Protection** to continue.

![C1NS1](/images/create_net_sec_16.png)

---
#### Congrats!! You have successfully integrated your AWS Account with Cloud One - Network Security :cloud: :laptop: :rocket:
