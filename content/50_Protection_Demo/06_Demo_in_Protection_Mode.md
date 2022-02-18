---
title: "Testing with Inspection"
chapter: false
weight: 52
pre: "<b>6.2 </b>"
---

### Let us enable inspection on the appliance.

---

#### 1. Sign in to the [Cloud One](https://cloudone.trendmicro.com/home)
- Select the **Network Security** tile
- Expand **Network** 
- Click on **Appliances**
- Click on the **Group/Appliance Name**

![ns_policy1](/images/ns_aplliances.png)
![ns_policy1](/images/ns_distro_policy_unhealthy.png)

---

#### 2. On the Appliance page, ENABLE the Inspection of the Appliance. 
- Toggle **Inspection State** to **enable** inspection. 

![ns_policy1](/images/ns_inspection.png)

---

#### 3. Navigate to the AWS Console
- Navigate to **EC2**
- Select EC2 instance **DVWA** 
- Copy the **Public IPv4 Address/DNS**

![ns_policy1](/images/dvwa_ip.png)


---

#### 4. Access the web application using the Public IP/DNS. 
- Remember that it will be over HTTP. 
- User: **admin**
- Password: **password**
- **Login**

![ns_policy1](/images/dvwa_login.png)

---

#### 5. DVWA SQL Injection
- Select: **SQL Injection**
- User ID:

        admin ' OR 1=1--'

![ns_policy1](/images/sql_1.png)
![ns_policy1](/images/sql_2.png)

---

#### 5.1 Remember we configured the SQL Injection filters to **Permit**, if you want to you can change it to Block. Let's check our CloudWatch dashboard for the SQL event.

{{% notice note %}}
<p style='text-align: left;'>
If you decide to change this intrusion prevention filter from permit to <b>BLOCK</b> you will need to redistribute the policy before it will take effect.
</p>
{{% /notice %}}

- In AWS Console navigate to **CloudWatch**
- From the left-hand menu select **Dashboards**
- Select: **Cloud_One_Network_Security_Panel**
- Check under **Cloud One Network Security - PERMIT Action**

![ns_policy1](/images/cw_permit_sql.png)


---

#### 6. DVWA Command Injection 
- Select: **Command Injection**
- User ID: <code>127.0.0.1; cat /etc/passwd</code>

![ns_policy1](/images/rce_1.png)

#### 6.1 Remember we configured the Command Injection filter to **Block**, so instead of the attack being permitted a timeout will occur. 

![ns_policy1](/images/timeout.png)

#### 6.2 Let's check our CloudWatch dashboard for the RCE event.
- In AWS Console navigate to **CloudWatch**
- From the left-hand menu select **Dashboards**
- Select: **Cloud_One_Network_Security_Panel**
- Check under **Cloud One Network Security - BLOCK Action**

![ns_policy1](/images/cw_block_rce.png)

---

#### 7. SSH to bastion machine 
- In the AWS Console navigate to **EC2**
- Select EC2 instance: **BastionLinux**
- Click **Connect**
- Select tab: **SSH client**
- Use the SSH Client to connect to the BastionLinux machine. 

![ns_policy1](/images/ec2_bastion.png)
![ns_policy1](/images/ssh_client.png)
![ns_policy1](/images/ssh_shell.png)

---

#### 7.1 Wget Retrieval Attempt - Download Files 
- In the **SSH shell/terminal**
- Run Command: <code>wget http://files.trendmicro.com/products/eicar-file/eicar.com</code>

#### 7.1 Remember we configured the intrusion prevention filter to **Block**, so instead of the file being permitted the Network Security Appliance drops the file attempt and another timeout will occur. 

![ns_policy1](/images/timeout_mfu.png)


#### 7.2 Let's check our CloudWatch dashboard for Wget Retrieval Attempt - Download File
- In AWS Console navigate to **CloudWatch**
- From the left-hand menu select **Dashboards**
- Select: **Cloud_One_Network_Security_Panel**
- Check under **Cloud One Network Security - BLOCK Action**

![ns_policy1](/images/cw_block_mfu.png)


-----
