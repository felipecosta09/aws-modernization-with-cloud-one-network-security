---
title: "Cloud One - Network Security Deploying AMI"
chapter: false
weight: 33
pre: "<b>4.3 </b>"
---

### Deploying Cloud One - Network Security Appliance 

Once you finish the steps to add the Cloud Account, you can start deploying the Network Security appliance. Here are the steps-by-steps:

----

#### 1. Select a cloud account that you created previously and click on Next: Select Asset

![C1NS1](/images/deploy_protec_1.png) 

---

#### 2. Select the VPC that you will deploy the Network Security Appliance.

- If you used the initial CloudFormation template to build the base AWS environment, you will neeed to select the VPC with the Internet Gateway Name **IGW - C1NS-labenvironment**
![C1NS1](/images/deploy_protec_2.png) 

---

#### 3. Select the SSH Key Pair that the Appliance will use and the API Key from Cloud One. Then you can click "Next: Use Deployment Script"

{{% notice note %}}
<p style='text-align: left;'>
The CloudFormation template will create 2 new subnets for you, the Inspection and the Management subnets.
</p>
{{% /notice %}}

![C1NS1](/images/deploy_protec_3.png) 

---

#### 4. Click on Generate a new API Key and you will forward to the page below where you will need to select your Cloud One acccount and click Go

![C1NS1](/images/deploy_protec_4.png) 

---

#### 5. Click on New to create the API Key

![C1NS1](/images/deploy_protec_5.png) 

---

#### 6. Select Full Access Role, the prefer language for you and the perfer Timezone. After you can click Next

![C1NS1](/images/deploy_protec_6.png)

---

#### 7. This will generate the API Key you will need to click Copy to Clipboard and save it properly. Because after you close this screen you will not be able to retrieve it later. 

![C1NS1](/images/deploy_protec_7.png) 

---

#### 8. Now you will need to go back to the tab with the Cloud One - Network Security wizard and paste the API key there, than you can click Next: Use Deployment Script

![C1NS1](/images/deploy_protec_8.png) 

---

#### 9. Click in Download to get the CloudFormation template

![C1NS1](/images/deploy_protec_9.png) 