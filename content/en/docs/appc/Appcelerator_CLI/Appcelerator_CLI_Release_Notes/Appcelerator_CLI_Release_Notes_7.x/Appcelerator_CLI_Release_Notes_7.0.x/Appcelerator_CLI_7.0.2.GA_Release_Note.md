{"title":"Appcelerator CLI 7.0.2.GA - 9 February 2018","weight":"200"} 

# Appcelerator CLI 7.0.2.GA - 9 February 2018

Appcelerator CLI 7.0.2.GA is a patch release that includes several improvements and bug fixes.

As of this GA release, the previous CLI patch release is no longer supported. Note: major and minor releases continue to be supported according to their nominal lifetime. See [Axway Appcelerator Deprecation Policy](/docs/appc/AMPLIFY_Appcelerator_Services_Overview/Axway_Appcelerator_Deprecation_Policy/) and [Nominal Lifetimes](/docs/appc/AMPLIFY_Appcelerator_Services_Overview/Axway_Appcelerator_Product_Lifecycle/#NominalLifetimes) documents for details.

## Component versions

The following components are shipped with CLI 7.0.2:

Alloy

1.10.12

API Builder

3.0.0

Cloud CLI

2.0.8

Titanium CLI

5.0.14

## Improvements

*   [ALOY-1534](https://jira.appcelerator.org/browse/ALOY-1534) - Add support for Backbone 1.3.3 and Underscore 1.8.3
    
    *   Added support for Backbone 1.3.3 and Underscore 1.8.3
        
*   [ALOY-1557](https://jira.appcelerator.org/browse/ALOY-1557) - Alloy: Keep Changelog up to date
    
    *   Continued updating the Changelog at [https://github.com/appcelerator/alloy/blob/master/CHANGELOG.md](https://github.com/appcelerator/alloy/blob/master/CHANGELOG.md)
        
*   [ALOY-1592](https://jira.appcelerator.org/browse/ALOY-1592) - Builtins: Reimplement measurement by convertUnits
    
    *   Re-implemented measurement by convertUnits
        
*   [ALOY-1597](https://jira.appcelerator.org/browse/ALOY-1597) - Use babel-code-frame to provide context when failing to parse code
    
    *   Used babel-code-frame to provide better parsing error messaging
        

## Fixed issues

*   [ALOY-1528](https://jira.appcelerator.org/browse/ALOY-1528) - getWidgetDirectories does not respect theme config.json
    
*   [ALOY-1596](https://jira.appcelerator.org/browse/ALOY-1596) - Mobileweb assets copied on alloy new
    
*   [CLI-939](https://jira.appcelerator.org/browse/CLI-939) - Fsevents failed to install
    
*   [CLI-972](https://jira.appcelerator.org/browse/CLI-972) - proxyServer not working when building for the first time on CLI
    
*   [CLI-1294](https://jira.appcelerator.org/browse/CLI-1294) - registry.handleResponse does not handle the code returned from a platform call
    
*   [CLI-1303](https://jira.appcelerator.org/browse/CLI-1303) - appc use does not select version after install on Windows