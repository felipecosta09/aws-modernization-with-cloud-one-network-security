---
title: "Need for Server Security"
chapter: false
weight: 7.2
---

### WHY SERVER AND CLOUD WORKLOAD SECURITY IS DIFFERENT
Threats target servers and cloud workloads differently than endpoints (desktops, laptops, etc),
and therefore require a different blend of detection and prevention techniques. In the past few
years, attacks and ransomware leveraging vulnerabilities, like Apache Struts 2 and Heartbleed,
have specifically targeted workloads, containers, and container platforms. While endpoint
products can run on a server operating system, they don’t address the way servers, cloud
workloads, and containers are deployed or attacked.


--- 
<h3><span style="color:red">Here are the main reasons servers/workloads require security that’s built for them:</span></h3>

#### Virtual Patching and Lateral Movement Detection
Virtual patching (using host-based intrusion detection systems/intrusion prevention systems
(IDS/IPS)) and lateral movement detection are critical for detecting and blocking operating
system and application vulnerabilities. Customers need protection as soon as the
vendor patch is available, and sometimes, even days before the vendor patch is released.

---

#### Server Workloads Moving to Containers
Containers are often very short lived at runtime, so it’s essential to protect them by “shifting left”,
and providing security in the DevOps software pipeline. In addition, each workload needs protection to secure the container
application, container platform, container network and traffic, as well as the host operating
system.


---

#### Workload Discovery and Auto Scaling
Workloads are vulnerable from the moment they are instantiated. Customers need to ensure that
security gets configured and deployed automatically when new workloads are instantiated, even
as a part of the build process or through your favorite deployment tools.




Let's check out the components and protection capabilities with **Cloud One - Workload Security** :cloud: :laptop: :rocket: