{"title":"Appcelerator CLI 5.4.0.RC - 3 August 2016","weight":"60"}

Appcelerator CLI 5.4.0.RC is a minor release that includes new features, improvements, and bug fixes.

As of this release, CLI 5.3.x will not be supported six months from 5.4.0.GA's release date. See [Axway Appcelerator Deprecation Policy](/docs/appc/AMPLIFY_Appcelerator_Services_Overview/Axway_Appcelerator_Deprecation_Policy/) and [Nominal Lifetimes](/docs/appc/AMPLIFY_Appcelerator_Services_Overview/Axway_Appcelerator_Product_Lifecycle/#nominal-lifetimes) documents for details.

## Component Versions

The following components are shipped with CLI 5.4.0.Beta:

<table class="confluenceTable"><thead class=" "></thead><tfoot class=" "></tfoot><tbody class=" "><tr><td class="confluenceTd" rowspan="1" colspan="1"><p>Alloy</p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>1.9.1</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p>Arrow Builder</p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>1.8.2</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p>Arrow Cloud CLI</p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>1.2.1</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p>Titanium CLI</p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>5.0.9</p></td></tr></tbody></table>

## New Features

* [CLI-875](https://jira.appcelerator.org/browse/CLI-875) - appc use command should allow --prerelease option

    * The appc use command allows you to use prelease versions by using the \--prerelease flag

## Improvements

* [CLI-741](https://jira.appcelerator.org/browse/CLI-741) - Allow for refreshing of session without logging in again explicitly

    * APPC CLI allows for refreshing of a session without having to log in again

## Fixed Issues

* [CLI-941](https://jira.appcelerator.org/browse/CLI-941) - Running appc access get on an unpublished app won't throw correct error

* [CLI-955](https://jira.appcelerator.org/browse/CLI-955) - CLI should not tell a user to install a pre-release CLI as an update from a GA version

* [CLI-988](https://jira.appcelerator.org/browse/CLI-988) - "-o" (org-id) is not honored with appc login

* [CLI-998](https://jira.appcelerator.org/browse/CLI-998) - We are displaying an OEM vendor name in logging and should not

* [CLI-999](https://jira.appcelerator.org/browse/CLI-999) - "(node:19181) fs: re-evaluating native module sources is not supported." message appears

* [CLI-1044](https://jira.appcelerator.org/browse/CLI-1044) - CLI 5.4.0-31 can not create apps in EU region
