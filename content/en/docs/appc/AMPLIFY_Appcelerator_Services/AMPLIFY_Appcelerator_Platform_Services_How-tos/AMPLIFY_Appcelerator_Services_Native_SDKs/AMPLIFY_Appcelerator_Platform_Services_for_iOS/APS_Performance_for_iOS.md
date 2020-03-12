{"title":"APS Performance for iOS","weight":"40"} 

# APS Performance for iOS

Enterprise Subscription Required!

This AMPLIFY Appcelerator Services feature requires an Enterprise Subscription.

*   [Introduction](#Introduction)
    
*   [Using Appcelerator Performance](#UsingAppceleratorPerformance)
    
    *   [Setup Your Project](#SetupYourProject)
        
    *   [Create a Breadcrumb Trail](#CreateaBreadcrumbTrail)
        
    *   [Add User Metadata](#AddUserMetadata)
        
    *   [Log An Exception](#LogAnException)
        
    *   [Allow the User to Opt-Out](#AllowtheUsertoOpt-Out)
        
    *   [Check for a Crash](#CheckforaCrash)
        
*   [Further Reading](#FurtherReading)
    

This page describes how to use the AMPLIFY Appcelerator Services Performance (APS) for native iOS applications, built with Objective-C and the iOS APIs.

Not developing a native iOS application with Objective-C?

See the following topics to use the Appcelerator Performance Service on other platforms:

![android_icon](/Images/appc/download/attachments/43298732/android_icon.png)

For native Android applications built with Java, see [APS Performance for Android](/docs/appc/AMPLIFY_Appcelerator_Services/AMPLIFY_Appcelerator_Platform_Services_How-tos/AMPLIFY_Appcelerator_Services_Native_SDKs/AMPLIFY_Appcelerator_Platform_Services_for_Android/APS_Performance_for_Android/).

![titanium_icon](/Images/appc/download/attachments/43298732/titanium_icon.png)

For Titanium Applications, see [Appcelerator Performance Management](/docs/appc/AMPLIFY_Appcelerator_Services/AMPLIFY_Appcelerator_Platform_Services_How-tos/Appcelerator_Performance_Management/).

## Introduction

The Appcelerator Performance service, powered by Apteligent, monitors your application's health, crashes and overall performance. Using Appcelerator Performance, developers are able to analyze crash reports to see why applications crashed and focus on the specific problems on user feedback.

This topic covers how to use the [APSPerformance API](http://docs.appcelerator.com/aps-sdk-apidoc/latest/ios/Classes/APSPerformance.html). For information about using the Performance Dashboard, see [Managing Performance and Crash Data](#undefined).

When you log into the Appcelerator Performance dashboard, you may encounter a gray navigation bar across the top, right below the AMPLIFY Appcelerator Services navigation bar, and an orange "Contact us!" pop-up when you navigate to certain areas of the dashboard. These items are for Apteligent customers using native SDKs and are invalid for Appcelerator mobile applications.

For support with Appcelerator Performance, visit [http://support.appcelerator.com](http://support.appcelerator.com).

## Using Appcelerator Performance

To use the Appcelerator Performance service, add the APS framework to your project, then use the APSPerformance API to add breadcrumbs, user metadata and exception handling code to log events leading up to a crash. Login to the Appcelerator Dashboard and use the Appcelerator Performance dashboard to monitor application performance and analyze crash reports.

### Setup Your Project

To integrate the Performance service with a new or existing iOS application:

1.  Go to the [Dashboard](https://platform.axway.com/) and create a new native iOS application.
    
2.  Download the Services SDK and get your Performance application key.
    
3.  Unpack the appcelerator-sdk-ios-<VERSION>.zip file.
    
4.  Drag the Appcelerator.framework folder into your Xcode project's root folder if you are using Xcode 6 and above, or the Frameworks folder if you are using Xcode 5 or below.
    
5.  Select **Copy items into destination…** and click **Finish**.
    
6.  Select your project in the Project Navigator and click the **Build Phases** tab.
    
7.  Expand the **Link Binary With Libraries** section and add the libsqlite3.dylib and libz.dylib frameworks.
    
8.  Click the **Build Settings** tab, then click the **All** button in the top-left corner of the tab.
    
9.  Expand the **Linking** section and add \-ObjC to **Other Linker Flags** .
    
10.  In your application delegate implementation file, import Appcelerator/Appcelerator.h .
    
    AppDelegate.m
    
    `#``import` `<Appcelerator/Appcelerator.h>`
    
11.  In the application delegate's application:didFinishLaunchingWithOptions method, enable the service by calling the APSServiceManager's enableWithAppKey: method.
    
    AppDelegate.m
    
    `- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions`
    
    `{`
    
    `[[APSServiceManager sharedInstance] enableWithAppKey:@``"APS_APP_KEY"``];`
    
    `return` `YES;`
    
    `}`
    
    To get your APS App key:
    
    1.  Login to the [AMPLIFY Platform](https://platform.axway.com/).
        
    2.  On the Dashboard tile, select **Go to Dashboard**.
        
    3.  Select your application from the Projects menu.
        
    4.  Click the **Overview** tab.
        
    5.  Click the **Services** button.
        
    6.  Click **Show Key** under the Analytics, Performance and Cloud section.
        
    

The iOS application is now ready to make method calls using the APSPerformance class.

### Create a Breadcrumb Trail

To make it easier to track the events leading up to a crash, use the leaveBreadcrumb method to add breadcrumbs in your code. Place breadcrumbs near events and application state changes to track problematic paths that can lead to an application crash. Append variables to your breadcrumbs to track their state. For example:

`- (``int``)alphaCB:(``int``)value {`

`[[APSPerformance sharedInstance] leaveBreadcrumb:[NSString stringWithFormat:@``"%@%d"``, @``"enter alphaCB:"``, value]];`

`//do some stuff...`

`[[APSPerformance sharedInstance] leaveBreadcrumb:[NSString stringWithFormat:@``"%@%d"``, @``"exit alphaCB:"``, result]];`

`return` `result;`

`}`

`- (``int``)betaCB:(``int``)value {`

`[[APSPerformance sharedInstance] leaveBreadcrumb:[NSString stringWithFormat:@``"%@%d"``, @``"enter betaCB:"``, value]];`

`// do some stuff...`

`[[APSPerformance sharedInstance] leaveBreadcrumb:[NSString stringWithFormat:@``"%@%d"``, @``"exit betaCB:"``, result]];`

`return` `result;`

`}`

`switch` `(state) {`

`[[APSPerformance sharedInstance] leaveBreadcrumb:[NSString stringWithFormat:@``"%@%d"``, @``"switch:"``, state]];`

`case` `x :`

`[self alphaCB:``1``];`

`break``;`

`case` `y :`

`[self alphaCB:``2``];`

`[self betaCB:``1``];`

`break``;`

`default` `:`

`[self alphaCB:``0``];`

`[self betaCB:``0``];`

`}`

These breadcrumbs are collected and passed to the Appcelerator Performance service. To view the breadcrumbs, in the Appcelerator Performance dashboard, when viewing a specific application, click either **Crash Reports** or **Handled Exceptions**. In the list of crashes or handled errors in the right pane, click on the crash or error to view its details. Click the **Breadcrumbs** tab to view the breadcrumb trails leading up to the crash or error.

The most recent 100 breadcrumbs are displayed before the crash occurred. A breadcrumb can be up to 140 characters.

### Add User Metadata

To differentiate users of your application when viewing reports on the Appcelerator Performance dashboard, use the username property to set the username of the session and use the \[\] subscription operator to leave custom metadata. For example:

`boolean` `status = [self login:username];`

`if` `(status) {`

`// Sets the username`

`[APSPerformance sharedInstance].setUsername = username;`

`// Sets some user state metadata for tracking errors`

`[APSPerformance sharedInstance][@``"lastLogin"``] = datetime;`

`}`

`// Track the user's state`

`[APSPerformance sharedInstance][@``"Game Level"``] = @(``0``);`

`// do some stuff...`

`[APSPerformance sharedInstance][@``"Game Level"``] = @(``1``);`

`// do some stuff...`

`[APSPerformance sharedInstance][@``"Game Level"``] = @(``2``);`

The username appears with the crash or error reports. By default, a guest profile is created to differentiate users if a username is not specified. To retrieve this unique identifier, use the uniqueIdentifier property.

To access the user metadata, either click on a username in a crash or error report to open a detailed view, or in the Appcelerator Performance dashboard, when viewing a specific application, click **Search by User** in the left pane then in the right pane, enter a user's name to find information about them.

### Log An Exception

You can track handled exceptions in your application by passing an NSException object to the logHandledException method, which can help identify and analyze potential errors and hot spots. For example:

`@try` `{`

`[NSException raise:NSGenericException format:@``"FATAL ERROR!"``];`

`}` `@catch` `(NSException *exception) {`

`[[APSPerformance sharedInstance] logHandledException:exception];`

`}`

Exception logs are useful for tracking crashes in third-party SDKs, code that syncs data between services, or detecting bad data that is returned from a server.

To view handled errors, in the Appcelerator Performance dashboard, when viewing a specific application, click **Handled Exceptions** in the left pane. A list of handled errors and statistics appears in the right pane. Click an error to view it in more detail.

Appcelerator Performance limits the logging of handled exceptions to one per minute. Up to five exceptions are buffered and are subsequently sent after the one minute limit.

### Allow the User to Opt-Out

Use the optOutStatus property to allow the user NOT to send any information to the Appcelerator Performance service. Passing true to this method disables sending data to Appcelerator Performance.

`// Disable sending data to Appcelerator Performance`

`[APSPerformance sharedInstance].optOutStatus = YES;`

### Check for a Crash

Use the didCrashOnLastAppLoad property to check if the application crashed in a previous session. If the property returns YES, the application crashed on the last session. Note that if optOutStatus is set to YES, this method always returns NO.

`if` `([APSPerformance sharedInstance].didCrashOnLastAppLoad){`

`// Application crashed on the last load`

`// Do something...`

`}`

## Further Reading

For complete API information, see [APSPerformance API](http://docs.appcelerator.com/aps-sdk-apidoc/latest/ios/Classes/APSPerformance.html).