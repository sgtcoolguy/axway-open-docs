{"title":"Appcelerator CLI 6.3.0.RC - 17 October 2017","weight":"20"}

Appcelerator CLI 6.3.0.RC is a minor release that includes new features, improvements, and bug fixes.

As of this release, CLI 6.2.x will not be supported six months from 6.3.0.GA's release date. See [Axway Appcelerator Deprecation Policy](/docs/appc/AMPLIFY_Appcelerator_Services_Overview/Axway_Appcelerator_Deprecation_Policy/) and [Nominal Lifetimes](/docs/appc/AMPLIFY_Appcelerator_Services_Overview/Axway_Appcelerator_Product_Lifecycle/#NominalLifetimes) documents for details.

## Component versions

The following components are shipped with CLI 6.3.0.RC:

Alloy

1.10.5

Arrow Builder

2.0.2

Arrow Cloud CLI

2.0.7

Titanium CLI

5.0.14

## New features

* [CLI-1069](https://jira.appcelerator.org/browse/CLI-1069) - Install hyperloop module directly through CLI command

  * Added support to install Hyperloop module

* [CLI-1250](https://jira.appcelerator.org/browse/CLI-1250) - Add support for allowing a proxy pac file to be specified in configuration

  * Added support for proxy pac file support


## Improvements

* [CLI-717](https://jira.appcelerator.org/browse/CLI-717) - Improve feedback when creating a module

  * Updated the ti create command to update the logging.txt file when building a module

* [CLI-1180](https://jira.appcelerator.org/browse/CLI-1180) - CLI rebuild check should determine if a rebuild is needed from the modules version property in node

  * Updated the CLI rebuild service to prevent unnecessary module rebuilds

* [CLI-1215](https://jira.appcelerator.org/browse/CLI-1215) - appc-install improve subprocess npm rebuild

  * Improved appc-install process to help prevent buffer overflow

* [CLI-1232](https://jira.appcelerator.org/browse/CLI-1232) - Update descriptions in appc cloud -help (ACS CLI)

  * Renamed some of the descriptions in the ACS CLI help to refer to new naming (API Runtime)


## Fixed issues

* [CLI-861](https://jira.appcelerator.org/browse/CLI-861) - The "--output" flag does not work with "appc use" command

* [CLI-931](https://jira.appcelerator.org/browse/CLI-931) - Alloy/Titanium via Unified CLI exits with code 0 while child process exits with 1

* [CLI-1176](https://jira.appcelerator.org/browse/CLI-1176) - appc -v with no cores installed throws TypeError
