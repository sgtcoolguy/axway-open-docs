{"title":"Appcelerator CLI 6.2.3.GA - 3 August 2017","weight":"50"} 

Appcelerator CLI 6.2.3.GA is a patch release that includes one improvement and three bug fixes.

As of this GA release, the previous CLI patch release is no longer supported. Note: major and minor releases continue to be supported according to their nominal lifetime. See [Axway Appcelerator Deprecation Policy](/docs/appc/AMPLIFY_Appcelerator_Services_Overview/Axway_Appcelerator_Deprecation_Policy/) and [Nominal Lifetimes](/docs/appc/AMPLIFY_Appcelerator_Services_Overview/Axway_Appcelerator_Product_Lifecycle/#NominalLifetimes) documents for details.

## Component versions

The following components are shipped with CLI 6.2.3.GA:

Alloy

1.9.13

API Builder

2.0.2

Arrow Cloud CLI

2.0.5

Titanium CLI

5.0.14

## Improvements

*   [CLI-1236](https://jira.appcelerator.org/browse/CLI-1236) - Trim any spaces from auth code entered for two-factor verification
    
    *   Added feature that trims whitespace character from authentication verification
        

## Fixed issues

*   [CLI-1017](https://jira.appcelerator.org/browse/CLI-1017) - An error is returned when packaging after using appc switch
    
*   [CLI-1117](https://jira.appcelerator.org/browse/CLI-1117) - checkSession endpoint is hit twice when building
    
*   [CLI-1205](https://jira.appcelerator.org/browse/CLI-1205) - Support Appc unpublish specific version