---
title: "Automated Process to create IaC pipeline with Security"
chapter: false
weight: 51
pre: "<b>4.1 </b>"
---

### Using the CloudFormation Template to build the IaC pipeline in you AWS account

Here is the link to the Git repository with the CloudFormation tempalte to build the IaC archictecture into your AWS account-> [GitHub Repository](https://github.com/fernandostc/AWS_IaC_pipeline_with_Security)

![Automated](/images/automated_iac.png)

Let's build the CloudFormation Template>

#### Create Stack

Go to AWS Console and search for CloudFormation and after click in "Create Stack"

![create](/images/create_stack.png)

Save the CloudFormation template provided in the Git Repository before or you can use the GIST link here to easily get the file: [GitHub Gist Link](https://gist.github.com/fernandostc/be67b1a0be68c4f53968e3e7ad82f84a)

After upload the cloudformation tempalte to AWS click in "Next"
![create1](/images/create_stack1.png)

Most of the parameters are pre-configured already, but you still need to define the <b>"Stack Name"</b> and the <b>"Cloud One - Conformity API Key"</b>

- <b>StackName</b> -> Can be the name that you prefer

- <b>Cloud One - Conformity API Key</b> -  In the <b>"Lab 3"</b> has a explanation on how to get the API Key in the Cloud One - Conformity console

After filling up the two fields missing informatuon click "Next"
![create2](/images/create_stack2.png)

Click "Next" again
![create3](/images/create_stack3.png)

After you will need to scroll down to acknowledge that AWS will be creating an IAM resource for the Roles and Policies needed for the lab and after click in "Create stack"
![create4](/images/create_stack4.png)


After the stack creating you will be able to play with the CloudFormation example in the CodeCommit repository.
![create5](/images/create_stack5.png)

Now let's see how was the first IaC pipeline execution with the CloudFormation exampla that you will have in the CodeCommit:
![create6](/images/create_stack6.png)

The first release that automatically kicked-off failed and you can click in <b>"Details"</b> on the Test stage and after click in the <b>"Link to Execution"</b> to see more details.

![create7](/images/create_stack7.png)

![create8](/images/create_stack8.png)

You will see more information about the Build stage of the Template Scanner. Now you will need to click in <b>Build details</b> tab and after scroll down to <b>Artifacts</b> and click in the <b>artifact link</b> that was uploaded to the S3 bucket. 

![create9](/images/create_stack9.png)

![create10](/images/create_stack10.png)

You can download the latest file there to see the results, just clicking in (Actions -> Downlaod). You will need to unzip the file and you will see the following information as a JSON format:


{{% notice note %}}
<p style='text-align: left;'>
If the file downloaded doesn't have the zip extension, please add .zip to the file and unzip it.
</p>
{{% /notice %}}

        INFO: Obtaining required environment variables...
        INFO: All environment variables were received. The pipeline will fail if any "HIGH" level issues are found
        INFO: Offending entries:
        [
            {
                "attributes": {
                    "categories": [
                        "security"
                    ],
                    "cost": 0,
                    "descriptorType": "s3-bucket",
                    "ignored": false,
                    "last-updated-date": null,
                    "message": "Bucket S3Bucket doesn't have encryption enabled",
                    "not-scored": false,
                    "pretty-risk-level": "High",
                    "provider": "aws",
                    "region": "us-east-1",
                    "resource": "S3Bucket",
                    "risk-level": "HIGH",
                    "rule-title": "S3 Bucket Default Encryption",
                    "status": "FAILURE",
                    "tags": [
                        "Environment::ModernizationWorkshop"
                    ],
                    "waste": 0
                },
                "id": "ccc:AccountId:S3-021:S3:us-east-1:S3Bucket",
                "relationships": {
                    "account": {
                        "data": {
                            "id": "AccountId",
                            "type": "accounts"
                        }
                    },
                    "rule": {
                        "data": {
                            "id": "S3-021",
                            "type": "rules"
                        }
                    }
                },
                "type": "checks"
            },
            {
                "attributes": {
                    "categories": [
                        "security"
                    ],
                    "cost": 0,
                    "descriptorType": "s3-bucket",
                    "extradata": [],
                    "ignored": false,
                    "last-updated-date": null,
                    "message": "s3-bucket S3Bucket does not have S3 Block Public Access feature enabled.",
                    "not-scored": false,
                    "pretty-risk-level": "Very High",
                    "provider": "aws",
                    "region": "global",
                    "resource": "S3Bucket",
                    "risk-level": "VERY_HIGH",
                    "rule-title": "Enable S3 Block Public Access for S3 Buckets",
                    "status": "FAILURE",
                    "tags": [
                        "Environment::ModernizationWorkshop"
                    ],
                    "waste": 0
                },
                "id": "ccc:AccountId:S3-026:S3:global:S3Bucket",
                "relationships": {
                    "account": {
                        "data": {
                            "id": "AccountId",
                            "type": "accounts"
                        }
                    },
                    "rule": {
                        "data": {
                            "id": "S3-026",
                            "type": "rules"
                        }
                    }
                },
                "type": "checks"
            }
        ]
        CRITICAL: 2 offending entries found

You can see that you have <b>two misconfiguration</b> that is not meeting the minimum risk level that we defined in our IaC pipeline as <b>HIGH</b> during the IaC pipeline creation. 
You could change the risk level configuration anytime that you need. 
For this case we are going to do the fix direct in the CodeCommit where is our CloudFormation template, but in the real life you will be able to share the details above with your Cloud Architect team and DevOps Engineers to improve the CloudFormation and then push it to the Code repository. 

Let's do the fixes in the CloudFormation then. :computer:
Search for CodeCommit and then click in the <b>CloudFormationRepo</b> that was created by the CloudFormation template early on this lab.
Click in the cloudformation.yml and after click in edit, you will see the following cloudformation template for us to fixed:


![create11](/images/create_stack11.png)

You will need to added the following lined to fix the two HIGH issues found by the Conformity Template Scanner. These code below neeed to be added after line 29:

      BucketEncryption: 
        ServerSideEncryptionConfiguration: 
        - ServerSideEncryptionByDefault:
            SSEAlgorithm: AES256
      PublicAccessBlockConfiguration:
        BlockPublicAcls: true
        BlockPublicPolicy: true
        IgnorePublicAcls: true
        RestrictPublicBuckets: true

{{% notice warning %}}
<p style='text-align: left;'>
Recommendation: Change the S3 bucket name to an unique name, because it's a global resource and can't have duplicated name across the globe.
</p>
{{% /notice %}}


{{% notice note %}}
<p style='text-align: left;'>
The Image ID used is from us-east-1 in AWS. If you are usign a different region to deploy the CloudFormation Template, please use the properly Image ID from the region that you are using. 
</p>
{{% /notice %}}

After adding the lines above your CloudFormation shoudl like it here:

        Resources:
        Ec2Instance:
            Type: 'AWS::EC2::Instance'
            Properties:
            SecurityGroups: 
            - Ref: InstanceSecurityGroup
            ImageId: ami-0742b4e673072066f
            Tags:
                - 
                Key: "Environment"
                Value: "ModernizationWorkshop"
        InstanceSecurityGroup:
            Type: 'AWS::EC2::SecurityGroup'
            Properties:
            GroupDescription: Enable SSH access via port 22 test 
            SecurityGroupIngress:
                - IpProtocol: tcp
                FromPort: 22
                ToPort: 22
                CidrIp: 0.0.0.0/0
            Tags:
                - 
                Key: "Environment"
                Value: "ModernizationWorkshop"
        S3Bucket:
            Type: AWS::S3::Bucket
            Properties:
            BucketName: test-modernizationworkshop
            BucketEncryption: 
                ServerSideEncryptionConfiguration: 
                - ServerSideEncryptionByDefault:
                    SSEAlgorithm: AES256
            PublicAccessBlockConfiguration:
                BlockPublicAcls: true
                BlockPublicPolicy: true
                IgnorePublicAcls: true
                RestrictPublicBuckets: true
            Tags:
                - 
                Key: "Environment"
                Value: "ModernizationWorkshop"


Now you will just need to add the information requested for the Commit and Click in "Commit Changes", this way the pipeline will kick-off automatically because the changes happening:


![create12](/images/create_stack12.png)

Go to Pipelines on the left under CodePipeline and click in the ModernizationWorshop pipeline to see the stages:

![create13](/images/create_stack13.png)

Now you will see that the CloudFormation template passed in the Template Scanner analysis and it was able to be build in the AWS :rocket: 
Now you have a simple fully automated IaC with security scanning for your Cloud Formation Templates before build the infrastructure.

![create14](/images/create_stack14.png)

---------------------


{{% notice note %}}
<p style='text-align: left;'>
The CloudFormation template will be creating a S3 bucket, a security group and an EC2.
You could go to the CloudFormation Stack and delete the stack that we just created called: <b>"modernization-workshop-cft-example"</b>
</p>
{{% /notice %}}


Now you can skip to the <b>lab 5. Integrating AWS with Cloud One - Conformity </b> :computer: :rocket:
