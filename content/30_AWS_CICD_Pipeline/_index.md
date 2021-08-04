---
title: "IaC Pipeline with Security"
chapter: false
weight: 50
pre: "<b>4. </b>"
---

### Create a CI/CD pipeline using AWS tools and integrate the Cloud One - Conformity Template Scanner into it

In the first stage, we show how you could scan CloudFormation Templates before committing a new version of the tempalte to the code repository, but sometimes the developers or DevOps engineer can forget to do it and commit the CloudFormation Templates with some issues. Now we will be able to create a security gate to help you prevent new resources from not following best practices recommended by your organization.

This can help you to monitor and audit any new change in real-time before you deploy in the AWS environment. 🤯

In this chapter, we will show how to use Template Scanner in the CI/CD pipeline with AWS CodeCommit, AWS CodeBuild, AWS CodePipeline. Let's do it :laptop:

Here is a little recap about the architecture that we are going to create:

![Diagram](/images/IaC_diagram.png)

----------------------------------------------------------------------------------------------------------------------

#### Infrastructure-as-Code - Pipeline with Security Creation

For this exercise we have a CloudFormation Template to build it for you:

- <b>Automated Creation</b>
    - Just go to <b>4.1 Automated Process to create IaC pipeline with Security </b> to start the automated process.