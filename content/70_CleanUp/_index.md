---
title: "Cleanup"
chapter: false
weight: 140
pre: "<b>8. </b>"
---

### Cleanup your Environment

Now that you have successfully completed this lab, to avoid charges please follow the documentation steps to remove resources deployed during this workshop.

#### 1. Sign into your AWS Console.
- Navigate to **CloudFormation**

![cleanup](/images/stacks_cleanup.png)

---

#### 2. Select CloudWatch panel Stack: **Demo-Cloud-One-Network-Security-Panel**
- Click on **Delete** button

![cleanup](/images/cw_stack_delete.png)

---

#### 3. Select Network Security Appliance Stack: **Modernization-Workshop-Network-Security-Appliance**
- Click on **Delete** button
- This stack will take a few minutes to delete

![cleanup](/images/ns_stack_delete.png)

---

##### 3.1 In a new tab navigate to **AWS VPC**
- From left-hand menu select **Route Tables**
- Select Route Table: **Protected Public Routes- C1NS-labenvironment**
- Actions: **Delete Route Table**
- Type **delete**
- Click **Delete**

![cleanup](/images/route_tables.png)
![cleanup](/images/route_tables_delete.png)

---

#### 4. Back in CloudFormation stacks tab. 
- Select VPC Stack: example **aws-netsec-workshop**
- Click on **Delete** button
- This stack will take a few minutes to delete

![cleanup](/images/vpc_stack_delete.png)

------

### Thank you for joining our workshop! We hope you enjoyed this and learned new things! :clap: :clap: