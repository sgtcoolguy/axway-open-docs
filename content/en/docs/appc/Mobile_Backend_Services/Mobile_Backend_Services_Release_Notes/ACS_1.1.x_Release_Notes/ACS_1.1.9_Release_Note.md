{"title":"ACS 1.1.9 - 05 March 2015","weight":"20"} 

# ACS 1.1.9 - 05 March 2015

## New features, improvements, and changes

*   **ACL queries** — In prior ACS releases, any user could query ACLs created by another user. In applications created with ACS 1.1.9 and later, a user can only query ACLs they create, while an application admin can query ACLs for any arbitrary user by specifying the user\_id field.
    
*   **Send push notifications to multiple push channels** — The Push Notifications API now supports sending push notifications to multiple push channels. Simply comma-separate the list of channels you want to send the notification to. Due to this change, push channel names cannot contain a comma.
    
*   **user\_id field renamed to sudo\_id for admin operations** — The user\_id field, which was used to indicate the user that an application administrator could perform an ACS API call on behalf of, was renamed to the sudo\_id field. For details, see [Admin Access-Perform ACS API Calls on Behalf of Another User](/docs/appc/Mobile_Backend_Services/Mobile_Backend_Services_Guide/Admin_Access/).
    

## Bug fix

*   Fixed an issue where a delayed job, such as exporting a large data set, would exit silently.
    
*   Fixed pagination on push channel queries. Previously, push channel query results would not be correctly paginated.