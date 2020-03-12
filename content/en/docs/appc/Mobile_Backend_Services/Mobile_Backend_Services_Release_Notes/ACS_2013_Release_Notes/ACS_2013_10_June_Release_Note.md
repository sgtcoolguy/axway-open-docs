{"title":"ACS 2013 10 June Release Note","weight":"70"} 

## Fixed issues and enhancements

This update includes the following bug fixes and enhancements:

*   Removed dependency between push notifications, and device and user registrations. Users are no longer required to have an ACS account to receive push notifications.
    
*   Fixed an issue where using special characters cause the query to fail.
    
*   Website: Fixed an issue viewing relational field objects. Relational field objects were being displayed as objects and not ID strings.
    
*   Website: Fixed an issue viewing custom objects. Some custom objects could not be viewed in the web interface.
    
*   Website: Fixed an issue with SMTP settings. If a TLS value was specified, it was not properly checked.
    

## Future behavior changes

In a future release, currently scheduled in a few months, the following changes are being made to user sessions and geo query.

### Application user session expiration

An application user session never expires today. We are introducing a policy of expiring and removing sessions that have been inactive for six months.

If your application logins a user and saves the session\_id, normally stored in a cookie, every time it makes a REST call to ACS using the same session\_id, the expiry clock is reset and the user gets another six months. As long as the ACS user is actively using the same session\_id within six months, there is no impact on your application and currently logged in user. If an application user is completely inactive for six months or more, this user session is removed and any subsequent ACS call that requires user login such as create.json, update.json and remove.json will get a 404 error. We recommend your application to handle an invalid user session error and prompt a login screen for the user to log in again.

### Geo query

ACS currently supports MongoDB’s [$nearSphere](http://docs.mongodb.org/manual/reference/operator/nearSphere/) geo query. Geo query requires a field to be indexed with a geo index. The ACS fields you can perform $nearSphere on are lnglat (pre-defined location data and only available in [Places](/arrowdb/latest/#!/api/Places) and [Events](/arrowdb/latest/#!/api/Places)) and coordinates (list of custom defined location data and available in all objects). It implies that Places and Events have two geo indexes in the same collection and that prevents us from supporting the [$geoNear](http://docs.mongodb.org/manual/reference/command/geoNear/) operation that is more powerful than $nearSphere. We will consolidate the lnglat value with the coordinates values and remove geo index on the lnglat field.

For Events and Places, even if you never explicitly copied the lnglat value to coordinates, lnglat appears as the first element of coordinates. Performing $nearSphere on the coordinates field returns a match if it matches the lnglat value. $nearSphere query on lnglat or coordinates continues to work as before.