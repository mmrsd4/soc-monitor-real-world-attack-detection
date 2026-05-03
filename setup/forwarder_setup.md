Splunk Universal Forwarder Setup



Objective



Forward logs from Ubuntu target to Splunk SIEM.







Step 1: Install Forwarder



Download correct version for your architecture.



Extract and navigate:





cd splunkforwarder/bin









Step 2: Connect to Splunk





./splunk add forward-server <splunk-ip>:9997









Step 3: Add Log Monitoring





./splunk add monitor /var/log/auth.log

./splunk add monitor /var/log/apache2/access.log

./splunk add monitor /var/log/apache2/error.log







Step 4: Restart Forwarder





./splunk restart





Result



\* Logs are forwarded to Splunk

\* Continuous monitoring enabled







