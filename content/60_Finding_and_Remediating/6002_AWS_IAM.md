---
title: "AWS IAM - lab"
chapter: false
weight: 82
pre: "<b>7.2 </b>"
---

### Scenario

In this scenario we have an use case where a customer by some mistake created an IAM Role Policy overly permissive. Our goal here is to detect the IAM role and fix it to be not very overly permissive.

![scenario2](/images/scenario2.png)


#### 1. Log in to Cloud One, cloose the Conformity services, select the account on your left that you have integrated for this workshop and then click in "Browser All Checks"

![la2_s3](/images/lab_s3_1.png)

#### 2. Click in Filter checks to open the filter options for us to do some tunning for an easy way to investigate some checks around AWS IAM

![la2_s3](/images/lab_s3_2.png)

#### 3. Define the Filter check

Here are the configs that you should apply

- On <b>Services</b> search for IAM and press < Enter >
- On <b>Search Tages</b> add "Lab::3" and press < Enter >
- On <b>Status</b> uncheck "Success"

After you do the configurations just click on Filter Check again

![la3_iam](/images/lab_iam_3.png)


#### 4. Looking for the specific Conformity check to do the properly Remediation

Look for the following Conformity check on the right side of those check you will see a button called Resolve it will give you the steps by steps on how to remediate those misconfigurations.

- IAM Role Policy Too Permissive - [Knowledge Base Link](https://www.cloudconformity.com/knowledge-base/aws/IAM/iam-role-policy-too-permissive.html#102741628407)

Clicking on (+) icon on the left side of the Conformity checks will allow you to see more details about the misconfiguration that was found. You will also have the direct link to the resource to help you to review and fix the misconfiguration that have been found. 

![la2_s3](/images/lab_iam_4.png)

#### 5. Remediation 

Clicking in the "Resolve" button will bring you to the Conformity Knowledge base where you will find the step-by-step on how to remediate the misconfiguration found by Cloud One - Conformity. 
In this case you will find multiple use cases for remediation and you can choose the best approach based in your Least Privilege Access strategy for giving permission for users and resources in the cloud.

For this lab you could apply the Case C in the Knowledge Base:

![la2_s3](/images/lab_iam_6.png)

#### 6. Review the remediation  

After going through the remediation for those two use cases. You can go back to the main dashboard of Conformity and click in "Run Conformity Bot" this will kick off a new Conformity Run Bot process. 

You could also have real-time monitoring if you enable the RTM feature in Conformity, but becasue we didnt do it the default process will be running Conformity Bot checks every hour or you could manually force it too.
After couple minutes the Conformity Bot Check will finish and you will be able to check if the check now will appear as "Successed" and not "Failed" as before. 

![la2_s3](/images/lab_s3_7.png)
