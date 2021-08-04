---
title: "IDE Security Plugin"
chapter: false
weight: 40
pre: "<b>3. </b>"
---

### Install the Security plugin in the IDE 

First you will need to install the VSCode IDE in your machine to install the Cloud Conformity Security Plugin as you can see here: VSCode Marketplace— Cloud Conformity Security Plugin — [Link](https://marketplace.visualstudio.com/items?itemName=raphaelbottino.cc-template-scanner)

![IDE1](/images/IDE1.png)


### Enabling the API Token to scan CloudFormation Templates on the IDE

Second you will need to create one account in Cloud One — Conformity using this link here (Create Account), login into your account, and generate an API Token.

Log-In <b>Cloud One Platform</b>:

1. Click in Conformity service
2. Click in the username on the top right
3. Then click in User Settings
4. API Keys on the left
5. Finally click in "New API Key" to create an API Key to be used in the VSCode Plugin.

Remember to copy the key and save it safely. You won't be able to get it again.

![API](/images/API.png)

#### Copy the API Key and go back to VSCode IDE 💻

1. Click on the Extensions icon (left side) and click in Extension Settings ⚙️ for the Cloud Conformity Template Scanner entry.
2. Select Edit in settings.json on the Cc. ApiKey section.
3. Input the API Key you generated on the previous step and save.

![API2](/images/API2.png)

Now you will be able to scan the CloudFormation templates based on hundreds of checks that help you comply with the AWS Well-Architected Framework among others Standards & Frameworks to ensure you are building superior cloud infrastructure.
Here is one example of a <b>BAD</b> CloudFormation template <b>NOT</b> following theengineering best practices for you to test it:


```
#This is an CloudFormation template example NOT following the AWS Well-Architected Framework  

Resources:
  Ec2Instance:
    Type: 'AWS::EC2::Instance'
    Properties:
      SecurityGroups:
        - !Ref InstanceSecurityGroup
      KeyName: ec2-keypair
      ImageId: ami-0ff8a91507f77f867
      Tags:
        - 
          Key: "Environment"
          Value: "TM_Lab"
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
          Value: "TM_Lab"
  S3Bucket:
    Type: AWS::S3::Bucket
    Properties:
      BucketName: test-tm-lab-s3-bucket
      Tags:
        - 
          Key: "Environment"
          Value: "TM_Lab"
```

To test the extension, open the CloudFormation Template above with the VSCode IDE and open the Command Pallet with:

    - MAC OS: ⇧ + ⌘ + P
    - Windows/Linux: Ctrl+Shift+P

Search for Cloud One Conformity: Scan the Current Open Template and hit **Enter** it will automatically start scanning your CloudFormation template:

![IDE3](/images/IDE3.png)

**The result will appear in a second tab called Scan Result like the image below.**

You can also check out the [Cloud Knowledge Base](https://www.cloudconformity.com/knowledge-base/aws/), which can help you understand more about any best practice check violations and how to remediate/fix it in your CloudFormation template or in Production environments:

![IDE4](/images/IDE4.png)

Awesome the first stage for an IaC Security automation is done. 😃🤖💻
------