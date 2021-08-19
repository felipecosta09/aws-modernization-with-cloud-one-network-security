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

---

#### 10. Now we will need to edit CloudFormation template (deploymentScript.yaml) that you downloaded from Cloud One console. 

You can use any text editor. In our example we are using [Visual Studio Code](https://code.visualstudio.com/download).

##### 10.1 Open CFT that you downloaded called - deploymentScript.yaml on your IDE

![C1NS1](/images/deploy_protec_10.png) 

---

##### 10.2 In the code, search for <code># -- END VTPS CLI</code>

![C1NS1](/images/deploy_protec_11.png) 

---

##### 10.3 Add the code bellow before the line of the string "# -- END VTPS CLI". These lines are to enable the forward event to the AWS CloudWatch and to use the America EST timezone.

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


##### 10.4  After making the changes, the code will be similar to the image bellow. The selection is the line that I added. Once changed, save the file.

{{% notice warning %}}
<p style='text-align: left;'>
<b>Be careful with the indention of the code, otherwise you will broke the template.</b>
</p>
{{% /notice %}}

![C1NS1](/images/deploy_protec_12.png) 

---

#### 11. Go back to the AWS Console in the service CloudFormation and click in "Create Stack"

![C1NS1](/images/deploy_protec_13.png) 

---

#### 12.  Select the "Upload a template file", choose the CloudFormation template and click "Next"

![C1NS1](/images/deploy_protec_14.png) 

---

#### 13.  Insert the Stack Name <code>Modernization-Workshop-Network-Security-Appliance</code> and click "Next"

![C1NS1](/images/deploy_protec_15.png) 

---
#### 14. (Optional) Add tags and click "Next"

![C1NS1](/images/deploy_protec_16.png) 

---
#### 15. Review, check the box "I acknowledge ..", and click on Create stack

![C1NS1](/images/deploy_protec_17.png)
![C1NS1](/images/deploy_protec_18.png)
![C1NS1](/images/deploy_protec_19.png)

---

#### 16. Wait until the successful creation of the stack and you will be ready to move to the next chapter.

![C1NS1](/images/deploy_protec_20.png) 

---
> **Et voila, we just generated completed the deployment of the Cloud One - Network Security Appliance in our AWS enviornment** 🤩 :cloud: 🤖 :rocket: