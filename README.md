# Azure-ActivityLog-Logging-Monitoring

![Cloud Honeynet / Azure Activity Log Logging And Monitoring](https://i.imgur.com/vYEyapb.jpg)

## Introduction

In a previous project, Rayda Estate, a fictional company, deployed an Azure-based honeynet to attract hackers from the Internet. Log sources were collected in a Log Analytics workspace, allowing Microsoft Sentinel to generate attack maps, alerts, and incidents. Initial security metrics were measured for 24 hours in the insecure environment. Afterward, security controls were implemented to strengthen the environment, and metrics were measured for another 24 hours. One of the logs collected was Azure's Activity Log. Azure's Activity log records data plane operations, capturing crucial details like operation type, resource, time, caller, and status. These logs are stored in Azure Monitor, providing centralized access and management. Integration with monitoring tools enables customized dashboards, alerts, and compliance reports. I will configure Azure Monitor to send the Activity log to the logs Analytics workspace for analysis.

## Step-By-Step Configuration Of Azure Activity Log Logging

![Architecture Diagram](https://i.imgur.com/rXoG07d.jpg)

1. From the Azure home page, search for Monitor in the search bar

2. Click to open The Monitor from the drop-down menu

![Architecture Diagram](https://i.imgur.com/SBpcXUH.jpg)

3. From the Monitor page

4. Click Activity log and then

5. Click Export Activity Logs

![Architecture Diagram](https://i.imgur.com/yGowO5L.jpg)

6. From the Diagnostic setting page, select the appropriate Subscription. In this case, it is "RaydaEstateProject" 

7. Click Add diagnostic setting to configure the Diagnostic setting

8. Give the Diagnostic setting a name by entering a name. In this case, it is "DS-Monitor"

9. Select from the Logs categories which log you want to collect
  EX: Administrative, Security, Service Health, Alerts, Recommendation, etc

10. Select the destination for the selected logs. In this case, They are sent to the Log Analytics workspace

11. Select the appropriate Subscription. In this case "RaydaEstateProject"

12. Select the appropriate Logs Analytics workspace. In this case, "LogAnalyticsREP" which resides in the east US 2

13. Click Save to create the Diagnostic setting for Azure Active Log

![Architecture Diagram](https://i.imgur.com/p3Ykccq.jpg)

14. Shows a Diagnostic setting named DS-monitor
    
## Test To Ensure The Logs Have Been Ingested Into The Logs Analytics Workspace

![Architecture Diagram](https://i.imgur.com/DpfQEML.jpg)

1. From the Azure home page, search for Log Analytics workspace in the search bar

2. Click to open the Log Analytics workspace from the drop-down menu

![Architecture Diagram](https://i.imgur.com/2xPJVxg.jpg)

3. From the Log Analytics workspace page

4. Click Logs to access the query page 

5. Type AzureActivity ( AzureActivity is the table created by the Activity log sent to the Log Analytics workspace where logs reside)

6. Click Run to run the AzureActivity query 

7. The results of the query are populated in the Logs Analytics workspace 

![Architecture Diagram](https://i.imgur.com/su9h1Jc.jpg)

8. Click the down arrow of a log for a more in-depth analysis of the log. i.e.: You will see the caller, CallerIpAddress, EventSubmissionTimestamp [UTC], etc,...

## Conclusion
The configuration was successful, The Azure's Activity log is being ingested into the Log Analytics workspace. This configuration would allow the monitoring of Azure Subscription-level logs through the Log Analytics workspace and Microsoft Sentinel. 
