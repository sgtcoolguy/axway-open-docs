{"title":"APS Performance for Android","weight":"30"} 

# APS Performance for Android

Pro or Enterprise Subscription Required

This AMPLIFY Appcelerator Services feature requires a Pro or Enterprise Subscription.

*   [Introduction](#Introduction)
    
*   [Using Appcelerator Performance](#UsingAppceleratorPerformance)
    
    *   [Setup your project](#Setupyourproject)
        
    *   [Create a breadcrumb trail](#Createabreadcrumbtrail)
        
    *   [Add user metadata](#Addusermetadata)
        
    *   [Log an exception](#Loganexception)
        
    *   [Allow the user to opt-out](#Allowtheusertoopt-out)
        
    *   [Check for a crash](#Checkforacrash)
        
*   [Further reading](#Furtherreading)
    

This page describes how to use the AMPLIFY Appcelerator Services Performance (APS) for native Android applications, built with Java and the Android APIs.

Not developing a native Android application with Java?

See the following topics to use the Appcelerator Performance Service on other platforms:

![ios_icon](/Images/appc/download/attachments/43298720/ios_icon.png)

For native iOS applications built with Objective-C, see [APS Performance for iOS](/docs/appc/AMPLIFY_Appcelerator_Services/AMPLIFY_Appcelerator_Platform_Services_How-tos/AMPLIFY_Appcelerator_Services_Native_SDKs/AMPLIFY_Appcelerator_Platform_Services_for_iOS/APS_Performance_for_iOS/).

![titanium_icon](/Images/appc/download/attachments/43298720/titanium_icon.png)

For Titanium Applications, see [Appcelerator Performance Management](/docs/appc/AMPLIFY_Appcelerator_Services/AMPLIFY_Appcelerator_Platform_Services_How-tos/Appcelerator_Performance_Management/).

## Introduction

The Appcelerator Performance service, powered by Apteligent, monitors your application's health, crashes, and overall performance. Using Appcelerator Performance, developers are able to analyze crash reports to see why applications crashed and focus on the specific problems on user feedback.

This topic covers how to use the [APSPerformance API](http://docs.appcelerator.com/aps-sdk-apidoc/latest/android/com/appcelerator/aps/APSPerformance.html). For information about using the Performance Dashboard, see [Application Details Screen: Performance Tab](/docs/appc/Appcelerator_Dashboard/Appcelerator_Dashboard_Guide/Managing_Applications/Managing_Client_Applications/#PerformanceTab).

When you log into the Appcelerator Performance dashboard, you may encounter a gray navigation bar across the top, right below the AMPLIFY Appcelerator Services navigation bar, and an orange "Contact us!" pop-up when you navigate to certain areas of the dashboard. These items are for Apteligent customers using native SDKs and are invalid for Appcelerator mobile applications.

For support with Appcelerator Performance, visit [http://support.appcelerator.com](http://support.appcelerator.com).

## Using Appcelerator Performance

To use the Appcelerator Performance service, add the APS library to your project, then use the APSPerformance API to add breadcrumbs, user metadata, and exception handling code to log events leading up to a crash. Log into the Dashboard and use the Appcelerator Performance dashboard to monitor application performance and analyze crash reports.

### Setup your project

To integrate the Performance service with a new or existing Android application:

1.  Go to the [Dashboard](https://platform.axway.com/) and create a new native Android application.
    
2.  Download the Services SDK and get your Performance application key.
    
3.  Unpack the Services SDK ZIP file.
    
4.  Copy theappcelerator-sdk-android-<VERSION>.jar to the lib folder of your Android project.
    
5.  Modify the project's AndroidManifest.xml file to include the following permissions:
    
    AndroidManifest.xml
    
    `<?``xml`  `version``=``"1.0"`  `encoding``=``"utf-8"``?>`
    
    `<``manifest`  `xmlns:android``=``"http://schemas.android.com/apk/res/android"`
    
    `package``=``"com.appcelerator.sample"`
    
    `android:versionCode``=``"1"`
    
    `android:versionName``=``"1.0"` `>`
    
    `<!-- Add these permissions to enable Performance -->`
    
    `<``uses``-permission` `android:name``=``"android.permission.ACCESS_NETWORK_STATE"``/>`
    
    `<``uses``-permission` `android:name``=``"android.permission.ACCESS_WIFI_STATE"``/>`
    
    `<``uses``-permission` `android:name``=``"android.permission.INTERNET"``/>`
    
    `<!-- Optional permissions for advanced reporting -->`
    
    `<``uses``-permission` `android:name``=``"android.permission.GET_TASKS"` `/>`
    
    `<``uses``-permission` `android:name``=``"android.permission.READ_LOGS"``/>`
    
    `</``manifest``>`
    
6.  Add the following import statements to the main Activity of the project:
    
    MainActivity.java
    
    `import` `com.appcelerator.aps.APSServiceManager;`
    
    `import` `com.appcelerator.aps.APSPerformance;`
    
7.  In the main Activity's onCreate() method, enable the service by calling the APSServiceManager's enable() method. Pass the method the application context as the first argument and the APS application key as the second argument. This provides basic app monitoring and crash reporting services.
    
    `public`  `void` `onCreate() {`
    
    `APSServiceManager.getInstance().enable(getApplicationContext(),` `"APP_KEY"``);`
    
    `}`
    
    To get your APS App key:
    
    1.  Login to the [AMPLIFY Platform](https://platform.axway.com/).
        
    2.  On the Dashboard tile, select **Go to Dashboard**.
        
    3.  Select your application from the Projects menu.
        
    4.  Click the **Overview** tab.
        
    5.  Click the **Services** button.
        
    6.  Click **Show Key** under the Analytics, Performance and Cloud section.
        
    

The Android application can now make additional method calls using the [APSPerformance class](http://docs.appcelerator.com/aps-sdk-apidoc/latest/android/com/appcelerator/aps/APSPerformance.html). Before making API calls to the APSPerformance class, you need to retrieve a shared instance using the getInstance() method. Make APSPerformance API calls using the shared instance.

### Create a breadcrumb trail

To make it easier to track the events leading up to a crash, use the leaveBreadcrumb() method to add breadcrumbs in your code. Place breadcrumbs near events and application state changes to track problematic paths that can lead to an application crash. Append variables to your breadcrumbs to track their state. For example:

`public`  `static`  `int` `alphaCB (``int` `value) {`

`APSPerformance.getInstance().leaveBreadcrumb(``"enter alphaCB:"` `+ value);`

`//do some stuff...`

`APSPerformance.getInstance().leaveBreadcrumb(``"exit alphaCB:"` `+ result);`

`return` `result;`

`}`

`public`  `static`  `int` `betaCB (``int` `value) {`

`APSPerformance.getInstance().leaveBreadcrumb(``"enter betaCB:"` `+ value);`

`// do some stuff...`

`APSPerformance.getInstance().leaveBreadcrumb(``"exit betaCB:"` `+ result);`

`return` `result;`

`}`

`switch` `(state) {`

`APSPerformance.getInstance().leaveBreadcrumb(``"switch:"` `+ state);`

`case` `x :`

`alphaCB(``1``);`

`break``;`

`case` `y :`

`alphaCB(``2``);`

`betaCB(``1``);`

`break``;`

`default` `:`

`alphaCB(``0``);`

`betaCB(``0``);`

`}`

These breadcrumbs are collected and passed to the Appcelerator Performance service. To view the breadcrumbs, in the Appcelerator Performance dashboard, when viewing a specific application, click either **Crash Reports** or **Handled Exceptions**. In the list of crashes or handled errors in the right pane, click on the crash or error to view its details. Click the **Breadcrumbs** tab to view the breadcrumb trails leading up to the crash or error.

The most recent 100 breadcrumbs are displayed before the crash occurred. A breadcrumb can be up to 140 characters.

### Add user metadata

Use the setUsername() and setMetadata() methods to differentiate users of your application when viewing reports on the Appcelerator Performance dashboard. For example:

`boolean` `status = login(username);`

`if` `(status) {`

`// Sets the username`

`APSPerformance.getInstance().setUsername(username);`

`// Sets some user state metadata for tracking errors`

`APSPerformance.getInstance().setMetadata(``"lastLogin"``, datetime);`

`}`

`// Track the user's state`

`APSPerformance.getInstance().setMetadata(``"gameLevel"``,` `0``);`

`// do some stuff...`

`APSPerformance.getInstance().setMetadata(``"gameLevel"``,` `1``);`

`// do some stuff...`

`APSPerformance.getInstance().setMetadata(``"gameLevel"``,` `2``);`

The username appears with the crash or error reports. By default, a guest profile is created to differentiate users if a username is not specified. To retrieve this unique identifier, use the getUniqueIdentifier() method.

To access the user metadata, either click on a username in a crash or error report to open a detailed view, or in the Appcelerator Performance dashboard, when viewing a specific application, click **Search by User** in the left pane then in the right pane, enter a user's name to find information about them.

### Log an exception

You can track handled exceptions in your application by passing a Java Exception object to the logHandledException() method, which can help identify and analyze potential errors and hot spots. For example:

`try` `{`

`throw` `Exception(``"FATAL ERROR!"``);`

`}`

`catch` `(exception) {`

`APSPerformance.getInstance().logHandledException(exception);`

`}`

Exception logs are useful for tracking crashes in third-party SDKs, code that syncs data between services, or detecting bad data that is returned from a server.

To view handled errors, in the Appcelerator Performance dashboard, when viewing a specific application, click **Handled Exceptions** in the left pane. A list of handled errors and statistics appears in the right pane. Click an error to view it in more detail.

Appcelerator Performance limits the logging of handled exceptions to one per minute. Up to five exceptions are buffered and are subsequently sent after the one minute limit.

### Allow the user to opt-out

Use the setOptOutStatus() method to allow the user NOT to send any information to the Appcelerator Performance service. Passing true to this method disables sending data to Appcelerator Performance.

`// Disable sending data to Appcelerator Performance`

`APSPerformance.getInstance().setOptOutStatus(``true``);`

### Check for a crash

Use the didCrashOnLastAppLoad() method to check if the application crashed in a previous session. If the method returns true, the application crashed on the last session. Note that if setOptOutStatus() is set to true, this method always returns false.

`if` `(APSPerformance.getInstance().didCrashOnLastAppLoad()){`

`// Application crashed on the last load`

`// Do something...`

`}`

## Further reading

For complete API information, see [APSPerformance API](http://docs.appcelerator.com/aps-sdk-apidoc/latest/android/com/appcelerator/aps/APSPerformance.html).