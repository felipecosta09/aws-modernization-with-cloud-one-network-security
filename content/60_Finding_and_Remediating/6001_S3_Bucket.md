---
title: "AWS S3 - lab"
chapter: false
weight: 81
pre: "<b>7.1 </b>"
---

### Scenario

In this scenario we have an use case where a customer by some mistake create a bucket and make it public and without encyrption. Our goal here is to detect the bucket and fix these two main security issues in this bucket configuration.

![scenario1](/images/scenario1.png)

### Automatically Finding the Misconfiguration

{{% notice warning %}}
<p style='text-align: left;'><b>
It's very important you did the the chapter 5 of the workshop before starting this one, because you will need a Cloud One account and the integration between Cloud One - Conformity and AWS. 
</b></p>
{{% /notice %}}

Using Cloud One - Conformity dashboard we will search for the misconfiguration associated with the scenario introduce in this lab.

#### 1. Log in to Cloud One, cloose the Conformity services, select the account on your left that you have integrated for this workshop and then click in "Browser All Checks"

![la2_s3](/images/lab_s3_1.png)

#### 2. Click in Filter checks to open the filter options for us to do some tunning for an easy way to investigate some checks around S3 Buckets

![la2_s3](/images/lab_s3_2.png)

#### 3. Define the Filter check

Here are the configs that you should apply

- On <b>Resource Types</b> search for S3 Bucket and press < Enter >
- On <b>Search Tages</b> add "Lab::2" and press < Enter >
- On <b>Status</b> uncheck "Success"

After you do the configurations just click on Filter Check again

![la2_s3](/images/lab_s3_3.png)

#### 4. Looking for the specific Conformity check to do the properly Remediation

Look for the following Conformity check on the right side of those check you will see a button called Resolve it will give you the steps by steps on how to remediate those misconfigurations.

- S3 Bucket Public Access Via Policy - [Knowledge Base Link](https://www.cloudconformity.com/knowledge-base/aws/S3/s3-bucket-public-access-via-policy.html#102741628407)
- Server Side Encryption - [Knowledge Base Link](https://www.cloudconformity.com/knowledge-base/aws/S3/server-side-encryption.html#102741628407)

![la2_s3](/images/lab_s3_4.png)

#### 5. View more details about the the Conformity Checks

Clicking on the Conformity checks will allow you to see more details about the misconfiguration that was found. You will also have the direct link to the resource to help you to review and fix the misconfiguration that have been found. 

![la2_s3](/images/lab_s3_5.png)

#### 6. Remediation 

Clicking in the "Resolve" button will bring you to the Conformity Knowledge base where you will find the step-by-step on how to remediate the misconfiguration found by Cloud One - Conformity.

![la2_s3](/images/lab_s3_6.png)

#### 7. Review the remediation  

After going through the remediation for those two use cases. You can go back to the main dashboard of Conformity and click in "Run Conformity Bot" this will kick off a new Conformity Run Bot process. 

You could also have real-time monitoring if you enable the RTM feature in Conformity, but becasue we didnt do it the default process will be running Conformity Bot checks every hour or you could manually force it too.
After couple minutes the Conformity Bot Check will finish and you will be able to check if the check now will appear as "Successed" and not "Failed" as before. 

![la2_s3](/images/lab_s3_7.png)
