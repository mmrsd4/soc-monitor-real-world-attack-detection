SQL Injection Detection



Objective



Detect SQL injection attempts using log patterns.







Query





index=\* 

| regex \_raw="(?i)(\\bor\\b\\s+1=1|--|#)"









Explanation



\* Matches common SQL injection patterns

\* Case-insensitive detection



Limitations



\* May detect benign inputs

\* Requires tuning







