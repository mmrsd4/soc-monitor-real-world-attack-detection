Target System Setup (Ubuntu Server)



Objective



Prepare the target machine with vulnerable services and logging enabled for SOC monitoring.







Step 1: Update System





sudo apt update \&\& sudo apt upgrade -y









Step 2: Install and Enable SSH





sudo apt install openssh-server -y

sudo systemctl start ssh

sudo systemctl enable ssh

sudo systemctl status ssh





Verify SSH is running (Port 22).







Step 3: Install Apache Web Server





sudo apt install apache2 -y

sudo systemctl start apache2

sudo systemctl enable apache2

sudo systemctl status apache2





Verify Apache is running (Port 80).







Step 4: Install Docker





sudo apt install docker.io -y

sudo systemctl start docker

sudo systemctl enable docker









Step 5: Deploy OWASP Juice Shop





sudo docker run -d -p 3000:3000 bkimminich/juice-shop

```



Access application:





http://<ubuntu-ip>:3000





Step 6: Verify Log Sources



Check logs:





tail -f /var/log/auth.log

tail -f /var/log/apache2/access.log

tail -f /var/log/apache2/error.log









Result



\* SSH and Apache services are active

\* Juice Shop is running

\* Logs are being generated for monitoring



