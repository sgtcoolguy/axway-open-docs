{"title":"Analytics Architecture","weight":"10"} 

*   [Overview](#Overview)
    
*   [Android Analytics](#AndroidAnalytics)
    
*   [iOS Analytics](#iOSAnalytics)
    
*   [FAQ](#FAQ)
    
    *   [What counts as a new session?](#Whatcountsasanewsession?)
        
    *   [The device details of the Analytics page displays information, such as "iPad2, 7" or "iPad3, 3". What is the meaning of the number after the comma?](#ThedevicedetailsoftheAnalyticspagedisplaysinformation,suchas"iPad2,7"or"iPad3,3".Whatisthemeaningofthenumberafterthecomma?)
        
    *   [The number of total installs reported in Appcelerator Analytics does not match the number of downloads that are reported by the iTunes or Android app store. What is going on?](#ThenumberoftotalinstallsreportedinAppceleratorAnalyticsdoesnotmatchthenumberofdownloadsthatarereportedbytheiTunesorAndroidappstore.Whatisgoingon?)
        
    *   [How do I disable Titanium Analytics?](#HowdoIdisableTitaniumAnalytics?)
        

This page describes the Analytics Architecture for AMPLIFY Appcelerator Services SDK, and Titanium SDK 3.3.0 and later.

## Overview

Analytics are sent by Titanium applications automatically unless the developer has chosen to turn them off. Generic analytics data about user activity session starts and ends, and application installations and upgrades are sent by default. Developers may send additional data to help understand how users are interacting with their application. Some analytics data can be viewed using the Analytics user interface.

By default, only the following events are sent by the Analytics module:

*   ti.enroll: indicates the first launch of the application after an installation or upgrade
    
*   ti.foreground: indicates the application is in the foreground and the start of a new session
    
*   ti.background: indicates the application is in the background and the current session has ended
    

For a tutorial about sending additional data, see [Appcelerator Analytics](/docs/appc/AMPLIFY_Appcelerator_Services/AMPLIFY_Appcelerator_Services_Guide/Appcelerator_Analytics/#Creatingcustomevents).

## Android Analytics

For the Android platform, the Analytics module sends three events: ti.enroll, which determines user installations or upgrades the first time an application is ran, and ti.foreground and ti.background, which determines the session of application activity by the user.

The ti.enroll event is generated when onCreate() is called. This event is only sent once on the first launch of the application after it has been installed or updated.

The ti.foreground event is generated each time the activity calls the onResume() method. The event is queued and is only sent if this is not the first event and the ti.background event has not been generated recently. If a ti.background event was processed within the last 30 seconds\*, this indicates that a new activity is being opened on top of an old activity. A possible scenario is if you hit the Home button, then reopen the app quickly resulting in a ti.foreground event to be placed on top of a ti.background event. In this case, both events are removed from the queue and the current session is still active.

The ti.background event is generated when the activity calls the onPause() method, which occurs in the following scenarios:

*   A new activity opens on top of the current activity, so the current activity (A1) is being replaced by a new activity (A2). In this scenario, the old activity (A1) would receive an onPause() call, which generates a ti.background event, then within a short period, the new activity (A2) would start and receive its onResume() call, which generates a ti.foreground event. Both of these events are removed from the queue, marking the current session as still active.
    
*   The application is placed in the background by hitting the Home button or Power button. In this scenario, the current activity receives an onPause() call, which generates a ti.background event to be placed in the event queue, which is sent after a small threshold of time to ensure a ti.foreground event is not generated.
    

Having onPause() generate the ti.background event ensures that it is generated in cases where the app was forced killed by the user or by the system due to low memory. The same case would be applicable in the scenario where the current activity is the only activity in the stack and it is closed by backing out of the application using the Back button until the application closes.

## iOS Analytics

For the iOS platform, the Analytics module sends the same events as the Android platform:

*   The ti.enroll event is only sent once on the first launch of the application after it has been installed or updated.
    
*   The ti.foreground event is generated when the application boots up and enters the foreground while the app transitions from the background to the active state, that is, from within the applicationWillEnterForeground method.
    
*   The ti.background event is generated when the application is in the background, that is, from within the applicationDidEnterBackground method, and when the application thread terminates.
    

Events stored in the analytics queue are polled and sent in batches. In case of a send failure, unsent events are queued and resends of the events are attempted five times before giving up. All pending events, which failed during the send, are queued and sent when the next event is generated.

## FAQ

### What counts as a new session?

A session is a period of activity that a user has used the application. This may not necessarily be the period when the application boots and terminates. If the application is placed in the background, then put back in the foreground at a later time, this ends the previous session and creates a new session respectively.

### The device details of the Analytics page displays information, such as "iPad2, 7" or "iPad3, 3". What is the meaning of the number after the comma?

"iPad2, 7" or "iPad3, 3" is the hardware model of the device. The number after the comma means the actual model of the device. Some examples:

*   "iPad2, 7" is [iPad mini (Wi-Fi/Verizon & Sprint/GPS)](http://www.everymac.com/systems/apple/ipad/specs/apple-ipad-mini-original-a1455-4g-lte-verizon-sprint-specs.html)
    
*   "iPad3, 3" is [iPad 3rd Gen (Wi-Fi/Cellular AT&T/GPS)](http://www.everymac.com/systems/apple/ipad/specs/apple-ipad-3rd-gen-early-2012-gsm-4g-lte-att-specs.html)
    

Modify the device model in the following URL to retrieve information about the device: [http://www.everymac.com/ultimate-mac-lookup/?search\_keywords=iPad3,3](http://www.everymac.com/ultimate-mac-lookup/?search_keywords=iPad3,3).

### The number of total installs reported in Appcelerator Analytics does not match the number of downloads that are reported by the iTunes or Android app store. What is going on?

The number of downloads from the app store is not expected to match the number of unique devices that run an application. Reasons include but are not limited to the following:

*   A user can download an app once, and install it on multiple devices. For example, if a family has three iPhones and two iPads, and they share applications through iTunes home sharing, then there will be one iTunes download, and five installs in Appcelerator Analytics.
    
*   For applications built before Titanium Mobile version 3.3.0.GA, if a user deletes an application, and later re-downloads a previously installed app, there will be two separate downloads from the app store, but the number of users in Appcelerator Analytics will not change because the machine ID will have been seen before.
    
*   When a new version of the app is released, many users will upgrade by downloading the new version. However, the downloads are actually upgrades and will not count as new installs in Appcelerator Analytics.
    
*   A user may download an application and never run it or run it when the device has no network connectivity to send analytic events.
    

### How do I disable Titanium Analytics?

Note that disabling Titanium Analytics will disable or display no data when you visit either platform.appcelerator.com for the Analytics section.

Open your project's tiapp.xml file. If the file contains the following tag: <analytics>true</analytics>, set the value to false. If this tag does not exist, you need to add it as a child of the <ti:app> parent tag with the value set to false.