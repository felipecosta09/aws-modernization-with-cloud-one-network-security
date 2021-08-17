---
title: "Cloud One - Network Security Adding Cloud Account"
chapter: false
weight: 32
pre: "<b>4.2 </b>"
---

### Integrating AWS with Cloud One Network Security

After you create a Cloud One account using this link here: [Register](https://cloudone.trendmicro.com/register) from Prerequisites, you will be able to login in Trend Micro - Cloud One console and we can start the process of deploying the Network Security appliance using the setup wizard.

----

#### 1. Log in Cloud One and go to Network Security

Upon signing into Cloud One, you’ll be prompted to select between the 7 services in Cloud One platform, select Network Security in the main page.

![C1NS1](/images/Login_C1.png) 

![C1NS2](/images/C1NS_Service.png) 

---

#### 2. After it you will be able to begin adding your AWS account after you click in "Start Wizard".

![C1NS3](/images/C1NS_Wizard.png)

---

#### 3. Now we will need to create an IAM policy for the Network Security in your AWS account

Follow the steps-by-steps describe in the Cloud One console

![C1NS4](/images/Add_IAM_Policy.png) 

<details>
  <summary> -> <code>CLICK HERE</code> to see the steps by steps described in the console.</summary>

#### 3.1 Access your AWS account and search for IAM and after go to Policies and click on Create Policy

![C1NS1](/images/create_net_sec_1.png) 

#### 3.2 Slect the tab JSON, paste the JSON policy from Cloud One Network Security console and then click Next:Tags

![C1NS1](/images/create_net_sec_2.png) 

Here is the JSON polciy from Cloud One - Network Security:

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

#### 3.3 Click on Next:Review

![C1NS1](/images/create_net_sec_3.png) 

#### 3.4 Add the Name for the policy and click Create policy

You can use the recommended name for the policy -> <code>NetworkSecurityPolicy</code>

![C1NS1](/images/create_net_sec_4.png) 

#### 3.5 Policy created successfully 

![C1NS1](/images/create_net_sec_5.png) 

---

</details>
---

---

#### 4. After creating IAM Policy, now we will need to create a cross-account IAM Role in your AWS account

After doing the processes describe in the Cloud One console you will need to paste the Role ARN created from AWS console and paste here and then you will be able to click Create Account Name.

![C1NS1](/images/create_net_sec_6.png) 

<details>
  <summary> -> <code>CLICK HERE</code> to see the steps by steps described in the console.</summary>

#### 4.1 Access your AWS account and search for IAM and after go to Roles and click on Create Role
![C1NS1](/images/create_net_sec_7.png) 

#### 4.2 Create Role

-  For select type of trusted entity, choose Another AWS account
-  Copy and Paste the Account ID provide in the Cloud One console
  - **Account ID:** copy this information from Cloud One Wizard 
-  Check the Option Require external ID 
-  Copy and Paste the External ID provide in the Cloud One console.
  - **External ID:** copy this information from Cloud One Wizard 
-  Click Next:Permissions


![C1NS1](/images/create_net_sec_8.png) 

#### 4.3 Attach permissions policies 

- Search for the policy name that you creted on the previous step, if you used our recommendation you shoueld search for this here <code>NetworkSecurityPolicy</code>
- Select the Role 
- Click Next:Tags

![C1NS1](/images/create_net_sec_9.png) 


#### 4.4 Optional - Add Tags 

![C1NS1](/images/create_net_sec_10.png) 

#### 4.5 Add the Role Name, in our example is <code>NetworkSecurityRole</code>, review and click Create Role
![C1NS1](/images/create_net_sec_11.png)

#### 4.6 Once you create the role, search for the name of the role that you create and click in the name of the Role.

- If you used the recommended name for the Role, you shoudl search for this one here: <code>NetworkSecurityRole</code>
![C1NS1](/images/create_net_sec_12.png) 

#### 4.7 Copy the Role ARN and go back to the Cloud One - Network Security console
![C1NS1](/images/create_net_sec_13.png) 

#### 4.8 Paste the Role ARN and Click Create Account Name
![C1NS1](/images/create_net_sec_6.png) 

</details>
---

---

#### 5. Now you will need to give a name for this AWS account on Cloud One and click on "+ Add Cloud Account"
![C1NS1](/images/create_net_sec_14.png) 

#### 6. Once it is successfully and you have added the cloud account it's time to click Deploy Protection for us to deploy the Network Security AMI in the AWS environment

![C1NS1](/images/create_net_sec_15.png) 