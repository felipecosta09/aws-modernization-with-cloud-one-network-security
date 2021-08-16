---
title: "Cloud One - Network Security Deployment"
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



</details>
---

---

#### 5. Now you will need to give a name for this AWS account on Cloud One and click "+ Add Cloud Account"

#### 6. Once it is successfully created you can click "Close"