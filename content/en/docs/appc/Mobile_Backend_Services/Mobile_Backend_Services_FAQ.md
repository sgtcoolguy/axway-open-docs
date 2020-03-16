{"title":"Mobile Backend Services FAQ","weight":"50"}

This document provides questions and answers for several frequently asked questions about MBS.

## Firebase push notification using Appcelerator

Firebase Cloud Messaging (FCM) is the new version of **GCM.** Please visit [https://console.firebase.google.com](https://console.firebase.google.com/).

Then create your project and use that Project ID and Web API Key as a GCM sender ID and GCM API key.

## Sending push via Firebase API key

You can import a cloud-enabled project into Firebase. Similarly, the result will be a new key is generated. The steps for this are:

1. Log into Firebase console: [https://console.firebase.google.com/](https://console.firebase.google.com/)

2. Choose **Import Google Project** from the project menu.

3. Select **Project Settings** from the gear menu

4. Select the **CLOUD MESSAGING Tab** and use the server key and sender ID.

5. Configure push service on the Dashboard by reviewing the information in [Configuring Push Services](/docs/appc/Titanium_SDK/Titanium_SDK_How-tos/Notification_Services/Push_Notifications/Configuring_Push_Services/).

Make sure your Appcelerator ID and package name are the same.

Further reading: [Generate a Google Server API Key](https://documentation.onesignal.com/docs/generate-a-google-server-api-key)

## Is GCM going to be deprecated?

We will continue to support the current version of GCM Android and iOS SDKs because we know a lot of developers are using GCM SDKs today to handle notifications and client app upgrade takes time.

## Push notification sample code

Appcelerator provided subscribed device token code with iOS 10, or later devices have some problem but part it doesn't work anymore: Ti.Platform.name == "iPhone OS"

Visit [https://gist.github.com/MotiurRahman/2cd4520727271bb60316d57032bf0028](https://gist.github.com/MotiurRahman/2cd4520727271bb60316d57032bf0028) for a working sample.

## Error enabling Cloud service for the project

If you receive a message similar to "Error enabling Cloud service for the project" in Studio when trying to enable Cloud services for your project, the Mobile Backend Services (MBS) server may be down, or Studio is unable to connect to the MBS server. Try to enable Cloud services later.

See [Troubleshooting Guide](/docs/appc/Mobile_Backend_Services/Mobile_Backend_Services_How-tos/Troubleshooting_Guide/#error-enabling-cloud-service-for-the-project) for more details.

## Push notification error messages

Apple Push and Google Cloud Messaging provide error codes for common push notification errors. See [Apple Push Notification Server errors](/docs/appc/Mobile_Backend_Services/Mobile_Backend_Services_How-tos/Troubleshooting_Guide/#apple-push-notification-server-apns-errors) and [Google Cloud Messaging errors](/docs/appc/Mobile_Backend_Services/Mobile_Backend_Services_How-tos/Troubleshooting_Guide/#GoogleCloudMessaging(GCM)errors) for more details.
