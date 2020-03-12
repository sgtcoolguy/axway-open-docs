{"title":"ACS 1.1.1 - 16 May 2014","weight":"80"} 

# ACS 1.1.1 - 16 May 2014

The 1.1.1 release of Appcelerator Cloud Services includes the following fixes and features:

## New features

*   When calling an ACS object's query or show methods you can include a new parameter called show\_user\_like. If the current user has liked the object being queried or shown, the JSON response contains "current\_user\_liked":true. See the [Checkins.query](/arrowdb/latest/#!/api/Checkins-method-query) and [Checkins.show](/arrowdb/latest/#!/api/Checkins-method-show) REST API examples for examples.
    
*   ACS now uses yajl-ruby to generate JSON responses. YAJL is faster than the previous Hash.to\_json implementation.
    
*   ACS now supports SSL uploads for File and Photo objects.
    

## Bug fixes

*   Fixed an Android issue with UTF-8 encoded characters not being displayed properly in push notifications.
    
*   Fixed an issue where an application administrator was unable to check ACLs for a regular user.