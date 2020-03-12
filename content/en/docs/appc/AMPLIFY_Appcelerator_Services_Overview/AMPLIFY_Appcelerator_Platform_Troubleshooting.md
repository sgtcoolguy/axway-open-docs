{"title":"AMPLIFY Appcelerator Platform Troubleshooting","weight":"40"}

* [Review the troubleshooting guides](#Reviewthetroubleshootingguides)

* [Common issues](#Commonissues)

  * [Dashboard sent an authorization token, but I did not receive one](#Dashboardsentanauthorizationtoken,butIdidnotreceiveone)

  * [Appcelerator updates in Studio hang or freeze, or cannot build for Android or iOS after updating from Studio](#AppceleratorupdatesinStudiohangorfreeze,orcannotbuildforAndroidoriOSafterupdatingfromStudio)

* [Tips](#Tips)

  * [Turn off LiveView](#TurnoffLiveView)


## Review the troubleshooting guides

For general installation issues, see [Installation Troubleshooting](/docs/appc/Titanium_SDK/Titanium_SDK_Getting_Started/Installation_and_Configuration/Installation_Troubleshooting/).

For in-depth troubleshooting information about specific Appcelerator components, see the following articles:

* **Alloy**: [Alloy Debugging and Troubleshooting](/docs/appc/Alloy_Framework/Alloy_How-tos/Alloy_Debugging_and_Troubleshooting/)

* **Appcelerator CLI**: [Appcelerator CLI Troubleshooting](/docs/appc/Appcelerator_CLI/Appcelerator_CLI_Guide/Appcelerator_CLI_Troubleshooting/)

* **Appcelerator Studio**: [Studio Troubleshooting](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Studio_Troubleshooting/)

* **Appcelerator Test**: [Troubleshooting problems with Test](#undefined)

* **AMPLIFY Runtime Services**: [AMPLIFY Runtime Services Troubleshooting](/docs/appc/AMPLIFY_Runtime_Services/AMPLIFY_Runtime_Services_Guide/AMPLIFY_Runtime_Services_Troubleshooting/)

* **Mobile Backend Services**: [Mobile Backend Services Troubleshooting Guide](/arrowdb/latest/#!/guide/troubleshooting)


## Common issues

### Dashboard sent an authorization token, but I did not receive one

If you are an enterprise AMPLIFY Appcelerator Services user, submit a ticket in the Support portal.

For all other users, send an e-mail to [support@appcelerator.com](mailto:support@appcelerator.com).

### Appcelerator updates in Studio hang or freeze, or cannot build for Android or iOS after updating from Studio

Close Studio and perform an update using the Appcelerator CLI.

`[sudo] npm install -g appcelerator`

`appc setup`

Start Studio after the update completes.

## Tips

### Turn off LiveView

LiveView may conflict with other applications or tooling components. The following are known issues if LiveView is active:

* If you are debugging, the debugger may not suspend execution when breakpoints are encountered if LiveView is turned on.

* On iOS, the application may not be able to retrieve a device token, which is needed to subscribe to push notifications.
