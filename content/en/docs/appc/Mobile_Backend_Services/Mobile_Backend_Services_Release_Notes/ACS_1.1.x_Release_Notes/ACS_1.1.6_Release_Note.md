{"title":"ACS 1.1.6 - 29 October 2014","weight":"40"}

Appcelerator Cloud Services version 1.1.6 contains the following new features, bug fixes, and improvements.

## New features

* With respect to ACS query operations, starting with ACS 1.1.6, we have made the following changes:

    * Skip is limited to 0-4999; as a result, you can not skip beyond 5000 records.

    * If the query includes count=true, the query response's meta object will contain a count field whose value is the total number of objects that matched the query criteria. If the query matches more than 5000 objects, the count field will contain the value "5000+". If your query result set includes more than 5000 records, you should perform range-based queries for pagination as discussed in [Query Pagination](/docs/appc/Mobile_Backend_Services/Mobile_Backend_Services_Guide/Search_and_Query_APIs/).

* Increased the size limit of iOS [push notification payloads](/arrowdb/latest/#!/api/PushPayload) to 2048KB.

* Added support for the category field in push notifications to support [interactive notifications](/docs/appc/Titanium_SDK/Titanium_SDK_How-tos/Notification_Services/iOS_Interactive_Notifications/) on iOS 8 devices.

## Bug fixes and improvements

* Fixed errors that occurred in the Community web console when creating, editing, updating, or deleting application users.

* The total photo count for an application now properly updates when adding or removing an object's primary photo, such as [Places.photo](/arrowdb/latest/#!/api/Places-property-photo) or [Users.photo](/arrowdb/latest/#!/api/Users-property-photo).
