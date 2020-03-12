{"title":"Appcelerator CLI 7.0.8.GA - 28 November 2018","weight":"90"}

Appcelerator CLI 7.0.8.GA is a patch release that includes several improvements and bug fixes.

As of this GA release, the previous CLI patch release is no longer supported. End of support for this version will be up to 2019-05-27 or until the next patch release. Note: major and minor releases continue to be supported according to their nominal lifetime. See [Axway Appcelerator Deprecation Policy](/docs/appc/AMPLIFY_Appcelerator_Services_Overview/Axway_Appcelerator_Deprecation_Policy/) and [Nominal Lifetimes](/docs/appc/AMPLIFY_Appcelerator_Services_Overview/Axway_Appcelerator_Product_Lifecycle/#NominalLifetimes) documents for details.

## Component versions

The following components are shipped with CLI 7.0.8:

Alloy

1.13.4

API Builder

3.2.7

Cloud CLI

2.0.11

Titanium CLI

5.1.1

Daemon

1.1.3

## Improvements

* [ALOY-1615](https://jira.appcelerator.org/browse/ALOY-1615) - Audioplayer cannot be created from Alloy without specifying ns property

  * Audioplayer can now be created without specifying ns property

* [ALOY-1621](https://jira.appcelerator.org/browse/ALOY-1621) - Move NavigationWindow API from Ti.UI.iOS to Ti.UI (parity)

  * Moved Ti.UI.iOS.NavigationWindow to Ti.UI namespace for parity with Android and Windows

* [ALOY-1631](https://jira.appcelerator.org/browse/ALOY-1631) - Define theme from CLI

  * Added theme CLI parameter

* [CLI-1203](https://jira.appcelerator.org/browse/CLI-1203) - Emojis should be removed from Appc CLI NPM

  * Removed emojis from Appc CLI

* [CLI-1319](https://jira.appcelerator.org/browse/CLI-1319) - Reduce number of vulnerabilities found by npm audit

  * Reduced the number of warnings from npm audit


## Fixed issues

* [ALOY-1620](https://jira.appcelerator.org/browse/ALOY-1620) - Fix new Buffer deprecation warnings

* [ALOY-1626](https://jira.appcelerator.org/browse/ALOY-1626) - Alloy: Missing plugins/ directory causes cloned app-projects to fail

* [ALOY-1627](https://jira.appcelerator.org/browse/ALOY-1627) - Breakpoints not working on alloy apps

* [ALOY-1636](https://jira.appcelerator.org/browse/ALOY-1636) - App fails to build on Android if a custom NavigationWindow tag is used

* [CLI-1321](https://jira.appcelerator.org/browse/CLI-1321) - Hyperloop: Windows platform is not added to tiapp.xml

* [CLI-1326](https://jira.appcelerator.org/browse/CLI-1326) - Fix tar extraction method

* [CLI-1328](https://jira.appcelerator.org/browse/CLI-1328) - AppC CLI --no-prompt flag broken
