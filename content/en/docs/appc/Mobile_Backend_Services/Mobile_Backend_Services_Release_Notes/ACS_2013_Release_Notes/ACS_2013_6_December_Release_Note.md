{"title":"ACS 2013 6 December Release Note","weight":"20"}

This update includes the following bug fixes and enhancements:

* Add ability to increment or decrement the badge value when sending a push notification. See the "Badge" section in [PushNotifications](/arrowdb/latest/#!/api/PushNotifications).

* Add ability to use a query to send push notifications to specific users. See the where parameter in [push\_notification/notify.json](/arrowdb/latest/#!/api/PushNotifications-method-notify).

* Add support for admin batch delete operations. See the "Admin Batch Delete" section in [Admin Access](/docs/appc/Mobile_Backend_Services/Mobile_Backend_Services_Guide/Admin_Access/).

* Change admin operation to send a push notification to all users. Set the to\_ids parameter to everyone for the push\_notification/notify.json method. Only new applications need to use this mechanism. Old applications made prior to this release can continue not to specify to\_ids. You do not need to set this parameter in the web interface.

* Add support for application admin to send push notifications to all users with the push\_notification/notify\_tokens.json method. Set the to\_tokens parameter to everyone. Previously, you could not send push notifications to all users with this method.
