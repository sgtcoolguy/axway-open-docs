{"title":"Appcelerator CLI 6.0.0.Beta - 18 October 2016","weight":"130"} 

# Appcelerator CLI 6.0.0.Beta - 18 October 2016

Appcelerator CLI 6.0.0.Beta is a patch release that includes several improvements and bug fixes.

As of this release, CLI 5.x will not be supported one calendar year from 6.0.0.GA's release date. See [Axway Appcelerator Deprecation Policy](/docs/appc/AMPLIFY_Appcelerator_Services_Overview/Axway_Appcelerator_Deprecation_Policy/) and [Nominal Lifetimes](/docs/appc/AMPLIFY_Appcelerator_Services_Overview/Axway_Appcelerator_Product_Lifecycle/#NominalLifetimes) documents for details.

## Component versions

The following components are shipped with CLI 6.0.0.Beta:

Alloy

1.9.3

Arrow Builder

1.8.9

Arrow Cloud CLI

1.2.1

Titanium CLI

5.0.10

## Improvements

*   [CLI-1035](https://jira.appcelerator.org/browse/CLI-1035) - Update appc-app-preview-cli-hook to latest version
    
    *   Improved logging message for appc-app-preview-cli-hook
        
*   [CLI-1046](https://jira.appcelerator.org/browse/CLI-1046) - Getting the correct module versions from dashboard
    
    *   The CLI pulls SDK compatible module versions
        
*   [CLI-1106](https://jira.appcelerator.org/browse/CLI-1106) - Improve speed of extracting modules on Windows
    
    *   Decreased extraction time for Windows modules
        
*   [CLI-1115](https://jira.appcelerator.org/browse/CLI-1115) - Set Node 4.x as minimum supported version
    
    *   Set Node 4.X as the minimum supported version
        

## Fixed issues

*   [CLI-1002](https://jira.appcelerator.org/browse/CLI-1002) - If you pass "--help" or "-h" flag to "appc ti", then "Cannot read property 'match' of undefined" error is returned
    
*   [CLI-1003](https://jira.appcelerator.org/browse/CLI-1003) - If you run "appc setup" with the help flag, then "appc setup" will try to find/download the latest core first
    
*   [CLI-1024](https://jira.appcelerator.org/browse/CLI-1024) - ti info returned the invalid json output
    
*   [CLI-1044](https://jira.appcelerator.org/browse/CLI-1044) - CLI 5.4.0-31 can not create apps in EU region
    
*   [CLI-1054](https://jira.appcelerator.org/browse/CLI-1054) - Set connection timeout for appc use command
    
*   [CLI-1071](https://jira.appcelerator.org/browse/CLI-1071) - Building with an invalidated session does not prompt for login and throws error
    
*   [CLI-1077](https://jira.appcelerator.org/browse/CLI-1077) - CLI outputting non-JSON warning to Studio
    
*   [CLI-1081](https://jira.appcelerator.org/browse/CLI-1081) - Modules update failed with Error: Invalid URI
    
*   [CLI-1090](https://jira.appcelerator.org/browse/CLI-1090) - update-notifier still getting installed
    
*   [CLI-1092](https://jira.appcelerator.org/browse/CLI-1092) - Error 'Cannot read property 'replace' of undefined' when creating an app without Test in an enterprise org
    
*   [CLI-1099](https://jira.appcelerator.org/browse/CLI-1099) - appc login error when specify arrowcloud url without protocol
    
*   [CLI-1122](https://jira.appcelerator.org/browse/CLI-1122) - Hyperloop is downloaded every time lastUpdateCheckTiDownloads expires on Windows