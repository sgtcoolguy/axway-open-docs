{"title":"ACS 1.1.3 - 17 July 2014","weight":"70"} 

# ACS 1.1.3 - 17 July 2014

The 1.1.3 release of Appcelerator Cloud Services includes the following fixes and features:

## New features

*   Add ability to query for all ACS objects a user liked. See the [Likes.query](/arrowdb/latest/#!/api/Likes-method-query) method.
    
*   Add ability to create a Files object by using a URL to access the file to upload. See the [Files.create](/arrowdb/latest/#!/api/Files-method-create) method.
    
*   Add a pretty\_json field to all method requests to enable or disable prettifying JSON response data. JSON pretty print is disabled by default.
    

## Bug fixes

*   Fixed an issue with sending ACS request from Titanium Mobile Web applications.
    
*   Fixed an issue where tags were not being stored for Events objects.
    
*   Fixed an issue where using the expire\_after\_seconds field with the PushNotifications notify\_token method would return an error.
    
*   Fixed an issue with the ACS web console where SMTP settings were not saved when switching Test mode off.
    
*   Fixed an issue where updating a relation object for a Places object was not being updated.
    
*   Fixed an issue where the application fails to unregister from push notifications when the application is uninstalled.
    
*   Fixed an issue on the Cloud Dashboard where the Storage statistic was not being displayed.
    
*   Fixed an issue on the Cloud Dashboard when editing a Statuses object. The Places object associated with the Statuses object was not updated.