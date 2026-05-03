Brute Force Detection



Objective



Detect SSH brute force attacks using Splunk.







Query





index=\* "Failed password"

| bin \_time span=1m

| stats count by src\_ip, \_time

| where count > 10









🧠 Explanation



Groups events into 1-minute windows

Counts login failures per IP

Flags abnormal spikes







Limitations



\* Static threshold

\* May generate false positives







