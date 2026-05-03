SSH Brute Force Attack



Objective



Simulate a brute force attack against SSH service.







Tool Used



\* Hydra







Command





hydra -l root -P rockyou.txt ssh://<ubuntu-ip>









Expected Behavior



\* Multiple login attempts

\* Repeated failures







Log Evidence



Check logs:





grep "Failed password" /var/log/auth.log









Observation



\* High volume of failed login attempts

\* Indicates brute force activity







