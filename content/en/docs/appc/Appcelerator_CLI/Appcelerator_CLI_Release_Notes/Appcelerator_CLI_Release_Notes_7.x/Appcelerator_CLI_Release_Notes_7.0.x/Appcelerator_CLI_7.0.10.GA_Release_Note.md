{"title":"Appcelerator CLI 7.0.10.GA - 14 March 2019","weight":"50"} 

Appcelerator CLI 7.0.10.RC is a patch release that includes several improvements and bug fixes. This release also drops support for SOASTA.

As of this GA release, the previous CLI patch release is no longer supported. End of support for this version will be up to 2019-09-14 or until the next patch release. Note: major and minor releases continue to be supported according to their nominal lifetime. See [Axway Appcelerator Deprecation Policy](/docs/appc/AMPLIFY_Appcelerator_Services_Overview/Axway_Appcelerator_Deprecation_Policy/) and [Nominal Lifetimes](/docs/appc/AMPLIFY_Appcelerator_Services_Overview/Axway_Appcelerator_Product_Lifecycle/#NominalLifetimes) documents for details.

## Component versions

The following components are shipped with CLI 7.0.10:

Alloy

1.13.8

API Builder

3.2.11

Cloud CLI

2.0.12

Titanium CLI

5.1.1

Daemon

1.1.3

## Improvements

*   [ALOY-1639](https://jira.appcelerator.org/browse/ALOY-1639) - Use Matrix2D/Matrix3D instead of 2DMatrix/3DMatrix
    
    *   Deprecated 2DMatrix and 3DMatrix which is replaced by Matrix2D and Matrix3D
        
*   [ALOY-1640](https://jira.appcelerator.org/browse/ALOY-1640) - Modify <TabbedBar/> to use "Ti.UI" instead of "Ti.UI.iOS" for 8.0.0
    
    *   Parity for Android
        

## Fixed issues

*   [CLI-1342](https://jira.appcelerator.org/browse/CLI-1342) - Remove SOASTA module for SDK 8.0.0+
    
*   [CLI-1345](https://jira.appcelerator.org/browse/CLI-1345) - Running Api builder throws Cannot find module error/CLI 7.0.10 MASTER -6 &7.0.10 master-7
    
*   [CLI-1347](https://jira.appcelerator.org/browse/CLI-1347) - "componentForDownload is not defined" error when running a project
    
*   [ALOY-1637](https://jira.appcelerator.org/browse/ALOY-1637) - ES6 code frame fails when using duplicate variable declarations
    
*   [ALOY-1638](https://jira.appcelerator.org/browse/ALOY-1638) - Theme is "null" when a theme is defined in config.json
    
*   [ALOY-1641](https://jira.appcelerator.org/browse/ALOY-1641) - iOS: TabbedBar usage on lower than SDK 8 is broken
    
*   [ALOY-1644](https://jira.appcelerator.org/browse/ALOY-1644) - Selective compilation does not regenerate platform app.js on Windows