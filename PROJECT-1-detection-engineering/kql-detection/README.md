## KQL Detection — Failed Login Activity

### Objective

The goal of this step was to create a detection query in Microsoft Sentinel to identify suspicious authentication activity, specifically repeated failed login attempts that may indicate brute-force behavior.

---

### Detection Logic

Failed login attempts can indicate password guessing or brute-force attacks. To detect this behavior, I created a KQL query that identifies multiple authentication failures from the same user and IP address.

---

### KQL Query
SigninLogs

| where ResultType != 0

| summarize FailedAttempts = count() by UserPrincipalName, IPAddress

| where FailedAttempts > 5

| sort by FailedAttempts desc


---

### Explanation

- `ResultType != 0` → Filters failed login attempts  
- `summarize count()` → Counts failed attempts per user and IP  
- `FailedAttempts > 5` → Flags suspicious behavior  
- `sort desc` → Shows most suspicious first  

---

### Result

The query successfully identified accounts with repeated failed login attempts. This confirmed that authentication activity can be monitored and suspicious behavior detected using KQL.

---

### Status

Completed — detection query created and validated.


