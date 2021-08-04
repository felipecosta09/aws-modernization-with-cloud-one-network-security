---
title: "Finding and Remediating Misconfigurations"
chapter: false
weight: 80
pre: "<b>7. </b>"
---

### Use cases of possible cloud misconfiguration and how to fix it

We have prepared a CloudFormation Template with some common use case of misconfiguration around to the main AWS services that we see in many customers. This way you will be able to run the CFT in your own AWS account for some practices or you could deplpy the CFT in an AWS account provided for a lab propose in a Security Immersion Day event. Here are some the use cases that we created for you:

1.  <b>AWS S3 Bucket</b>
    - S3 Bucket Publix Access Via Policy
    - S3 Server Side Encryption

2.  <b>AWS IAM</b>
    - Overly Permissive IAM Role

3.  <b>AWS SQS and AWS SNS</b>
    - Unecrypted SQS queue
    - SNS Topics Disable

:warning: For the first 3 labs you will need to deploy this CloudFormation stack that will have those labs ->  <b>[LINK](https://trend-aws-security-immersion-day.s3.amazonaws.com/template.json) </b>

#### Populating the AWS account with misconfigurations for the Labs

- Back in the AWS account, go to the CloudFormation console:
[AWS Cloud Formation](https://console.aws.amazon.com/cloudformation/)

- Select Create stack -> With New Resources
![Populating_AWS](/images/populating.png)

- Use the following CloudFormation tempalte link to create the stack in the AWS
https://trend-aws-security-immersion-day.s3.amazonaws.com/template.json

- Paste the link into Amazong S3 URL field and click next:
![Populating_AWS_2](/images/populating2.png)

- Set up the name of the CloudFormation stack
![Populating_AWS_3](/images/populating3.png)

- Click Next
![Populating_AWS_4](/images/populating4.png)

- Scroll down, check the box to acknoledge and after click in Create Stack
![Populating_AWS_5](/images/populating5.png)

- After couple minutes the stack will be completed and you will be able to start the labs
![Populating_AWS_6](/images/populating6.png)

----------------------------------------------------------------------------------------------------------------------

-  <b>Scanning IaC CloudFormation Template and fixing it</b>
    - Enable S3 Block Public Access for S3 Buckets
    - S3 Bucket Default Encryption
    - S3 Bucket Logging Enabled
    - VPC Flow Logs Enabled

:warning: For the template scanner you will need to download this CloudFormation Template to use in your IDE for the exercise ->  <b>[LINK](https://trend-aws-security-immersion-day.s3.amazonaws.com/lab5.template.yaml) </b>

Let's start those exercises :laptop: