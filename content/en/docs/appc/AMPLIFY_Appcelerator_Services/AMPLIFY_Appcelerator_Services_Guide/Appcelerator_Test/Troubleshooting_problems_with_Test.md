{"title":"Troubleshooting problems with Test","weight":"60"} 

# Troubleshooting problems with Test

Enterprise Subscription Required!

This AMPLIFY Appcelerator Services feature requires an Enterprise Subscription.

This page lists common problems and errors and you may encounter using Appcelerator Test.

*   [TouchTest Agent errors](#TouchTestAgenterrors)
    
    *   [Cannot Open Page (iOS) or Failed to launch app (Android)](#CannotOpenPage(iOS)orFailedtolaunchapp(Android))
        
*   [Dashboard errors](#Dashboarderrors)
    
    *   [Test dashboard does not load ("Server has encountered an error. Please try again or contact support")](#Testdashboarddoesnotload("Serverhasencounteredanerror.Pleasetryagainorcontactsupport"))
        

## TouchTest Agent errors

### Cannot Open Page (iOS) or Failed to launch app (Android)

If you get one of these errors when you start a clip recording or playing back a composition, it can mean one of the following:

*   You selected the wrong target application when starting a recording.
    
*   The application is not installed on the device.
    

![image2014-3-19_15_53_25](/Images/appc/download/attachments/43298705/image2014-3-19_15_53_25.png) ![image2014-3-19_15_55_19](/Images/appc/download/attachments/43298705/image2014-3-19_15_55_19.png)

First, verify that the test application is installed on the test device; if not, use Studio to re-install the app. Next, make sure you are selecting the correct application in the **Choose a Device Agent and Mobile App** dialog.

![image2014-3-19_16_3_12](/Images/appc/download/attachments/43298705/image2014-3-19_16_3_12.png)

## Dashboard errors

### Test dashboard does not load ("Server has encountered an error. Please try again or contact support")

If you changed your password on the Test page, your Test password is out of sync with your Dashboard password. To fix this issue, change the password on the Test page back to your Dashboard password.

**To reset your Test password to match your Appcelerator Dashboard password**:

1.  Open the [Soasta CloudTest](http://appctest-2.appcelerator.com/concerto/) page and log in. (Soasta is the underlying test automation service that enables Appcelerator Test.)
    
2.  In the **Central** tab, go to **Settings** > **Account**.
    
3.  In the **Password** field, click the **Change** link and enter your Dashboard password.
    
4.  Click **Update**.
    

Only change your password through [Dashboard](https://platform.axway.com).