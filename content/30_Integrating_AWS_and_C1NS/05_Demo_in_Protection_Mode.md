---
title: "Integrating AWS with Cloud One Network Security"
chapter: false
weight: 80
pre: "<b>4.3 </b>"
---

### Integrating AWS with Cloud One Network Security

After you create a Cloud One account using this link here: [SingUp](https://cloudone.trendmicro.com/SignIn.screen#) on pre-requisites. Now we will be integrating your AWS account into Cloud One - Conformity to help you bring deep visibility around the possible drifts and misconfiguration over 80 different AWS Services mapping it with the most commom standard and framework in the market and with AWS Well-Architected Framework too :star_struck:


#### Login in Cloud One and go to Network Security

Upon signing into Cloud One, you’ll be prompted to select between the 6 services in Cloud One platform, select Conformity in the main page.

![Integration1](/images/integration1.png) 

![Integration2](/images/integration2_update.png) 

After it you will be able to begin adding your AWS account after you click in "Add Account". There are two ways to link your account: Automatically or Manually.

![Integration3](/images/integration3.png) 

![Integration4](/images/integration4.png) 

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

![Integration5](/images/integration5.png) 

To link your account, be it automatically or manually, a dedicated IAM role with two custom policies will be created in order to enable Cross Account Access. To verify the IAM role and the type of access necessary to use it, click Manual setup and review the attached custom policies.

![Integration6](/images/integration6.png) 

![Integration8](/images/integration8.png) 


Follow the automation instructions regarding AWS setup. After selecting “Launch Stack”, you’ll be taken to your AWS Management Console and prompted to check “I acknowledge…” After a few moments, a CloudFormation Stack will be created. Upon creation, go to Outputs, copy the CloudConformityRoleArn and paste into the box on Cloud One - Conformity:

![Integration7](/images/integration7.png) 

![Integration9](/images/integration9.png) 

![Integration10](/images/integration10.png) 

After adding the ARN to Cloud One - Conformity click "Next". Now you have successfully added your AWS account :cloud: :smile:

![Integration11](/images/integration11.png) 

The Cloud One - Conformity bot will automatically kick off a scan upon completion. After the scan has completed, you have successfully set up your account.

![Integration12](/images/integration12.png) 

Now you are all set up and you will bee able to see the results after couple minutes in the dashboard like te image below:

![Integration13](/images/integration13.png) 