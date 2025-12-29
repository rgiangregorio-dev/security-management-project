---
Installing Proofpoint's ET (emerging threats) Pro edition. This provides OPNsense with the latest threat detection rules (I also downloaded os-intrusion-detection-content-et-open, I just didn't get a screenshot for it).
---
---

![138](./assets/image138.png)

---
Configuring Suricata (the network-based IDS).
---
---

![139](./assets/image139.png)

---
Enabling all of the rulesets (the Pro Telemetry ruleset, and the et-open ruleset).
---
---

![140](./assets/image140.png)

---
Showing that the telemetry token is valid.
---
---

![141](./assets/image141.png)

---
Adding a cronjob, so that rules will be automatically downloaded and updated.
---
---

![142](./assets/image142.png)
![143](./assets/image143.png)

---
Creating a central Wazuh (host-based IDS) server.
---
---

![144](./assets/image144.png)
![145](./assets/image145.png)
![146](./assets/image146.png)
![147](./assets/image147.png)
![148](./assets/image148.png)
![149](./assets/image149.png)
![150](./assets/image150.png)

---
These commands download Wazuh's cert tool and a sample configuration file.
---
---

![151](./assets/image151.png)

---
Setting the correct IP address for the indexer, server, and dashboard. The indexer stores and manages the data. The server analyzes the data and detects threats and performs incident response. THe dashboard is a way to view the security data.
---
---

![152](./assets/image152.png)

---
Generating certificates for Wazuh.
---
---

![153](./assets/image153.png)

---
Installing Wazuh's GPG key.
---
---

![155](./assets/image155.png)

---
Adding the repository.
---
---

![156](./assets/image156.png)

---
Installing the indexer package.
---
---

![158](./assets/image158.png)

---
Configuring the Wazuh indexer so that only connections from the Wazuh server will be able to reach the indexer.
---
---

![159](./assets/image159.png)

---
These commands essentially set up the node certificates in a secure folder so the Wazuh Indexer can safely communicate over the network using encrypted connections.
---
---

![160](./assets/image160.png)
![161](./assets/image161.png)
![162](./assets/image162.png)

---
Checking status of wazuh-indexer, after enabling and starting it.
---
---

![163](./assets/image163.png)

---
This script sets up the initial security configuration for the Wazuh Indexer cluster, like creating built-in users (like admin), setting up roles and permissions, and configuring authentication and encryption between nodes.
---
---

![164](./assets/image164.png)

---
Validating that the Wazuh indexer is running and accessible.
---
---

![165](./assets/image165.png)

---
Setting up the acutal Wazuh server and making sure it is running.
---
---

![167](./assets/image167.png)
![168](./assets/image168.png)

---
Installing filebeat, a log aggregation tool.
---
---

![169](./assets/image169.png)
![170](./assets/image170.png)

---
Editng the filebeat configuration file and setting the host value to the Wazuh server IP.
---
---

![171](./assets/image171.png)

---
Here, I am creating a filebeat keystore so that credentials can be stored securely. I am adding default credentials, but will change later.
---
---

![172](./assets/image172.png)

---
Installing the Wazuh module for filebeat.
---
---

![173](./assets/image173.png)

---
After I deployed certificates (similar to the Wazuh indexer), I enabled and started the service, and confirmed it is running and working as expected.
---
---

![174](./assets/image174.png)
![175](./assets/image175.png)

---
Installing the Wazuh dashboard.
---
---

![178](./assets/image178.png)

---
This makes the dashboard connect to the indexer running on the Wazuh server.
---
---

![179](./assets/image179.png)

---
Deploying the certificates for the dashboard, starting the service, and checking status of service.
---
---

![180](./assets/image180.png)
![181](./assets/image181.png)

---
Accessing the Wazuh dashboard via the "wks" VM.
---
---

![182](./assets/image182.png)

---
Deploying a new agent on "wks".
---
---

![183](./assets/image183.png)

---
This registers the agent as a service so that it starts at boot time on Windows.
---
---

![184](./assets/image184.png)

---
Repeating steps for dc1, dc2, srv, and core.
---
---

![185](./assets/image185.png)
![186](./assets/image186.png)
![187](./assets/image187.png)
![188](./assets/image188.png)

---
Setting up Wazuh on OPNsense.
---
---

![189](./assets/image189.png)

---
Downloading Sysmon, a Windows tool that collects system and security events.
---
---

![190](./assets/image190.png)

---
After adding some settings to ossec.conf in each VM with a Wazuh agent, I am copying these two .xml file rules to /var/ossec/etc/rules/local_rules.xml.
---
---

![191](./assets/image191.png)
![192](./assets/image192.png)

---
Restarting so the rules can take effect.
---
---

![193](./assets/image193.png)

---
This shows alerts related to dc1. I am adding two filters to show successful and unsuccessful authentication attempts.
---
---

![194](./assets/image194.png)
![195](./assets/image195.png)

---
This filter will help to analyze installed software.
---
---

![196](./assets/image196.png)

---
This is adding that filter to the Wazuh visualizer so I can use it in the future.
---
---

![197](./assets/image197.png)

---
Wazuh is performing an assessment of the "wks" OS; it is giving a list of things that passed and failed against a benchmark.
---
---

![198](./assets/image198.png)

---
The following has nothing to do with the previous part of this project; it is just documenting some testing with Kali Linux and several vulnerable VMs. Here, I am running nmap against the targets.
---
---

![211](./assets/image211.png)

---
Using gobuster to probe web interfaces on the VMs to see what directories and files it can find.
---
---

![212](./assets/image212.png)
![213](./assets/image213.png)
![214](./assets/image214.png)
![215](./assets/image215.png)

---
Using a tool called Nikto to check for vulnerabilities, misconfigurations, and outdated software on the VMs.
---
---

![216](./assets/image216.png)
![217](./assets/image217.png)

---
Using Nessus to scan for security weaknesses in these 7 VMs.
---
---

![218](./assets/image218.png)
![219](./assets/image219.png)
