{"title":"Leverage Custom Queries to gather insights from Crash Analytics Data","weight":"30"} 

# Leverage Custom Queries to gather insights from Crash Analytics Data

*   [Troubleshooting crashes reported by a user](#Troubleshootingcrashesreportedbyauser)
    
*   [Crash Events, Feature Events, and Breadcrumbs](#CrashEvents,FeatureEvents,andBreadcrumbs)
    

## Troubleshooting crashes reported by a user

App crashes happen. With the help of the custom queries interface found in AMPLIFY Crash Analytics (ACA), you can find the most recent crash experienced by that user and gather more information about the reported crash.

1.  In the **Dashboard**, you browse to the Application and look up **tabCrashIssue**.
    
    ![tabCrashIssue](/Images/appc/download/attachments/60143477/tabCrashIssue.png)
2.  Click on **Analytics** > **Custom Queries**.
    
    ![custom_queries](/Images/appc/download/attachments/60143477/custom_queries.png)
3.  Select **Crash** as the option under **Grouping** to group the results and use **data.meta.username** as the property name to filter the username. Note: if you are using ACA version 1.2, use **data.username** instead of data.meta.username.
    
4.  To **filter** on the **username value**, you should set the username value with the [setusername](https://docs.appcelerator.com/platform/latest/#!/api/Modules.Performance-method-setUsername). You can also set properties that would provide diagnostic information, like battery information, network conditions, or custom app properties using [setMetadata](https://docs.appcelerator.com/platform/latest/#!/api/Modules.Performance-method-setUsername) and query for those values by filtering against data.meta.key. Additionally, the custom queries interface provides options to filter on platform versions, device model, app versions, and other properties that are supported by the platform by default.
    

## Crash Events, Feature Events, and Breadcrumbs

When you attach breadcrumbs, the breadcrumbs are sent to the platform as feature events. Breadcrumbs are _not_ displayed by default (along with other feature events in analytics view) in the breadcrumbs view of crash details. To view the breadcrumb details, you must enable the feature events by checking the box labeled **Include feature events** and then expand the breadcrumb list in the breadcrumb tabs.

![Picture1](/Images/appc/download/attachments/60143477/Picture1.png)

Since crash events are treated as another type of AMPLIFY Analytic event, the crash events are counted against the organization’s analytics event capacity. Crash events have the same retention period entitlements as analytics events (2 years for Enterprise plans and 3 months for Pro plans).