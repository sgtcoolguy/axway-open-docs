{"title":"Troubleshooting Guide","weight":"40"}

This document provides information on troubleshooting Titanium SDK and Studio and information about push notification error messages.

* [Titanium SDK and Studio](#titanium-sdk-and-studio)

    * [Error enabling Cloud service for the project](#error-enabling-cloud-service-for-the-project)

* [Push notification error messages](#push-notification-error-messages)

    * [Apple Push Notification Server (APNS) errors](#apple-push-notification-server-apns-errors)

    * [Firebase Cloud Messaging (FCM) errors](#firebase-cloud-messaging-fcm-errors)

## Titanium SDK and Studio

### Error enabling Cloud service for the project

If you receive a message similar to "Error enabling Cloud service for the project" in Studio when trying to enable Cloud services for your project, the Mobile Backend Services (MBS) server may be down, or Studio is unable to connect to the MBS server. Try to enable Cloud services later.If you are still receiving this error when trying to enable Cloud services, check to see if your application was created in [https://platform.axway.com/](https://platform.axway.com/).

If the application was created, check to see if MBS keys were created for the application. To find your MBS keys, go to [https://platform.axway.com/](https://platform.axway.com/), select your application from the **Apps** drop-down list, then click **Configuration**. You should see items for **App Key**, **OAuth Consumer Key**, and **OAuth Secret**. Click the **Show** link to expand these items. Note that you need both the Development and Production version of these items. You can switch between the two by clicking the drop-down box in the top-right corner that displays either **Development** or **Production**.

If you do _not_ have MBS keys, try to enable Cloud services again at a later time.

If you do have MBS keys, manually enter the MBS key information in the tiapp.xml file. To manually enter this information:

1. Double-click your tiapp.xml file to open it in the **Editor**.

2. Click the **tiapp.xml** tab in the lower-left corner of the **Editor**.

3. Insert the following MBS property keys as children of the ti:app parent tag and replace with the application's MBS keys found earlier:

    `<``ti``:app` `xmlns:ti``=``"http://ti.appcelerator.org"``>`

    `<!-- Add these six tags and replace with your application's ArrowDB keys -->`

    `<``property`  `name``=``"acs-oauth-secret-development"`  `type``=``"string"``>OAUTH_CONSUMER_SECRET_DEV</``property``>`

    `<``property`  `name``=``"acs-oauth-key-development"`  `type``=``"string"``>OAUTH_CONSUMER_KEY_DEV</``property``>`

    `<``property`  `name``=``"acs-api-key-development"`  `type``=``"string"``>APP_KEY_DEV</``property``>`

    `<``property`  `name``=``"acs-oauth-secret-production"`  `type``=``"string"``>OAUTH_CONSUMER_SECRET_PROD</``property``>`

    `<``property`  `name``=``"acs-oauth-key-production"`  `type``=``"string"``>OAUTH_CONSUMER_KEY_PROD</``property``>`

    `<``property`  `name``=``"acs-api-key-production"`  `type``=``"string"``>APP_KEY_PROD</``property``>`

    `<!-- Add these two tags if you are using Appcelerator Studio -->`

    `<``property`  `name``=``"acs-authbase-url"`  `type``=``"string"``>``https://secure-identity.cloud.appcelerator.com``</``property``>`

    `<``property`  `name``=``"acs-base-url"`  `type``=``"string"``>``https://api.cloud.appcelerator.com``</``property``>`

    `...`

    `</``ti``:app>`

4. Save and close your tiapp.xml file.

5. Reopen your tiapp.xml file. In the **Overview** tab, it should show that Cloud services are enabled.

## Push notification error messages

The following table lists error messages reported by the MBS push notification dispatcher, which is responsible for sending push notifications to the Apple Push Notification Service (APNS) and Firebase Cloud Messaging (FCM).

Firebase Cloud Messaging (FCM) is the new version of Google Cloud Messaging (GCM). For additional information, refer to [Firebase Cloud Messaging](https://developers.google.com/cloud-messaging/concept-options).

### Apple Push Notification Server (APNS) errors

| Code | Message | Description |
| --- | --- | --- |
| 2001 | There was a problem loading or reading the keystore. | There was a problem loading the keystore (APNS certificate). Try [re-creating](/docs/appc/Titanium_SDK/Titanium_SDK_How-tos/Notification_Services/Push_Notifications/Configuring_Push_Services/) and uploading your keystore. |
| 2002 | There was a network problem communicating with APNS, such as an SSL or socket error. | Network communication between the MBS push notification dispatcher and APNS was interrupted for some reason. |
| 2003 | A certificate does not exist. | The specified [APNS push certificate](/docs/appc/Titanium_SDK/Titanium_SDK_How-tos/Notification_Services/Push_Notifications/Configuring_Push_Services/) does not exist. |
| 2004 | The certificate is disabled. | The specified [APNS push certificate](/docs/appc/Titanium_SDK/Titanium_SDK_How-tos/Notification_Services/Push_Notifications/Configuring_Push_Services/) is disabled. |
| 2005 | The payload is invalid. | The [JSON payload](#undefined) is invalid. |
| 2006 | The payload is longer than 2048 bytes. | The JSON payload is longer than 2048 bytes. You need to make the payload smaller. |
| 2007 | The certificate is revoked. | The specified [APNS push certificate](/docs/appc/Titanium_SDK/Titanium_SDK_How-tos/Notification_Services/Push_Notifications/Configuring_Push_Services/) has been revoked. You need to generate a new certificate. |
| 2008 | The certificate is expired. | The specified [APNS push certificate](/docs/appc/Titanium_SDK/Titanium_SDK_How-tos/Notification_Services/Push_Notifications/Configuring_Push_Services/) has expired. You need to generate a new certificate. |
| 2009 | The certificate is invalid. | The specified [APNS push certificate](/docs/appc/Titanium_SDK/Titanium_SDK_How-tos/Notification_Services/Push_Notifications/Configuring_Push_Services/) is invalid. You need to generate a new certificate. |
| 2010 | The socket is closed. | The socket connection between the Mobile Backend Services push dispatcher and APNS was closed. |

### Firebase Cloud Messaging (FCM) errors

Error codes in the 3000-3099 range are [FCM error codes](http://developer.android.com/reference/com/google/android/gcm/server/Constants.html). Error codes above 3100 are for custom MBS push dispatcher errors.

| Code | Message | Description |
| --- | --- | --- |
| 3001 | Too many messages were sent to a specific device. Retry sending after a while. | FCM limits the number of push messages that can be sent to a particular device over a period. Increase the period between notifications for this device. |
| 3002 | A particular message could not be sent because the FCM servers encountered an error. | FCM servers encountered an error. |
| 3003 | Bad registration\_id. The sender should remove this registration\_id. | The FCM client sent a bad [registration ID](https://developer.android.com/google/gcm/client.html#sample-register) and should re-register with FCM to obtain a new ID. This error is uncommon if you are using the [Modules.CloudPush](#!/api/Modules.CloudPush) module. |
| 3004 | The time-to-live value provided is less than zero or more than the allowed maximum. | The message's [Time to Live](http://developer.android.com/google/gcm/adv.html#ttl) (expiration date) value is invalid. This error is uncommon if you are using the [Modules.CloudPush](#!/api/Modules.CloudPush) module. |
| 3005 | The payload is longer than the maximum allowed size of 4096 bytes. | FCM limits push notification payload size to 4096 bytes; try reducing the JSON message size and sending it again. |
| 3006 | The sender\_id contained in the registration\_id does not match the sender\_id used to register with the FCM servers. | The [FCM client](https://developer.android.com/google/gcm/client.html) did not use the proper sender\_id. This error is uncommon if you are using the [Modules.CloudPush](#!/api/Modules.CloudPush) module. |
| 3007 | A collapse key is required. Include the collapse key in the request. | If you are using a custom FCM client, you need to include a [collapse key](http://developer.android.com/google/gcm/adv.html) in the request. This error is uncommon if you are using the [Modules.CloudPush](#!/api/Modules.CloudPush) module. |
| 3008 | The request was missing a registration\_id; registration\_id is required with every request. | The FCM client did not include a [registration ID](https://developer.android.com/google/gcm/client.html#sample-register) in its request. This error is uncommon if you are using the [Modules.CloudPush](#!/api/Modules.CloudPush) module. |
| 3009 | The user has uninstalled the application or turned off notifications. The sender should stop sending messages to this device and delete the registration\_id. The client needs to re-register with the FCM servers to receive notifications again. |  |
| 3010 | Too many messages sent by the sender. Retry after a while. | FCM limits the number of push notifications that can be sent by a particular sender over a given period. Increase the period between push notification send requests. |
| 3011 | A particular message could not be sent because the FCM servers were not available. | The FCM server was not available for an unknown reason. Try again later. |
| 3101 | No result retrieved from FCM Server. | The FCM server did not return a response from the push notification request. |
| 3102 | fcm\_apiKey is null. | Make sure you've [configured Mobile Backend Services push notifications](/docs/appc/Titanium_SDK/Titanium_SDK_How-tos/Notification_Services/Push_Notifications/Configuring_Push_Services/) with your API key. |
| 3103 | RegistrationId(s) is null or empty. | The FCM client provided a null or empty [registration ID](https://developer.android.com/google/gcm/client.html#sample-register). This error is uncommon if you are using the [Modules.CloudPush](#!/api/Modules.CloudPush) module. |
| 3104 | FCM internal error. | An internal error occurred with FCM. Check FCM status. |
| 3105 | The message could not be sent, or there was a JSON parsing error. | Make sure that the notification [JSON payload](#undefined) is formatted correctly. |
