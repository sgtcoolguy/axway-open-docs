{"title":"Appcelerator Analytics","weight":"10"}

* [Introduction](#introduction)

* [Terminology](#terminology)

* [Getting started with Analytics](#getting-started-with-analytics)

* [Creating custom events](#creating-custom-events)

    * [Feature events](#feature-events)

* [Creating and viewing event funnels](#creating-and-viewing-event-funnels)

    * [Creating an event funnel](#creating-an-event-funnel)

    * [Viewing event funnels](#viewing-event-funnels)

## Introduction

Appcelerator Analytics collects real-time data about your application's usage, which can then be viewed in the **[Analytics dashboard](/docs/appc/Appcelerator_Dashboard/Appcelerator_Dashboard_Guide/Managing_Applications/Managing_Client_Applications/#viewing-real-time-and-aggregated-analytics)**. By default, the Analytics dashboard provides information about app installs, the number of sessions, and average app session length (organized by app name, platform, and geography). Your app can also utilize custom analytic events and event funnels.

This document provides an overview of the features provided by Analytics and how to use them using the Titanium SDK. **If you are developing an iOS application with Objective-C or Swift or an Android application with Java**, see [APS Analytics for iOS](/docs/appc/AMPLIFY_Appcelerator_Services/AMPLIFY_Appcelerator_Platform_Services_How-tos/AMPLIFY_Appcelerator_Services_Native_SDKs/AMPLIFY_Appcelerator_Platform_Services_for_iOS/APS_Analytics_for_iOS/) or [APS Analytics for Android](/docs/appc/AMPLIFY_Appcelerator_Services/AMPLIFY_Appcelerator_Platform_Services_How-tos/AMPLIFY_Appcelerator_Services_Native_SDKs/AMPLIFY_Appcelerator_Platform_Services_for_Android/APS_Analytics_for_Android/) for details on using Analytics.

For platform-specific details about how analytics captured, see [Analytics Architecture](/docs/appc/AMPLIFY_Appcelerator_Services/AMPLIFY_Appcelerator_Services_Guide/Appcelerator_Analytics/Analytics_Architecture/).

For information about viewing analytics data, see [Managing Client Applications](/docs/appc/Appcelerator_Dashboard/Appcelerator_Dashboard_Guide/Managing_Applications/Managing_Client_Applications/#viewing-real-time-and-aggregated-analytics).

## Terminology

**Analytics** refers to data about how your application has been used, as well as information about how users interact with your application. Analytics data is transmitted in the form of _events_.

Events are operational milestones in the application. Some events are generated automatically, such as those that mark an installation, or the beginning and end of a session. Others may be **custom events**, which have a meaning specific to an application, such as tapping a specific button or opening a certain window.

A feature event represents an action a user could take in an application, such as 'liking an item' or launching a video'. Applications use the Titanium or APSAnalytics API to create custom events.

**Event funnels** let you define custom, ordered event sequences that let you track a specific user process, such as finding a product and making a purchase.

The **Analytics dashboard** organizes, analyzes, and presents analytics data captured for your applications. You also use the Analytics dashboard to create and view event funnels.

## Getting started with Analytics

Enabling analytics is enabled by default when creating a project using **Appcelerator Studio** (Studio). If for some reason, it's not enabled, you can enable **Axway Appcelerator Platform Services** in the project's tiapp.xml and deploy your application.

**To enable analytics in a new Appcelerator project**:

1. In **Studio**, create a new Mobile Application (**File** \> **New Mobile App Project...**).

2. Make sure the **Enable Axway Appcelerator Platform Services** option is enabled in the New Mobile App Project dialog, and select the appropriate organization from the Organization pop-up menu. The application is tied to the account and organization used to create it.

    ![Enable_serices](/Images/appc/download/attachments/43298693/Enable_serices.png)
3. Enter the rest of the required project information and click **Finish**.

4. Build your application and deploy it to devices to begin collecting analytics data.

Next steps

* Once deployed, you can begin to view data captured for your application in the [Analytics dashboard](/docs/appc/Appcelerator_Dashboard/Appcelerator_Dashboard_Guide/Managing_Applications/Managing_Client_Applications/)

* Use [custom events](#creating-custom-events) to track basic usage and navigation patterns

* Create [event funnels](#CreatingandViewingEventFunnels) to analyze a specific process better

Enabling Appcelerator Services modifies your project's tiapp.xml file and other application files. Do not modify these code changes as it may break your project. See [Platform Services](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Titanium_Development/Platform_Services/) for details on what changes are made to your code.

## Creating custom events

The [Titanium.Analytics](#!/api/Titanium.Analytics) API can be used to send custom events and data, called feature events.

### Feature events

[Titanium.Analytics.featureEvent(name, data)](https://docs.appcelerator.com/platform/latest/#!/api/Titanium.Analytics-method-featureEvent) is used to send a feature event. A feature event can be used to represent a user action, application state, or send a data payload.

Feature event names should be as generic as possible and without spaces (for example, "_home\_window.open_" instead of "_Home Window Open_"). This allows events to be easily consolidated and queried from Dashboard.

User actions can be logged using feature events; here's an example of logging a user opening the home window of an app.

`// Detect when home window is opened.`

`home_window.addEventListener(``'open'``, e => {`

`// Send analytics feature event to log user action.`

`Ti.Analytics.featureEvent(``'home_window.open'``);`

`...`

`});`

In some cases, additional data can also be sent, which can be queried on Dashboard. In this example, an analytics event is sent when the user backgrounds their app.

`// Detect when application is backgrounded.`

`Ti.App.addEventListener(``'paused'``, e => {`

`// Send analytics feature event with payload.`

`// In this example, the user may have added items to their shopping basket but decided to exit the app.`

`// We can log how many items were in the users basket and query this data on Dashboard.`

`Ti.Analytics.featureEvent(``'shopping_basket.backgrounded'``, {`

`items: shopping_basket.count`

`});`

`...`

`});`

We can then create a custom query in Dashboard to calculate the average number of items users had in their basket upon backgrounding the application.

![averageItemsQuery](/Images/appc/download/attachments/43298693/averageItemsQuery.png)

## Creating and viewing event funnels

You use Dashboard to [create](#CreatinganEventFunnel) and [view](#ViewingEventFunnels) event funnels. Using event funnels involves the following basic steps:

1. **Identify the process to track**, such as a user sign-up, or product purchase flow.

2. **Identifying the custom events** to be recorded and when they should be captured in the process.

3. **Instrumenting the custom events** in your application, as described in [Creating Custom Events](#creating-custom-events).

4. **Deploying the application** to devices and begin collecting custom event data. Until the application has been deployed to a device, simulator, or emulator, the custom events won't appear in Dashboard.

5. **Creating the** **event funnel** in Dashboard (see [Creating an Event Funnel](#creating-an-event-funnel)).

### Creating an event funnel

When you create an event funnel in Dashboard, you select the events you want to track, in the order that defines the process you want to track and analyze. For instance, in the following example, the user has created an event funnel named "Product Purchase" that tracks the progress of a retail customer through five basic phases: logging into the site, searching for products, reviewing product information, making a purchase, and confirming the purchase.

![CreateEventFunnel_latest](/Images/appc/download/attachments/43298693/CreateEventFunnel_latest.png)

**Note**

* An event funnel must contain at least two events

**To create an event funnel**

1. In the Analytics Dashboard, make sure your application is selected.

2. Select **Analytics** from the left navigation menu.

3. Select **Event Funnels** from the Analytics menu. Your application's current event funnels are displayed, if any, exist.

4. Click the **+** button to create a new event funnel.

5. Enter a name for your event funnel.

6. Drag two or more custom events from the left column to the right column. Enter the name of an event in the Custom Events text field to filter available events by name.

    To get custom events to appear on this list, you must build your application and trigger each event to ensure that the events are registered with the analytics engine.

7. To re-order an event, drag its reorder control up or down in the event list. Keep in mind that the order of the events you include is significant in terms of how the event funnel data is analyzed and presented.

8. Remove an event by clicking the '**X**'  next to its name.

9. Click **Save** to save the event funnel.

### Viewing event funnels

Once you've created an event funnel, you can begin analyzing the funnel results. The screenshot below shows the current results of the "Product Purchase" event funnel created above. As you can see, of all visitors to the home page, 83% of those searching for products, 67% of those who searched for products reviewed additional product information, and 10% of those who reviewed additional product information made a purchase.

![event-funnel-results_latest](/Images/appc/download/attachments/43298693/event-funnel-results_latest.png)

**To view an event funnel**

1. In the Analytics Dashboard, make sure your application is selected.

2. Click **Analytics** in the left navigation menu.

3. Click **Event Funnels** in the Analytics menu to view a list of your application's event funnels.

4. To filter data by version, environment, or custom date range, use the drop-down lists located right below the main navigation bar.

**To edit an event funnel**

1. In the Analytics Dashboard, make sure your application is selected.

2. Click **Analytics** in the left navigation menu.

3. Click **Event Funnels** in the Analytics menu to view a list of your event funnels.

4. Locate the event funnel you want to edit, then click its **Pencil** icon in the top-right corner.

5. From the edit screen you can:

    1. Move new custom events you want to track from the left column to the right column.

    2. Reorder events in the funnel.

    3. Remove events from the funnel by clicking the **×** next to the event.

    4. Rename the event funnel.

6. Click **Save** to save your changes.

**To remove an event funnel**

1. In the Analytics Dashboard, make sure your application is selected.

2. Click **Analytics** in the left navigation menu.

3. Click **Event Funnels** in the Analytics menu. This list your application's current event funnels.

4. Locate the event funnel you want to remove, then click its **Pencil** icon in the top-right corner.

5. Click **Remove** to delete the event funnel.

6. A dialog appears asking to confirm the deletion. Click **Continue**.
