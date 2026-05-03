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



<img src="architecture/lab_diagram.png" width="600"/>



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



<img src="screenshots/01_network_connectivity.png" width="700"/>







##### Services Running



SSH and Apache services are started on the target server.



<img src="screenshots/02_services_running.png" width="700"/>





##### Juice Shop Application



OWASP Juice Shop deployed and accessible via browser.



<img src="screenshots/03_juice_shop_running.png" width="700"/>







##### Log Monitoring



System and web logs are actively monitored.



<img src="screenshots/04_log_sources-1.png" width="700"/>
<img src="screenshots/04_log_sources-2.png" width="700"/>






##### Splunk Forwarder Setup



Logs configured for forwarding to Splunk SIEM.



<img src="screenshots/05_forwarder_status.png" width="700"/>

<img src="screenshots/06_splunk_port.png" width="700"/>



#### **Data Ingestion**



Logs successfully indexed in Splunk.


<img src="screenshots/07_data_ingestion.png" width="700"/>




##### Attack Simulation





###### Brute Force Attack (SSH)



Hydra used to perform brute force attack on SSH service.



<img src="screenshots/08_hydra_attack.png" width="700"/>





###### Failed Login Evidence



Multiple failed login attempts recorded in system logs.



<img src="screenshots/09_failed_logins.png" width="700"/>





#### Detection Engineering





###### Brute Force Detection





index=\* "Failed password"

| bin \_time span=1m

| stats count by src\_ip, \_time

| where count > 10





<img src="screenshots/10_bruteforce_query.png" width="700"/>







#### Alert Triggered



Splunk alert generated for brute force activity.



<img src="screenshots/11_alert_triggered.png" width="700"/>



##### 

##### SQL Injection Attack



SQL injection executed using Burp Suite.



<img src="screenshots/12_sql_injection_burp.png" width="700"/>







##### Web Log Evidence



Malicious requests captured in Apache logs.



<img src="screenshots/13_sql_logs.png" width="700"/>



##### 

##### SQL Injection Detection





index=\* 

| regex \_raw="(?i)(\\bor\\b\\s+1=1|--|#)"





<img src="screenshots/14_sql_detection.png" width="700"/>





##### Dashboard



Centralized visualization of attack activity and alerts.



<img src="screenshots/15_dashboard.png" width="700"/>







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









