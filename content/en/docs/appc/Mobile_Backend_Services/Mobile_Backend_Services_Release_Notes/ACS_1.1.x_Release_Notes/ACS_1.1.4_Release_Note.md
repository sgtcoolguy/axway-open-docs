{"title":"ACS 1.1.4 - 14 August 2014","weight":"60"}

The 1.1.4 release of Appcelerator Cloud Services includes the following updates and bug fixes:

## New features

* Added a new count API to that returns the total number of objects of the specified type. This API is available to the following ACS types: [ACLs](/arrowdb/latest/#!/api/ACLs), [Chats](/arrowdb/latest/#!/api/Chats), [Checkins](/arrowdb/latest/#!/api/Checkins), [PhotoCollections](/arrowdb/latest/#!/api/PhotoCollections), [Emails](/arrowdb/latest/#!/api/Emails), [Events](/arrowdb/latest/#!/api/Events), [Files](/arrowdb/latest/#!/api/Files), [GeoFences](/arrowdb/latest/#!/api/GeoFences), [KeyValues](/arrowdb/latest/#!/api/KeyValues), [Messages](/arrowdb/latest/#!/api/Messages), [CustomObjects](/arrowdb/latest/#!/api/CustomObjects), [Photos](/arrowdb/latest/#!/api/Photos), [Places](/arrowdb/latest/#!/api/Places), [Posts](/arrowdb/latest/#!/api/Posts), [PushNotifications](/arrowdb/latest/#!/api/PushNotifications), [Reviews](/arrowdb/latest/#!/api/Reviews), [Statuses](/arrowdb/latest/#!/api/Statuses), and [Users](/arrowdb/latest/#!/api/Users).

  * For example, the following shows an example cURL request and response for the number of Photos:

    `$ curl -b cookies.txt -c cookies.txt` `"https://api.cloud.appcelerator.com/v1/photos/count.json?key=<YOUR_APP_KEY>&pretty_json=true"`

  * Example response:

    `{`

    `"meta"``: {`

    `"code"``: 200,`

    `"status"``:` `"ok"``,`

    `},`

    `"response"``: {`

    `"photos"``: 10.0`

    `}`

    `}`


## Bug fixes

* [get\_chat\_groups](/arrowdb/latest/#!/api/Chats-method-get_chat_groups) now only returns chat groups that the current user belongs to, as expected.

* [subscribe\_token](/arrowdb/latest/#!/api/PushNotifications-method-subscribe_token) now properly increases the subscribed device count, as displayed in Dashboard or My Apps.

* Queries now properly limit the number of results specified by the query [limit](/arrowdb/latest/#!/guide/search_query-section-skip-and-limit) parameter.

* Fixed an issue where valid .p12 certificates were being disabled when ACS could not make a successful connection to Apple Push Notification Service (APNS).

* Fixed an issue where calling [keyvalues.incrby](/arrowdb/latest/#!/api/KeyValues-method-incrby) or [keyvalues.append](/arrowdb/latest/#!/api/KeyValues-method-append) as an application admin on behalf of another user (by specifying the user\_id parameter) would create a new keyvalue belonging to the admin, rather than updating the one belonging to the specified user.

* Fixed an unexpected error ("Export currently in progress") when exporting application data from the My Apps web console.

* An ACS user's first\_name or last\_name fields can now be set to an empty string, as expected, as long the username field is not empty.

* Fixed an issue when assigning binary data to a keyvalue object.

* Fixed an issue with [push\_notification/notify.json](/arrowdb/latest/#!/api/PushNotifications-method-notify) where a non-admin user was able to send a geo-based notification without specifying either to\_ids or friends fields.

* Fixed an issue where creating a new [Review](/arrowdb/latest/#!/api/Reviews-method-create) for a Photo object made the reviewed photo the primary photo for the new review.

* The push notification logs in the My Apps web console now shows the correct push count for Android and IOS devices.
