SQL Injection Attack



Objective



Simulate SQL injection attack on web application.







Tool Used



\* Burp Suite







Steps



1\. Open Burp Suite

2\. Enable Proxy → Intercept ON

3\. Open Juice Shop login page

4\. Enter payload:





' OR 1=1--





5\. Capture request

6\. Modify and forward







Log Evidence





tail -f /var/log/apache2/access.log









Observation



\* Suspicious request patterns detected

\* Indicates SQL injection attempt







