{"title":"Appcelerator Performance Management","weight":"30"} 

# Appcelerator Performance Management

Deprecation Notice

In conjunction with the release of the AMPLIFY Crash module feature, this feature has been deprecated. To begin using the AMPLIFY Crash module feature, refer to [AMPLIFY Crash Analytics](/docs/appc/AMPLIFY_Appcelerator_Services/AMPLIFY_Appcelerator_Platform_Services_How-tos/AMPLIFY_Crash_Analytics/).

This AMPLIFY Appcelerator Services feature requires an Enterprise Subscription.

This page describes how to use the Appcelerator Performance Management module API to help track crashes in your application.

*   [Introduction](#Introduction)
    
*   [Using Appcelerator Performance](#UsingAppceleratorPerformance)
    
    *   [Setup Your Project](#SetupYourProject)
        
    *   [Initialize the Module](#InitializetheModule)
        
    *   [Create a Breadcrumb Trail](#CreateaBreadcrumbTrail)
        
    *   [Add User Metadata](#AddUserMetadata)
        
    *   [Log An Error](#LogAnError)
        
    *   [Allow the User to Opt-Out](#AllowtheUsertoOpt-Out)
        
    *   [Check for a Crash](#CheckforaCrash)
        
    *   [Android-Specific Features](#Android-SpecificFeatures)
        
        *   [Capture Logcat Data](#CaptureLogcatData)
            
        *   [Set a Custom Notification Title](#SetaCustomNotificationTitle)
            
*   [Further Reading](#FurtherReading)
    

## Introduction

The Appcelerator Performance service, powered by Apteligent, monitors your application's health, crashes and overall performance. Using Appcelerator Performance, developers are able to analyze crash reports to see why applications crashed and focus on the specific problems on user feedback.

Currently, the Appcelerator Performance service only supports the Android and iOS platforms.

When you log into the Appcelerator Performance dashboard, you may encounter a gray navigation bar across the top, right below the AMPLIFY Appcelerator Services navigation bar, and an orange "Contact us!" pop-up when you navigate to certain areas of the dashboard. These items are for Apteligent customers using native SDKs and are invalid for Appcelerator mobile applications.

For support with Appcelerator Performance, visit [http://support.appcelerator.com](http://support.appcelerator.com).

For additional documentation, see the "Further Reading" section below.

## Using Appcelerator Performance

To use the Appcelerator Performance service, enable Appcelerator Services for your project, then use the Appcelerator Performance module API to add breadcrumbs, user metadata and error handling code to log events leading up to a crash. Login to the Dashboard and use the Appcelerator Performance dashboard to monitor application performance and analyze crash reports.

![PerformanceDashboard_new](/Images/appc/download/attachments/43298691/PerformanceDashboard_new.png)

### Setup Your Project

When creating a new application in Appcelerator Studio, make sure the **Enable Appcelerator Services** check box is enabled.

For a previously created project, if Appcelerator Services were not previously enabled, open your tiapp.xml file, then click the **Enable Services** button under the _Appcelerator Service_ section.

Appcelerator Studio injects code into the tiapp.xml file to set up the Appcelerator Performance Management module (com.appcelerator.apm). See [Platform Services](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Titanium_Development/Platform_Services/) for the code modifications. Do not modify these changes made by Appcelerator Studio or else you will disable the Appcelerator Performance service.

### Initialize the Module

Before making API calls to the Performance module, the application needs to load the module and initialize it. Load the module using the require() method and pass the name of the module ( com.appcelerator.apm ) to the method, then initialize the module by call the init() method.

`var` `apm = require(``"com.appcelerator.apm"``);`

`apm.init();`

For Alloy projects, you can keep a global reference to the module in the Alloy.Globals namespace.

app/alloy.js

`Alloy.Globals.apm = require(``"com.appcelerator.apm"``);`

`Alloy.Globals.apm.init();`

Make Performance Management module API calls using the app object. For complete API information, see [Performance Module API](#!/api/Modules.Performance).

By default, the init() method uses the value of the com-appcelerator-apm-id key in the tiapp.xml file to initialize the Performance service. You can optionally pass a different ID by passing it as an argument to the init method . The app ID passed to the init method takes precedence over the com-appcelerator-apm-id key.

To get your APM App ID either:

*   Open your tiapp.xml file (in the Overview view) and click the **Show ID** link next to the **Performance** service or look for the com-appcelerator-apm-id key in the raw view.
    
*   Go to the [Dashboard](https://platform.axway.com/), select your application, click **Performance** and click **Settings** in the left pane. In the right pane, select the **Basics** tab and locate **Crittercism App ID**.
    

### Create a Breadcrumb Trail

To make it easier to track the events leading up to a crash, use the leaveBreadcrumb method to add breadcrumbs in your code. Place breadcrumbs near events and application state changes to track problematic paths that can lead to an application crash. Append variables to your breadcrumbs to track their state. For example:

`// If Alloy project`

`// var apm = Alloy.Globals.apm;`

`function` `alphaCB (args) {`

`apm.leaveBreadcrumb(``'enter alphaCB:'` `+ JSON.stringify(args));`

`//do some stuff...`

`apm.leaveBreadcrumb(``'exit alphaCB:'` `+ result);`

`return` `result;`

`}`

`function` `betaCB (args) {`

`apm.leaveBreadcrumb(``'enter betaCB:'` `+ JSON.stringify(args));`

`// do some stuff...`

`apm.leaveBreadcrumb(``'exit betaCB:'` `+ result);`

`return` `result;`

`}`

`switch` `(state) {`

`apm.leaveBreadcrumb(``'switch:'` `+ state);`

`case` `x :`

`alphaCB({foo: 1});`

`break``;`

`case` `y :`

`alphaCB({foo: 2});`

`betaCB({foo: 1});`

`break``;`

`default` `:`

`alphaCB({foobar: 0});`

`betaCB({foobar: 0});`

`}`

These breadcrumbs are collected and passed to the Appcelerator Performance service. To view the breadcrumbs, in the Appcelerator Performance dashboard, when viewing a specific application, click either **Crash Reports** or **Handled Exceptions**. In the list of crashes or handled errors in the right pane, click on the crash or error to view its details. Click the **Breadcrumbs** tab to view the breadcrumb trails leading up to the crash or error.

The most recent 100 breadcrumbs are displayed before the crash occurred. A breadcrumb can be up to 140 characters.

### Add User Metadata

Use the setUsername and setMetadata methods to differentiate users of your application when viewing reports on the Appcelerator Performance dashboard. For example:

`// If Alloy project`

`// var apm = Alloy.Globals.apm;`

`var` `status = login(username);`

`if` `(status) {`

`// Sets the username`

`apm.setUsername(username);`

`// Sets some user state metadata for tracking errors`

`apm.setMetadata(``'lastLogin'``, datetime);`

`}`

`// Track the user's state`

`apm.setMetadata(``'gameLevel'``, 0);`

`// do some stuff...`

`apm.setMetadata(``'gameLevel'``, 1);`

`// do some stuff...`

`apm.setMetadata(``'gameLevel'``, 2);`

By default, a guest profile is created to differentiate users if a username is not specified. The username appears with the crash or error reports.

To access the user metadata, either click on a username in a crash or error report to open a detailed view, or in the Appcelerator Performance dashboard, when viewing a specific application, click **Search by User** in the left pane then in the right pane, enter a user's name to find information about them.

### Log An Error

You can track handled errors in your application by passing a JavaScript Error object to thelogHandledException method, which can help identify and analyze potential errors and hot spots. For example:

`// If Alloy project`

`// var apm = Alloy.Globals.apm;`

`try` `{`

`var` `err =` `new` `Error(``'FATAL ERROR: Value cannot be null or undefined!'``);`

`if` `(value ===` `null` `|| value === undefined)` `throw` `err;`

`}`

`catch` `(err) {`

`apm.logHandledException(err);`

`}`

Error logs are useful for tracking crashes in third-party SDKs, code that syncs data between services, or detecting bad data that is returned from a server.

To view handled errors, in the Appcelerator Performance dashboard, when viewing a specific application, click **Handled Exceptions** in the left pane. A list of handled errors and statistics appears in the right pane. Click an error to view it in more detail.

Appcelerator Performance limits the logging of handled errors to one per minute. Up to five errors are buffered and are subsequently sent after the one minute limit.

### Allow the User to Opt-Out

Use the setOptOutStatus method to allow the user NOT to send any information to the Appcelerator Performance service. Passing true to this method disables sending data to Appcelerator Performance.

`// If Alloy project`

`// var apm = Alloy.Globals.apm;`

`// Disable sending data to Appcelerator Performance`

`apm.setOptOutStatus(``true``);`

### Check for a Crash

Use the didCrashOnLastAppLoad method to check if the application crashed in a previous session. If the method returns true, the application crashed on the last session.

`// If Alloy project`

`// var apm = Alloy.Globals.apm;`

`if` `(apm.didCrashOnLastAppLoad()){`

`// Application crashed on the last load`

`// Do something...`

`}`

### Android-Specific Features

Most of the Android features below are specified by passing a dictionary object as the second parameter to the init() method:

`// If Alloy project`

`// var apm = Alloy.Globals.apm;`

`var` `params = {`

`shouldCollectLogcat:` `true``,`

`notificationTitle:` `'customTitle'`

`};`

`apm.init(``'YOUR_CRITTERCISM_APP_ID'``, params);`

See the topics below for a description of each dictionary key.

#### Capture Logcat Data

To include the Android system log data with your crash reports, you must do the following:

For Google API Level 15 and earlier, add the following line to the Android manifest section of your tiapp.xml file:

`<uses-permission android:name=``"android.permission.READ_LOGS"``/>`

For Google API Level 16 and later, when initializing the module, specify {shouldCollectLogcat: true} as a second parameter when calling the init method:

`apm.init(``'YOUR_CRITTERCISM_APP_ID'``, {shouldCollectLogcat:` `true``});`

#### Set a Custom Notification Title

To include a custom notification title for alerts, specify the notificationTitle key as a second parameter when calling the init method:

`apm.init(``'YOUR_CRITTERCISM_APP_ID'``, {notificationTitle:` `'customTitle'``});`

## Further Reading

For complete API information, see [Performance Module API](#!/api/Modules.Performance).