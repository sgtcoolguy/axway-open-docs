{"title":"ACS 2013 7 November Release Note","weight":"30"}

This update includes the following bug fixes and enhancements:

* Add ability to set an expiration date for push notifications with the expire\_after\_seconds parameter. See the options parameter for [push\_notification/notify.json](/arrowdb/latest/#!/api/PushNotifications-method-notify) and [push\_notification/notify\_token.json](/arrowdb/latest/#!/api/PushNotifications-method-notify_tokens).

* Add ability to schedule push notifications to be sent at specific times and intervals. This feature is only available to Enterprise customers. See [PushSchedules](/arrowdb/latest/#!/api/PushSchedules).

* Changed PushNotification API to use android as the push notification type for either MQTT or GCM. After you have configured the ACS web console for either MQTT or GCM, the ACS server automatically sends the push notification to the correct service. Previously, you had to specify either android for MQTT or gcm for GCM.

* Fixed an issue where a currently logged in user could not create a new user.
