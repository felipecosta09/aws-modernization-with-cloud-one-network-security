---
title: "Protection Capabilites"
chapter: true
weight: 10
pre: "<b>2.1 </b>"
---

## About the Workload Security protection modules

Trend Micro Workload Security has tightly integrated modules that easily expand your security capabilities.

![modules](/images/modules.png)

### Intrusion Prevention
The Intrusion Prevention module inspects incoming and outgoing traffic to detect and block suspicious activity. This prevents exploitation of known and zero-day vulnerabilities. Workload Security supports "virtual patching": you can use Intrusion Prevention rules to shield from known vulnerabilities until they can be patched, which is required by many compliance regulations. You can configure Workload Security to automatically receive new rules that shield newly discovered vulnerabilities within hours of their discovery.

The Intrusion Prevention module also protects your web applications and the data that they process from SQL injection attacks, cross-site scripting attacks, and other web application vulnerabilities until code fixes can be completed.

---

### Anti-Malware

The Anti-Malware module protects your Windows and Linux workloads against malicious software, such as malware, spyware, and Trojans. Powered by the Trend Micro™ Smart Protection Network™, the Anti-Malware module helps you instantly identify and remove malware and block domains known to be command and control servers.

---

### Firewall

The Firewall module is for controlling incoming and outgoing traffic and it also maintains firewall event logs for audits.

---

### Web Reputation

The majority of today’s attacks start with a visit to a URL that’s carrying a malicious payload. The Web Reputation module provides content filtering by blocking access to malicious domains and known communication and control (C&C) servers used by criminals. The Web Reputation module taps into the Trend Micro Smart Protection Network, which identifies new threats quickly and accurately.

---

### Integrity Monitoring

The Integrity Monitoring module provides the ability to track both authorized and unauthorized changes made to an instance and enables you to receive alerts about unplanned or malicious changes. The ability to detect unauthorized changes is a critical component in your cloud security strategy because it provides visibility into changes that could indicate the compromise of an instance.

---

### Log Inspection

The Log Inspection module captures and analyzes system logs to provide audit evidence for PCI DSS or internal requirements that your organization may have. It helps you to identify important security events that may be buried in multiple log entries. You can configure Log Inspection to forward suspicious events to an SIEM system or centralized logging server for correlation, reporting, and archiving.

---

### Application Control

The Application Control module monitors changes - "drift" or "delta" - compared to the computer’s original software. Once application control is enabled, all software changes are logged and events are created when it detects new or changed software on the file system. When Deep Security Agent detects changes, you can allow or block the software, and optionally lock down the computer.

---

### Activity Monitoring

Activity Monitoring is a security policy that takes your detection and response support to the next level, providing complete visibility of your workloads. When Activity Monitoring is enabled, the following activity information is forwarded to the Trend Micro Vision One (XDR) platform:

- Process Activity
- File Activity
- Network Activity
- Connection Activity
- Domain Query Activity
- Registry Activity(Windows)
- User Account Activity(Windows)

---