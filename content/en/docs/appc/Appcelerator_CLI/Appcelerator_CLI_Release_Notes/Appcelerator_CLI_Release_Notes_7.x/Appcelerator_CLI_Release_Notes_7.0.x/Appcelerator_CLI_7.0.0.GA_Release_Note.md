{"title":"Appcelerator CLI 7.0.0.GA - 8 December 2017","weight":"240"} 

# Appcelerator CLI 7.0.0.GA - 8 December 2017

Appcelerator CLI 7.0.0.GA is a major release that includes new features, improvements, and bug fixes.

As of this release, CLI 6.x will not be supported one calendar year from 7.0.0.GA's release date. See [Axway Appcelerator Deprecation Policy](/docs/appc/AMPLIFY_Appcelerator_Services_Overview/Axway_Appcelerator_Deprecation_Policy/) and [Nominal Lifetimes](/docs/appc/AMPLIFY_Appcelerator_Services_Overview/Axway_Appcelerator_Product_Lifecycle/#NominalLifetimes) documents for details.

## Component versions

The following components are shipped with CLI 7.0.0:

Alloy

1.10.10 - 1.10.9

API Builder

3.0.0

Cloud CLI

2.0.8

Titanium CLI

5.0.14

## Improvements

*   [CLI-628](https://jira.appcelerator.org/browse/CLI-628) - Improve Offline with Remote Verbiage
    
    *   Improved verbiage for offline devices
        
*   [CLI-1130](https://jira.appcelerator.org/browse/CLI-1130) - Use node.js os.homedir to get homedir
    
    *   Improved how CLI retrieves home directory
        
*   [CLI-1251](https://jira.appcelerator.org/browse/CLI-1251) - Remove download of hyperloop module for SDKs with pre-packaged module
    
    *   Users are no longer prompted to download the Hyperloop module as it has been integrated into the SDK core
        
*   [CLI-1272](https://jira.appcelerator.org/browse/CLI-1272) - Alloy: remove 'mobileweb' from config template
    
    *   remove mobileweb from config template
        
*   [CLI-1275](https://jira.appcelerator.org/browse/CLI-1275) - Include appc-platform-sdk 3.\*
    
    *   Updated appc-platform-sdk to v3.0.1
        
*   [CLI-1277](https://jira.appcelerator.org/browse/CLI-1277) - cli should replace "tar.gz" as it is deprecated
    
    *   Replaced the unsupported tar.gz format with tar
        
*   [CLI-1279](https://jira.appcelerator.org/browse/CLI-1279) - Include API Builder 3.\*
    
    *   CLI 7.0.0 include API Builder 3.x.x
        
*   [CLI-1283](https://jira.appcelerator.org/browse/CLI-1283) - appc use pre-release versions are not listed numerically
    
    *   Improved pre-release versions so they appear in the correct numerical order
        
*   [CLI-1285](https://jira.appcelerator.org/browse/CLI-1285) - "appc use" must stop the daemon, if present, prior to switching core
    
    *   Added feature to stop the Daemon prior to switching to core
        
*   [CLI-1288](https://jira.appcelerator.org/browse/CLI-1288) - "appc appcd dump" should not display the banner
    
    *   Added feature to suppress the banner when you execute any appc appcd
        

## Fixed issues

*   [CLI-1266](https://jira.appcelerator.org/browse/CLI-1266) - async function without callback warning when downloading hyperloop
    
*   [CLI-1280](https://jira.appcelerator.org/browse/CLI-1280) - CLI: Cannot create projects when using 7.0.0-master.11
    
*   [CLI-1286](https://jira.appcelerator.org/browse/CLI-1286) - install: CLI should enforce minimum node version of 8.0.0
    
*   [CLI-1287](https://jira.appcelerator.org/browse/CLI-1287) - CLI Core 7.0.0-master.34 fails to install "ioslib/node-ios-device" with error