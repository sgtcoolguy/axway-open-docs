{"title":"Re-enabling Test After Service Upgrade","weight":"30"} 

Enterprise Subscription Required!

This AMPLIFY Appcelerator Services feature requires an Enterprise Subscription.

Whenever there is an update to the Appcelerator Test service, you must re-enable Test on any Titanium, Android or iOS applications that you had previously enabled, as explained below.

## Re-enabling Test for Titanium Applications

Titanium developers use Studio to update the plug-in, then re-enable Test in each project's tiapp.xml file.

**To install the latest Test module and re-enable Test in a Titanium application** :

1.  In Studio select **Help > Check for Appcelerator Updates**.
    
2.  Click **Install** in the Appcelerator Updates dialog that appears.
    
3.  Once the update is complete, do the following for each Studio project you had previously Test-enabled:
    
    1.  Open the project's tiapp.xml file.
        
    2.  Click **Enable Services** in the Appcelerator Services section to re-enable Test. Once enabled, a green checkmark appears next to Test.
        

## Re-enabling Test for iOS and Android Applications

Objective-C, Swift and Java developers need to download the latest [Appcelerator-Test CLI](/docs/appc/AMPLIFY_Appcelerator_Services/AMPLIFY_Appcelerator_Platform_Services_How-tos/AMPLIFY_Appcelerator_Services_Native_SDKs/Appcelerator_Test_CLI_Reference/) and run it against their projects.

**To install the latest Appcelerator-Test CLI and re-enable Test in an Android or iOS application** :

1.  Login to the [AMPLIFY Platform](https://platform.axway.com/).
    
2.  On the Dashboard tile, select **Go to Dashboard**.
    
3.  Select your application from the Projects menu.
    
4.  On the application's **Overview** screen, click the **Services** tab.
    
5.  Click **Add Platform Services to your app** on the Services tab.
    
6.  Click the **Test** tab.
    
7.  Follow the instructions shown there to download and run the new CLI tool. Also, see the Appcelerator Test CLI Reference for details on using the utility.