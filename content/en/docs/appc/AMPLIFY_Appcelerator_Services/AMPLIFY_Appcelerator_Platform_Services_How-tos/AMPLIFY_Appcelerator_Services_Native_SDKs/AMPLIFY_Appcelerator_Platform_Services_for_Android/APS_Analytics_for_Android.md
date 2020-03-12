{"title":"APS Analytics for Android","weight":"20"} 

Pro or Enterprise Subscription Required

This AMPLIFY Appcelerator Services feature requires a Pro or Enterprise Subscription.

*   [Introduction](#Introduction)
    
*   [Terminology](#Terminology)
    
*   [Getting started](#Gettingstarted)
    
    *   [Advanced initialization options](#Advancedinitializationoptions)
        
        *   [Session timeout](#Sessiontimeout)
            
    *   [Setup user session events](#Setupusersessionevents)
        
*   [Creating custom events](#Creatingcustomevents)
    
    *   [Feature events](#Featureevents)
        
    *   [Geo events](#Geoevents)
        

This page describes how to use the AMPLIFY Appcelerator Services Analytics for native Android applications, built with Java and the Android APIs.

Not developing a native Android application with Java?

See the following topics to use the Appcelerator Analytics Service on other platforms:

![ios_icon](/Images/appc/download/attachments/43298722/ios_icon.png)

For native iOS applications built with Objective-C, see [APS Analytics for iOS](/docs/appc/AMPLIFY_Appcelerator_Services/AMPLIFY_Appcelerator_Platform_Services_How-tos/AMPLIFY_Appcelerator_Services_Native_SDKs/AMPLIFY_Appcelerator_Platform_Services_for_iOS/APS_Analytics_for_iOS/).

![titanium_icon](/Images/appc/download/attachments/43298732/titanium_icon.png)

For Titanium Applications, see [Appcelerator Analytics](/docs/appc/AMPLIFY_Appcelerator_Services/AMPLIFY_Appcelerator_Services_Guide/Appcelerator_Analytics/).

## Introduction

Appcelerator Analytics collects real-time data about your application's usage which can then be viewed in the **[Analytics dashboard](/docs/appc/Appcelerator_Dashboard/Appcelerator_Dashboard_Guide/Managing_Applications/Managing_Client_Applications/#AnalyticsViewingReal-timeandAggregatedAnalytics)** . By default, the Analytics dashboard provides information about app installs, number of sessions, and average app session length (organized by app name, platform, and geography). Your app can also utilize custom analytic events and event funnels.

This document provides an overview of the features provided by Analytics, and how to use them using the Titanium SDK. **If you are developing an iOS application with Objective-C or Swift or an Android application with Java**, see [APS Analytics for iOS](/docs/appc/AMPLIFY_Appcelerator_Services/AMPLIFY_Appcelerator_Platform_Services_How-tos/AMPLIFY_Appcelerator_Services_Native_SDKs/AMPLIFY_Appcelerator_Platform_Services_for_iOS/APS_Analytics_for_iOS/) or [APS Analytics for Android](#undefined) for details on using Analytics.

For platform-specific details about how analytics captured, see [Analytics Architecture](/docs/appc/AMPLIFY_Appcelerator_Services/AMPLIFY_Appcelerator_Services_Guide/Appcelerator_Analytics/Analytics_Architecture/).

For information about viewing analytics data, see [Managing Client Applications](/docs/appc/Appcelerator_Dashboard/Appcelerator_Dashboard_Guide/Managing_Applications/Managing_Client_Applications/#AnalyticsViewingReal-timeandAggregatedAnalytics).  
  
**Please ask your Confluence administrator to update the license for the [MultiExcerpt Plugin for Confluence 4+](https://plugins.atlassian.com/plugins/biz.artemissoftware.confluence.multiexcerpt.MultiExcerptMacro) .**  
**Admin Info: The error is: license VERSION\_MISMATCH**

## Terminology

**Analytics** refers to data about how your application has been used, as well as information about how users interact with your application. Analytics data is transmitted in the form of _events_.

Events are operational milestones in the application. Some events are generated automatically, such as those that mark an installation, or the beginning and end of a session. Others may be **custom events**, which have a meaning specific to an application, such as tapping a specific button or opening a certain window.

A feature event represents an action a user could take in an application, such as 'liking an item' or launching a video'. Applications use the Titanium or APSAnalytics API to create custom events.

**Event funnels** let you define custom, ordered event sequences that let you track a specific user process, such as finding a product and making a purchase.

The **Analytics dashboard** organizes, analyzes, and presents analytics data captured for your applications. You also use the Analytics dashboard to create and view event funnels.  
  
**Please ask your Confluence administrator to update the license for the [MultiExcerpt Plugin for Confluence 4+](https://plugins.atlassian.com/plugins/biz.artemissoftware.confluence.multiexcerpt.MultiExcerptMacro) .**  
**Admin Info: The error is: license VERSION\_MISMATCH**

## Getting started

To integrate the Analytics service with a new or existing Android application:

1.  Go to the [Dashboard](https://platform.axway.com/) and create a new native Android application.
    
2.  Download the Services SDK and get your Analytics application key.
    
3.  Unpack the Services SDK ZIP file.
    
4.  Copy the appcelerator-sdk-android-<VERSION>.jar to the lib folder of your Android project.
    
5.  Modify the project's AndroidManifest.xml file to include the following permissions and to add the APSAnalytics package as a service:
    
    AndroidManifest.xml
    
    `<?``xml`  `version``=``"1.0"`  `encoding``=``"utf-8"``?>`
    
    `<``manifest`  `xmlns:android``=``"http://schemas.android.com/apk/res/android"`
    
    `package``=``"com.appcelerator.sample"`
    
    `android:versionCode``=``"1"`
    
    `android:versionName``=``"1.0"` `>`
    
    `<!-- Add these permissions to enable Analytics -->`
    
    `<``uses``-permission` `android:name``=``"android.permission.ACCESS_NETWORK_STATE"``/>`
    
    `<``uses``-permission` `android:name``=``"android.permission.ACCESS_WIFI_STATE"``/>`
    
    `<``uses``-permission` `android:name``=``"android.permission.INTERNET"``/>`
    
    `<``uses``-permission` `android:name``=``"android.permission.WRITE_EXTERNAL_STORAGE"`
    
    `android:maxSdkVersion``=``"18"` `/>`
    
    `<``application``>`
    
    `<``activity``>`
    
    `...`
    
    `</``activity``>`
    
    `<!-- Add this service to enable Analytics -->`
    
    `<``service`  `android:name``=``"com.appcelerator.aps.APSAnalyticsService"`
    
    `android:exported``=``"false"` `/>`
    
    `</``application``>`
    
    `</``manifest``>`
    
6.  Add the following import statements to the main Activity of the project:
    
    MainActivity.java
    
    `import` `com.appcelerator.aps.APSServiceManager;`
    
    `import` `com.appcelerator.aps.APSAnalytics;`
    
7.  In the main Activity's onCreate() method, enable the service by calling the APSServiceManager's enable method. Pass the method the application context as the first argument and the APS application key as the second argument.
    
    `public`  `void` `onCreate() {`
    
    `APSServiceManager.getInstance().enable(getApplicationContext(),` `"APP_KEY"``);`
    
    `}`
    
    To get your APS App key:
    
    1.  Go to the [Dashboard](https://platform.axway.com/).
        
    2.  Select your application from the **Apps** drop-down menu.
        
    3.  Click the **Overview** tab.
        
    4.  Click the **Services** button.
        
    5.  Click **Show Key** under the Analytics, Performance and Cloud section.
        
    

The Android application can now make additional method calls using the [APSAnalytics class](http://docs.appcelerator.com/aps-sdk-apidoc/latest/android/com/appcelerator/aps/APSAnalytics.html). Before making API calls to the APSAnalytics class, you need to retrieve a shared instance using the getInstance() method. Make APSAnalytics API calls using the shared instance.

For the Android platform, you need to set up the application to send [user session events](#Setupuser).

### Advanced initialization options

#### Session timeout

By default, after the application has been backgrounded for 30000 milliseconds (30 seconds), the Analytics service ends the current user session and starts a new one when the application enters the foreground again. To adjust the timeout, use the APSAnalytics's setSessionTimeout() method.

`// Sets the timeout to 15000 milliseconds (15 seconds) instead of 30000 milliseconds.`

`APSAnalytics.getInstance().setSessionTimeout(``15000``, TimeUnit.MILLISECONDS);`

### Setup user session events

On the Android platform, user session events are not automatically sent, unlike the iOS and Titanium platforms. You need to add three APSAnalyitcs method calls in the main Activity of your application in order to capture user session data.

1.  Call the [sendAppEnrollEvent()](http://docs.appcelerator.com/aps-sdk-apidoc/latest/android/com/appcelerator/aps/APSAnalytics.html#sendAppEnrollEvent()) method right after the application calls the APSServiceManager.getInstance().enable() in the onCreate() method. The enroll event indicates application installs or upgrades.
    
2.  Call the sendAppForegroundEvent() method inside the main Activity's onResume() method. The foreground event indicates when the application is being used.
    
3.  Call the sendAppBackgroundEvent() method inside the main Activity's onPause() method. The background event indicates when the application has been dismissed.
    

MainActivity.java

`@Override`

`protected`  `void` `onCreate(Bundle savedInstanceState) {`

`super``.onCreate(savedInstanceState);`

`setContentView(R.layout.activity_main);`

`APSServiceManager.getInstance().enable(getApplicationContext(),` `"APP_KEY"``);`

`APSAnalytics.getInstance().sendAppEnrollEvent();`

`}`

`@Override`

`public`  `void` `onPause(){`

`super``.onPause();`

`APSAnalytics.getInstance().sendSessionBackgroundEvent();`

`}`

`@Override`

`public`  `void` `onResume(){`

`super``.onResume();`

`APSAnalytics.getInstance().sendSessionForegroundEvent();`

`}`

## Creating custom events

You use the [A](#!/api/Titanium.Analytics) PSAnalytics API to log and report custom events. [Feature Events](#Featureevents) are for capturing a user action, such as selecting a specific menu option or launching a video.

### Feature events

You use the APSAnalytics' sendAppFeatureEvent() method to generate a feature event that captures a specific application or user activity. A feature event should represent an action, such as launching a video, or 'new item', 'launch video', and so forth. The name you assign to a feature event should incorporate the application state into the event name, rather than long descriptive names. The following naming convention is suggested, where _group.event_ refers to the parent event: group.event.sub-event

Feature event names should be as generic as possible. For instance, if you want to track when users select a certain menu option, use a name like **"user.menu.selection"**, not **"joeuser.menu.selection"**. The first option is better because it groups all the same types of events into a single metric that's easy to view on Dashboard. The person analyzing the data only has to look at a single number to get an overview of how many users have selected that menu option. The second might be fine for very small user bases, but if you have more than 100 users it means that the person analyzing the data would have to look through 100 different event names to be able to generate any useful data.

For example, to track a user's menu selection you might use the following code, where the 10 digit number uniquely identifies the selection in your code:

Good Practice: Track the State with the Naming Syntax

`APSAnalytics.getInstance().sendAppFeatureEvent(``"select.item.12345678910"``,` `null``);`

You should avoid using long, descriptive event names, as shown below:

Bad Practice: Avoid Long Descriptions

`APSAnalytics.getInstance().sendAppFeatureEvent(``"Select Item THIS IS THE DESCRIPTION OF THE EVENT -12345678910"``,` `null``);`

### Geo events

Use the APSAnalytics' sendAppGeoEvent() method to send real-time geographic data to the Analytics service. Pass the method an Android [Location](http://developer.android.com/reference/android/location/Location.html) object.

In the following example, the application uses a default location provider to get location information from the device. The application sends the location data to the Analytics service.

MainActivity.java

`/*`

`* Don't forget to add the ACCESS_COARSE_LOCATION and ACCESS_FINE_LOCATION permissions`

`* in the AndroidManifest.xml file.`

`*/`

`public`  `class` `MainActivity` `extends` `Activity` `implements` `LocationListener{`

`private` `LocationManager locationManager;`

`private` `String provider;`

`@Override`

`protected`  `void` `onCreate(Bundle savedInstanceState) {`

`super``.onCreate(savedInstanceState);`

`setContentView(R.layout.activity_main);`

`// Initialize Analytics`

`APSServiceManager.getInstance().enable(getApplicationContext(),` `"APP_KEY"``);`

`APSAnalytics.getInstance().sendAppEnrollEvent();`

`// Get the location manager and use a default provider`

`locationManager = (LocationManager) getSystemService(Context.LOCATION_SERVICE);`

`Criteria criteria =` `new` `Criteria();`

`provider = locationManager.getBestProvider(criteria,` `false``);`

`Location location = locationManager.getLastKnownLocation(provider);`

`// Initialize the location`

`if` `(location !=` `null``) {`

`Log.i(``"GEO"``,` `"Provider "` `+ provider +` `" has been selected."``);`

`onLocationChanged(location);`

`}`

`}`

`// Get location updates`

`public`  `void` `onLocationChanged(Location location) {`

`APSAnalytics.getInstance().sendAppGeoEvent(location);`

`Log.i(``"GEO"``, location.getLatitude() +` `","` `+ location.getLongitude());`

`}`

`@Override`

`protected`  `void` `onResume() {`

`super``.onResume();`

`APSAnalytics.getInstance().sendAppForegroundEvent();`

`// Request location updates at least every 5 minutes`

`// and only if the location between updates is at least 1000 meters`

`locationManager.requestLocationUpdates(provider,` `5` `*` `60` `*` `1000``,` `1000``,` `this``);`

`}`

`@Override`

`protected`  `void` `onPause() {`

`super``.onPause();`

`APSAnalytics.getInstance().sendAppBackgroundEvent();`

`// Stop update requests`

`locationManager.removeUpdates(``this``);`

`}`

`@Override`

`public`  `void` `onStatusChanged(String s,` `int` `i, Bundle bundle) {`

`// To be implemented`

`}`

`@Override`

`public`  `void` `onProviderEnabled(String s) {`

`// To be implemented`

`}`

`@Override`

`public`  `void` `onProviderDisabled(String s) {`

`// To be implemented`

`}`

`}`