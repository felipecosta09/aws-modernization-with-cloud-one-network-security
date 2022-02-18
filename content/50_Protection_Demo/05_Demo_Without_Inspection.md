---
title: "Test without Inspection"
chapter: false
weight: 51
pre: "<b>6.1 </b>"
---
 
---

#### 1. Sign in to the [Cloud One](https://cloudone.trendmicro.com/home)
- Select the **Network Security** tile
- Expand **Network** 
- Click on **Appliances**
- Click on the **Group/Appliance Name**

![ns_policy1](/images/ns_aplliances.png)
![ns_policy1](/images/ns_distro_policy.png)

---

#### 2. On the Appliance page, DISABLE the Inspection of the Appliance. 
- Toggle **Inspection State** to **disable** inspection. 

{{% notice note %}}
<p style='text-align: left;'>
With the appliance now in "fallback mode" we will <b>not</b> be able to inspect the traffic, but will be our first steps to demo without protection
</p>
{{% /notice %}}

![ns_policy1](/images/ns_fallback.png)

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

#### 5. Now that you have successfully logged in, Create/Reset Database. 
- Click button: **Create/Reset Database**

{{% notice note %}}
<p style='text-align: left;'>
After Create/Reset you will be logged out of the DVWA. Please login again using same credentials from Step 4.
</p>
{{% /notice %}}

![ns_policy1](/images/dvwa_db_set.png)

---

#### 6. DVWA SQL Injection 
- Select: **SQL Injection**
- User ID: 
    
        admin ' OR 1=1--'

![ns_policy1](/images/sql_1.png)
![ns_policy1](/images/sql_2.png)

---

#### 7. DVWA Command Injection 
- Select: **Command Injection**
- User ID: <code>127.0.0.1; cat /etc/passwd</code>

![ns_policy1](/images/rce_1.png)
![ns_policy1](/images/rce_2.png)

---

#### 8. SSH to bastion machine 
- In the AWS Console navigate to **EC2**
- Select EC2 instance: **BastionLinux**
- Click **Connect**
- Select tab: **SSH client**
- Use the SSH Client to connect to the BastionLinux machine. 

![ns_policy1](/images/ec2_bastion.png)
![ns_policy1](/images/ssh_client.png)
![ns_policy1](/images/ssh_shell.png)

---

##### 8.1 Wget Retrieval Attempt - Download Files 
- In the **SSH shell/terminal**
- Run Command: <code>wget http://files.trendmicro.com/products/eicar-file/eicar.com</code>

![ns_policy1](/images/wget.png)


-----
#### Congrats you have attacked this web app. Unfortunately all the attacks were successful. Let us fix that!! :rocket: :cloud:
