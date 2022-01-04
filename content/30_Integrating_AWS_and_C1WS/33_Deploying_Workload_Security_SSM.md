---
title: "Automate deployment with AWS SSM"
chapter: false
weight: 33
pre: "<b>4.3 </b>"
---

### Integrating Cloud One - Workload Security Agent with AWS Systems Manager Distributor

AWS Systems Manager Distributor is a feature integrated with AWS Systems Manager that you can use to securely store and distribute software packages in your accounts. By integrating Workload Security with AWS Systems Manager Distributor, you can distribute Deep Security Agents across multiple platforms, control access to managed instances, and automate your deployments.

---

#### 1. In the Cloud One Workload Security Console.
- Click **Support**
- Select **Deployment Scripts**

![ssm](/images/deployment_script1.png)

##### 1.1 Locate the 3 parameters described below:
Leave the default selections and scroll to the bottom of the bash script provided.

- Copy the **tenantID**
- Copy the **token**
- Copy the **activation URL**: <code>dsm://agents.workload.<b>Your C1 Region</b>.cloudone.trendmicro.com:443/</code>
![ssm](/images/deployment_script2.png)
![ssm](/images/deployment_script3.png)

---

#### 2. In the AWS console, navigate to **Systems Manager**.
- In the left-hand menu, under Application Management select **Parameter Store**
![ssm](/images/create_param.png)

##### 2.1 We need to create 4 parameters.

##### Parameter- 1

- Click **Create Parameter**
- Name: **dsActivationUrl**
- Value: **<code> Paste the Actvation URL copied from step 1.1 </code>**
- Click **Create Parameter**
![ssm](/images/create_param1.png)

---

##### Parameter- 2

- Click **Create Parameter**
- Name: **dsTenantId**
- Value: **<code> Paste the tenantID value copied from step 1.1 </code>**
- Click **Create Parameter**
![ssm](/images/create_param2.png)

---

##### Parameter- 3

- Click **Create Parameter**
- Name: **dsToken**
- Value: **<code> Paste the token value copied from step 1.1 </code>**
- Click **Create Parameter**
![ssm](/images/create_param3.png)

---

##### Parameter- 4

- Click **Create Parameter**
- Name: **dsManagerUrl**
- Value: **https://workload.REGION.cloudone.trendmicro.com:443** where **region** is your [Trend Micro Cloud One region ID](https://cloudone.trendmicro.com/docs/account-and-user-management/c1-regions/)
- Click **Create Parameter**
![ssm](/images/create_param4.png)

##### Your parameter store should have the following parmaters created now.
![ssm](/images/create_param5.png)

---

#### 3. In Systems Manager, on the left-hand menu, under Node Management select **Distributor**.
- Select **Thrid Party** tab
- Search: <code>TrendMicro-CloudOne-WorkloadSecurity</code>
- Select the Package
- Click on **Install on a Schedule**
![ssm](/images/ssm1.png)

---

#### 4. Create Association.

Provide association details

- Name: <code>workload-security-distributor-workshop</code>

Document

- Do not edit the document Section

Parameters

- Installation Type: **In-place update**

Target Selection

- Target Slection: **Specify instance tags**
- Tag Key: <code>Project</code>
- Tag Key: <code>Cloud One Demo Lab</code>
- Click **Add**

Specify Schedule

- Select **No Schedule**

Advanced Options

- Compliance Severity: **Medium**

Rate Control

- Concurrency: **5**
- Click on: **Create Association**

![ssm](/images/ssm2.png)
![ssm](/images/ssm3.png)
![ssm](/images/ssm4.png)

---

> **Et voila, we just automated the deployment of multiple Cloud One - Workload Security Agents in our AWS enviornment** 🤩 :cloud: 🤖 :rocket: