{"title":"ACS 1.1.7 - 05 Jan 2015","weight":"30"}

## New features, improvements, and changes

* **Photo resizing** — By default, ACS no longer automatically resizes photo uploads. To resize photos upon upload, include the photo\_sizes\[<size>\] parameter in the request. See [Photo Uploading & Resizing](/arrowdb/latest/#!/guide/photosizes) for details.

* **Default JSON response depth** — If not specified in the request, the default value for the response\_json\_depth parameter for ACS method calls is now **1**. For applications created prior to ACS 1.1.7, the default value for response\_json\_depth is still **3**. Valid values are between 1-8.

  A higher response\_json\_depth value can reduce the number of API calls your application makes to retrieve related or dependent objects. It can also increase the size of the JSON response payload and the server's response time.

* **Filtering of unauthorized results** — In prior ACS releases, if a query request matched objects whose ACL settings did not allow access to the current user, the response would include "placeholder" records that indicate the permissions error. In applications created with ACS 1.1.7 and later, query objects the current user is not allowed to view are not included in the response at all.


## Bug fixes

* Fixed internal server error when querying a user by their geographic coordinates.

* Fixed internal error when calling messages/show.json when providing a deleted message ID.

* Fixed internal server error when calling users/show with an invalid or missing session ID.

* Fixed issue with updating/deleting ACS object with custom ACL permission.

* Fixed error when configuring SMTP settings for Office 365.

* Fixed error that occurred when updating the primary photo for an ACS object.

* Fixed issue that occurred after deleting application data in the web console that caused changes to the application settings to fail.

* Fixed issue with Cloud API logs not appearing in Dashboard.

* Fixed HTTP 500 error when calling keyvalues/append.json.

* Fixed issue uploading photos using the community web console.

* Attempting to access an ACS object whose ACL does allow access by the current user now returns an HTTP 401 error instead of 403.

* Fixed an issue with notification emails not being sent when an error with an iOS push certificate was encountered.

* Fixed 500 error in the community web console when browsing Place objects.

* Deleting a review of an object now properly updates the review count for that object.

* Querying objects with selectors on relational fields now works as expected.
