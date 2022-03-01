---
title: "Introduction"
chapter: true
weight: 5
pre: "<b>1. </b>"
---

## SECURE THE CLOUD WITHOUT GIVING UP THE BENEFITS
As more and more enterprises adopt multi- or hybrid-cloud strategies, cloud architects and network security teams are looking for simpler ways to protect business-critical assets across their many different cloud environments. They’re finding that what worked on-premise for security doesn’t necessarily translate to the cloud.

---

### A challenge to deploy

Many existing network security solutions are painful to deploy because they’re not designed for the cloud. Some require extensive downtime to be inserted inline, some have outdated throughput-based licensing models, and others may be impossible to deploy within an enterprise’s existing
cloud infrastructure. For example, agent/host-based solutions aren’t always feasible or desirable in the cloud. Enterprises may not have the right
to deploy an agent on their cloud provider’s virtual server—or may not want to dedicate compute to an agent at the expense of other workloads.
There’s also the problem of complexity. An overwhelming number of appliances, load balancers, and other “moving parts” have to be installed and
managed to inspect inbound and outbound traffic. If every Virtual Private Cloud (VPC) needs its own firewall—and if an enterprise has hundreds of
VPCs—the management burden and costs quickly add up.

Changes often have to be made to the network infrastructure itself to accommodate those additional components, with some security solutions
requiring IP addresses to be changed or specific topologies to be deployed. New devices inserted in the network can also become “critical” going
forward, meaning they can’t be easily (or cheaply) removed or modified. As more pieces get added, they bring inefficiencies that can disrupt or
slow down network traffic, affecting core business operations and processes.

There are cloud-native security solutions, of course, but these are often tied to specific platforms, such as Amazon Web Services (AWS). Having a different security solution for every cloud provider prevents enterprises from getting a centralized view of the threats they face.
It also increases the risks of management dashboard/console overload, increasing the odds that important security alerts will be missed. These platform-specific cloud solutions may not address all security use cases, such as virtual patching at the network layer, egress filtering, and deep packet inspection.

![Introduction](/images/intro.png)

---

## Network Policies to Help Reduce Risk and Improve Security

>*Cloud workloads frequently require internet access, and as we know, anything accessing the internet can be breached. This article explores simple tactics such as access-level restriction and overlaying threat intelligence to enhance your security posture.*


Most cloud practitioners start their network control journey looking at security groups, firewalls, or web application firewalls (WAF) to protect their public applications from inbound attacks. But what about workloads that aren’t public facing but still have internet access?

For example, this Amazon Elastic Compute Cloud (EC2) Linux workload can be infiltrated by Kinsingpunk Malware to steal Amazon Web Services (AWS) credentials, Secure Shell (SSH) keys, the bash history file, and many other types of sensitive information and credentials. Collected data is then sent to the remote command and control server **sayhi.bplaced[.]net**.

Considering Kinsingpunk uses techniques to rapidly change the domains pointing to the command and control server, security teams may find themselves trying to chase down malicious domains one at a time. This is difficult, if not impossible, to react to. In this attack, restricting internet traffic to only known, good domains would have prevented data exfiltration to **sayhi.bplaced[.]net**.

Situations like this are, in part, why frameworks like PCI DSS (Section 1.2.1) make this proactive and powerful security control a requirement.

With cloud providers introducing new networking technologies, it’s important to use a transparent, threat-focused security solution like Trend Micro Cloud One™ – Network Security. This solution can be implemented next to the internet gateway to achieve these goals. With a multi-cloud approach, these benefits can be made available to any compute service in your VPC or VNet communicating via an internet gateway.

> <h4>Now… overlay threat context to supercharge your automation and response:</h4>

Ok, so now that unsanctioned internet communications are prevented, what’s next to maximize security and minimize risk?

Looking at what threats were blocked can determine the appropriate response. Overlaying threat intelligence provides powerful context to differentiate between an application issue or a security issue.

For instance, a workload reaching out to **example.com** may simply indicate the need for a policy change or be from incomplete code that inadvertently made it to production. While this needs to be addressed, it likely doesn’t warrant immediate concern. Therefore, responding with automation to create an issue or to inform the app owner of this violation may be all that is needed.

What about a blocked attempt to reach out to known command and control (C&C)? Or a communications attempt to an anonymous proxy or suspicious geo-region? Or a network inspection that blocks a known malware check-in? This response may be significantly different—like automation that terminates or quarantines the affected code, notifying your security operations center (SOC), and possibly initiating incident response activities.

This security context provided from solutions like Network Security allow for a better response. Now, you can rest easy knowing that even approved internet-bound traffic to the specified known, good domains will be further analyzed for signs of malicious activity, exfiltration attempts, and other compromises.

--- 

<h4>On Architecture:</h4>

Implementing Network Security at your application’s internet gateway is a great way for DevOps teams to add protection. For cloud architects, patterns that share security and network infrastructure can scale this compliance and security control. This can then provide a security best practice guardrail that can be rapidly used across your organization by many teams.

Common patterns include, sharing a centrally managed network control using AWS technologies like Gateway Load Balancer (GWLB) or architecting a hub-and-spoke network topology with a shared internet egress point—providing a great location to deploy a control for multiple teams.

![Introduction](/images/intro_2.png)
