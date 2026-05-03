Splunk Enterprise Setup



Objective



Install and configure Splunk SIEM for log ingestion and analysis.







Step 1: Install Splunk Enterprise



Download from official site and install.



Start Splunk:





./splunk start









Step 2: Access Web Interface



Open browser:





http://<splunk-ip>:8000





Login with admin credentials.







Step 3: Enable Receiving Port



1\. Go to \*\*Settings\*\*

2\. Click \*\*Forwarding and Receiving\*\*

3\. Under \*\*Receiving\*\*, click \*\*Add New\*\*

4\. Enter:





9997





5\. Click Save







Step 4: Verify Splunk is Ready



Go to:



\* Search \& Reporting



Run:





index=\*









Result



\* Splunk is running

\* Port 9997 enabled

\* Ready to receive logs







