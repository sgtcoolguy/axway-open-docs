{"title":"Appcelerator CLI 6.2.0.GA - 13 April 2017","weight":"90"}

Appcelerator CLI 6.2.0.GA is a minor release that includes seven bug fixes.

As of this release, CLI 6.1.x will not be supported six months from 6.2.0.GA's release date. See [Axway Appcelerator Deprecation Policy](/docs/appc/AMPLIFY_Appcelerator_Services_Overview/Axway_Appcelerator_Deprecation_Policy/) and [Nominal Lifetimes](/docs/appc/AMPLIFY_Appcelerator_Services_Overview/Axway_Appcelerator_Product_Lifecycle/#NominalLifetimes) documents for details.

## Component versions

The following components are shipped with CLI 6.2.0.GA:

Alloy

1.9.11

Arrow Builder

2.0.3

Arrow Cloud CLI

2.0.4

Titanium CLI

5.0.12

## Fixed issues

* [CLI-1031](https://jira.appcelerator.org/browse/CLI-1031) - Windows: Node process is not killed when you use ctrl+c

* [CLI-1107](https://jira.appcelerator.org/browse/CLI-1107) - deprecated minimatch. Please update to minimatch 3.0.2 or higher to avoid a RegExp DoS issue

* [CLI-1166](https://jira.appcelerator.org/browse/CLI-1166) - Correct NSP errors in appc-cli-titanium

* [CLI-1169](https://jira.appcelerator.org/browse/CLI-1169) - TypeError: Data must be a string or a buffer thrown when running commands if sid is undefined in config

* [CLI-1171](https://jira.appcelerator.org/browse/CLI-1171) - cannot find module session

* [CLI-1173](https://jira.appcelerator.org/browse/CLI-1173) - Error: Error attempting to login to Arrow Cloud

* [CLI-1174](https://jira.appcelerator.org/browse/CLI-1174) - Bad reference to session lib in install plugin
