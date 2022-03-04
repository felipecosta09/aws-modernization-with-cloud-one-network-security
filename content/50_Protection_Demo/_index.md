---
title: "Configure and Protect"
chapter: true
weight: 50
pre: "<b>6. </b>"
---

### Configuring the Policy for Cloud One Network Security 

---

#### 1. Sign in to the [Cloud One](https://cloudone.trendmicro.com/home)
- Select the **Network Security** tile
- Expand **Policy** 
- Click on **Intrusion Prevention Filtering**

![ns_policy1](/images/ns_ips.png)

---

#### Here you will see all the available filters. As you can see we have more than 22k filters that can be applied.
- You can use the **Search filters by properties** text box to search for specific filters.

![ns_policy1](/images/ns_ips_filters.png)

---

#### 2. Apply the following IPS filters.

##### 2.1 Search for the filter: <code>5673</code> 
5673: HTTP: SQL Injection (Boolean Identity)

- **Check the rule box** to assign
- Click the **Settings Wheel** to configure rule
- **Use customized actions**
- Filter State: **Enabled**
- Flow Control: **Permit**
- Log Event: **Enabled**
- **Save**

![ns_ips](/images/5673.png)

---

##### 2.2 Search for the filter: <code>3798</code>
3798: HTTP: SQL Injection (Boolean Identity)

- **Check the rule box** to assign
- Click the **Settings Wheel** to configure rule
- **Use customized actions**
- Filter State: **Enabled**
- Flow Control: **Permit**
- Log Event: **Enabled**
- **Save**

![ns_ips](/images/3798.png)

---

##### 2.3 Search for the filter: <code>0361</code>
0361: HTTP: Protected File Access (/etc/passwd)

- **Check the rule box** to assign
- Click the **Settings Wheel** to configure rule
- **Use customized actions**
- Filter State: **Enabled**
- Flow Control: **Block**
- Log Event: **Enabled**
- **Save**

![ns_ips](/images/0361.png)

---

##### 2.4 Search for the filter: <code>6763</code>
6763: HTTP: Wget Web Page Retrieval Attempt

- **Check the rule box** to assign
- Click the **Settings Wheel** to configure rule
- **Use customized actions**
- Filter State: **Enabled**
- Flow Control: **Block**
- Log Event: **Enabled**
- **Save**

![ns_ips](/images/6763.png)

---

#### 3. Deploying the Policy.
- In the Network Security Console select **Appliances**
- Click on the **Group/Appliance Name**

![ns_policy1](/images/ns_aplliances.png)
![ns_policy1](/images/ns_distro_policy.png)

---

#### 4. On the Appliance page, click in **Distribute Policy** and wait until it distribution has finished.

![ns_policy1](/images/distro_policy_start.png)

---

##### 4.1 Once it finish it will look like the image below.


![ns_policy1](/images/distro_policy_finish.png)

--------

### Congrats you have assigned filters and distributed the policy to your Network Security Appliance :star-struck: :robot: :white_check_mark: :cloud: