{"title":"Building Queries","weight":"20"}

As of the Dashboard 5.3.0 release, the Query Builder feature has been replaced with Custom Queries feature. For additional information, refer to [Creating Custom Queries](#undefined).

The Custom Query feature assists you in creating queries against the analytics data collected from your mobile application. You can create custom queries based on [featureEvents](https://docs.appcelerator.com/platform/latest/#!/api/Titanium.Analytics-method-featureEvent) in your Titanium SDK applications using the Custom Queries feature. If you have [featureEvents](https://docs.appcelerator.com/platform/latest/#!/api/Titanium.Analytics-method-featureEvent) enabled in your application, you can create queries like, "Show me how many times, in the last month, users on Android, tapped the login button".

If you do not have [featureEvents](https://docs.appcelerator.com/platform/latest/#!/api/Titanium.Analytics-method-featureEvent) enabled in your application, but do have analytics turned on, you can still use the Custom Queries builder to create queries based on the default fields that are automatically logged (for example, OS, SDK version, and so forth).

Some of the capabilities of the Custom Queries feature are:

* Default filters for OS platform, device model, OS version, country, and deployment modes.

* Query for specific features or properties set against specific events in the application.

* Share the query publicly to all users in the organization.

* Build funnels based on the feature events configured in the application.

* Set up alert notifications when a query count is below or above a preset threshold.

* Compare and visualize multiple queries.

The Custom Queries feature is accessible through the **Analytics** menu on the Dashboard.

![query_builder_02_latest](/Images/appc/download/attachments/51250946/query_builder_02_latest.png)

For first-time users of the Custom Queries feature, a description of the Custom Queries feature will be displayed when the **Custom Queries** tab is selected. To navigate to the Custom Queries feature, click the **Go to Custom Queries** button. To prevent the description of the Custom Queries feature being displayed again, select **Do not show this page again**.

To create a custom query, refer to [Creating Custom Queries](https://docs.axway.com/bundle/Appcelerator_Dashboard_allOS_en/page/creating_custom_queries.html).

![query_builder_03_latest](/Images/appc/download/attachments/51250946/query_builder_03_latest.png)

Notifications can be configured on saved queries. Notifications can be sent through email, or the query results can be configured to be sent to a web URL for display on a web page.

![query_builder_05](/Images/appc/download/attachments/51250946/query_builder_05.png)
