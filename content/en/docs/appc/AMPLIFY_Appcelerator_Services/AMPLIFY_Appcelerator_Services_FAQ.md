{"title":"AMPLIFY Appcelerator Services FAQ","weight":"30"} 

## Single Event Funnel in Appcelerator Analytics won't work

You must use at least two events.

## Where can I find my organization ID for Test?

You can locate your organization ID in the My Profile screen in Dashboard or inside the project's tiapp.xml file in Appcelerator Studio.

## How do I integrate Appcelerator Test with Jenkins?

See [Integrating Test with Jenkins](/docs/appc/AMPLIFY_Appcelerator_Services/AMPLIFY_Appcelerator_Services_Guide/Appcelerator_Test/Integrating_Test_with_Jenkins/) for details.

## Appcelerator Test error: Cannot open page (iOS)

See [Troubleshooting problems with Test](/docs/appc/AMPLIFY_Appcelerator_Services/AMPLIFY_Appcelerator_Services_Guide/Appcelerator_Test/Troubleshooting_problems_with_Test/#CannotOpenPage(iOS)orFailedtolaunchapp(Android)) for details on how to correct this error.

## Appcelerator Test error: Failed to launch app (Android)

See [Troubleshooting problems with Test](/docs/appc/AMPLIFY_Appcelerator_Services/AMPLIFY_Appcelerator_Services_Guide/Appcelerator_Test/Troubleshooting_problems_with_Test/#CannotOpenPage(iOS)orFailedtolaunchapp(Android)) for details on how to correct this error.

## Test dashboard does not load ("Server has encountered error. Please try again or contact support")

See [Troubleshooting problems with Test](/docs/appc/AMPLIFY_Appcelerator_Services/AMPLIFY_Appcelerator_Services_Guide/Appcelerator_Test/Troubleshooting_problems_with_Test/#Testdashboarddoesnotload(&quot;Serverhasencounterederror.Pleasetryagainorcontactsupport&quot;)) for details on how to correct this error.

## CLI Troubleshooting

### Application does not Specify a CFBundleExecutable

This error can occur when installing an iOS app bundle that has been dynamically instrumented for testing after compilation.

![error-cfbundleexec](/Images/appc/download/attachments/43298734/error-cfbundleexec.png)

As a workaround, you can "statically" instrument the Xcode project, compile the project, and then install the app bundle to the device. For steps on statically instrumenting an Xcode project, see the iOS Project example.

### Resource Not Found

If you receive the following error:

`com.appcelerator.mattwrapper.rest.RESTException: Error executing GET request! Received error code:` `404`

`{``"success"``:``false``,``"description"``:``"Resource Not Found"``,``"code"``:``404``}`

Make sure the appkey parameter is correct.

### Fails with "java.lang.OutOfMemoryError: Java heap space" when targeting an APK file

Add the \-Xmx2g option to the Java command to increase the JVM heap size.

`java -Xmx2g -jar appcelerator-test.jar -apk ~/Documents/Eclipse_Workspace/SampleProject/SampleProject.apk -androidsdk ~/opts/android-sdk/ -appkey` `"11111111-2222-3333-4444-555555555555"` `-dashboardurl https:``//platform.appcelerator.com -username user@appcelerator.com -password secret`