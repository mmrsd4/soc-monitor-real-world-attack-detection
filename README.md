### **SOC MONITOR REAL WORLD ATTACK DETECTION** 



#### Overview



This project simulates a real-world Security Operations Center (SOC) workflow by executing cyber attacks, collecting logs, forwarding them to a SIEM, and detecting malicious activity using Splunk.



The focus is on detection engineering and analysis, not just attack execution.







#### Objectives



Simulate SSH brute force and SQL injection attacks

Collect logs from system and web services

Forward logs to Splunk SIEM

Detect attacks using custom queries

Trigger alerts for suspicious activity

Visualize threats using dashboards



#### 

Tools \& Technologies

---

Kali Linux (Attack Simulation)

Hydra (Brute-force tool)

Burp Suite (Web attack testing)

Ubuntu Server (Target system)

Docker (Juice Shop deployment)

Splunk Enterprise (SIEM)

Splunk Universal Forwarder (Log forwarding)





#### Lab Architecture



add image



SOC Lab Architecture showing attack flow, log forwarding, and SIEM detection







#### Environment Setup



Component  Description                             

Attacker   Kali Linux (Hydra, Burp Suite)           

Target     Ubuntu Server (SSH, Apache2, Juice Shop) 

SIEM       Splunk Enterprise                        

Logs       auth.log, access.log, error.log          







#### **Implementation Steps**







##### Network Connectivity



Verifying connectivity between attacker and target system.



<p align="center">

&#x20; <img src="screenshots/01\_network\_connectivity.png" width="700"/>

</p>







##### Services Running



SSH and Apache services are started on the target server.



<p align="center">

&#x20; <img src="screenshots/02\_services\_running.png" width="700"/>

</p>





##### Juice Shop Application



OWASP Juice Shop deployed and accessible via browser.



<p align="center">

&#x20; <img src="screenshots/03\_juice\_shop\_running.png" width="700"/>

</p>







##### Log Monitoring



System and web logs are actively monitored.



<p align="center">

&#x20; <img src="screenshots/04\_log\_sources.png" width="700"/>

</p>







##### Splunk Forwarder Setup



Logs configured for forwarding to Splunk SIEM.



<p align="center">

&#x20; <img src="screenshots/05\_forwarder\_status.png" width="700"/>

</p>





#### **Data Ingestion**



Logs successfully indexed in Splunk.



<p align="center">

&#x20; <img src="screenshots/07\_data\_ingestion.png" width="700"/>

</p>




##### Attack Simulation





###### Brute Force Attack (SSH)



Hydra used to perform brute force attack on SSH service.



<p align="center">

&#x20; <img src="screenshots/08\_hydra\_attack.png" width="700"/>

</p>





###### Failed Login Evidence



Multiple failed login attempts recorded in system logs.



<p align="center">

&#x20; <img src="screenshots/09\_failed\_logins.png" width="700"/>

</p>





#### Detection Engineering





###### Brute Force Detection





index=\* "Failed password"

| bin \_time span=1m

| stats count by src\_ip, \_time

| where count > 10





<p align="center">

&#x20; <img src="screenshots/10\_bruteforce\_query.png" width="700"/>

</p>







#### Alert Triggered



Splunk alert generated for brute force activity.



<p align="center">

&#x20; <img src="screenshots/11\_alert\_triggered.png" width="700"/>

</p>



##### 

##### SQL Injection Attack



SQL injection executed using Burp Suite.



<p align="center">

&#x20; <img src="screenshots/12\_sql\_injection\_burp.png" width="700"/>

</p>







##### Web Log Evidence



Malicious requests captured in Apache logs.



<p align="center">

&#x20; <img src="screenshots/13\_sql\_logs.png" width="700"/>

</p>



##### 

##### SQL Injection Detection





index=\* 

| regex \_raw="(?i)(\\bor\\b\\s+1=1|--|#)"





<p align="center">

&#x20; <img src="screenshots/14\_sql\_detection.png" width="700"/>

</p>





##### Dashboard



Centralized visualization of attack activity and alerts.



<p align="center">

&#x20; <img src="screenshots/15\_dashboard.png" width="750"/>

</p>







##### Alerting



Alerts configured in Splunk with:



&#x20;Trigger Condition: Number of results > 0

&#x20;Trigger Mode: Per Result





##### Limitations



Static thresholds may generate false positives

No threat intelligence enrichment

Limited log sources

No automated response









##### Key Learnings



Detection is more important than attack execution

Logs must be analyzed, not just collected

SIEM effectiveness depends on detection logic

Real SOC work involves investigation and correlation





##### Conclusion



This project demonstrates a complete SOC workflow:



Attack → Log Generation → Forwarding → Detection → Alerting → Visualization



It highlights how security analysts detect and respond to real-world threats using SIEM tools.









