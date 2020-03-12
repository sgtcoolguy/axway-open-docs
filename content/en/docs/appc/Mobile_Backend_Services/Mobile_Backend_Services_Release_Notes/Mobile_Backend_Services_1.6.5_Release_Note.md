{"title":"Mobile Backend Services 1.6.5 Release Note","weight":"10"} 

## Mobile Backend Services 1.6.5 - 18 October 2019

This release of Mobile Backend Services 1.6.5 is a minor release, which includes an improvement and bug fixes.

## Improvement

*   Previously, the customer documentation had a reference to an internal Docker GitHub repository. Now, the reference to the internal GitHub repository has been removed and replaced with references to customer accessible Docker installation packages.
    

## Fixed issues

*   Previously, the export of customer data from a Mobile Backend Services application would fail when an attempt was made to export a large amount of data. Now, the export issue has been resolved and customers are able to export date from Mobile Backend Services applications even when there is a large amount of data to export.
    
*   Previously, pull requests to upload files would not pass the DEP check and failed to upload the dependency check. Now, the pull requests to upload files are successfully completed.
    
*   Previously, push notifications were not working for customer applications and they would receive the "App is not configured for Push Notification" error message while sending test notifications from Dashboard. Now, push notifications are properly configured and are working for customer applications.