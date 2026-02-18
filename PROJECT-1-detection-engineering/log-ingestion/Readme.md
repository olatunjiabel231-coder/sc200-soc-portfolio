In this step,

I confirmed that Microsoft Entra ID sign-in logs were successfully flowing into Microsoft Sentinel. The data source used was Microsoft Entra ID (Azure Active Directory) Sign-in Logs.

To verify that log ingestion was working, I ran a simple KQL query:

"SigninLogs | take 5"


This query showed recent sign-in records, which confirmed that authentication logs were being collected in the Log Analytics workspace.

This means my SOC environment is now receiving log data and is ready for detection and investigation.
