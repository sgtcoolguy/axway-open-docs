{"title":"Quick Start Guide for iOS APS SDK using Swift","weight":"20"}

*Pro or Enterprise Subscription Required*

This AMPLIFY Appcelerator Services feature requires a Pro or Enterprise Subscription.

* [Introduction](#introduction)

* [Requirements](#requirements)

* [Setup](#setup)

    * [Register an APS SDK application](#register-an-aps-sdk-application)

    * [Register an API or Microservice application](#register-an-api-or-microservice-application)

    * [Register a Website or Web application](#register-a-website-or-web-application)

    * [Register a Custom application](#register-a-custom-application)

* [Quick Tutorial](#quick-tutorial)

    * [Modify the Application](#modify-the-application)

    * [Send an Analytics Feature Event](#send-an-analytics-feature-event)

    * [Query Cloud Users](#query-cloud-users)

    * [Log in to a Cloud Account](#log-in-to-a-cloud-account)

    * [Set a Username for Crash Logs](#set-a-username-for-crash-logs)

    * [Testing the Tutorial Sample](#testing-the-tutorial-sample)

* [Next Steps for Appcelerator Analytics and Cloud](#next-steps-for-appcelerator-analytics-and-cloud)

## Introduction

This guide walks through the setup of the AMPLIFY Appcelerator Services for iOS applications. The AMPLIFY Appcelerator Services SDK gives you access to the Appcelerator Analytics and Cloud services. Note that the Appcelerator Test service does not currently work with Swift projects.

*Not developing a native iOS application with Swift?*

See the following topics to use the AMPLIFY Appcelerator Services on other platforms:

For native Android applications built with Java, see [Quick Start Guide for Android APS SDK](/docs/appc/AMPLIFY_Appcelerator_Services/AMPLIFY_Appcelerator_Platform_Services_How-tos/AMPLIFY_Appcelerator_Services_Native_SDKs/AMPLIFY_Appcelerator_Platform_Services_for_Android/Quick_Start_Guide_for_Android_APS_SDK/).

For native iOS applications built with Objective-C, see [Quick Start Guide for iOS APS SDK](/docs/appc/AMPLIFY_Appcelerator_Services/AMPLIFY_Appcelerator_Platform_Services_How-tos/AMPLIFY_Appcelerator_Services_Native_SDKs/AMPLIFY_Appcelerator_Platform_Services_for_iOS/Quick_Start_Guide_for_iOS_APS_SDK/).

For Titanium Applications, see [Quick Start](/docs/appc/Quick_Start/).

## Requirements

You should be familiar with developing native iOS applications using Xcode and Swift. The SDKs supports the following base SDK and target iOS versions:

| Maximum SDK version | Minimum SDK version | Maximum target iOS version | Minimum target iOS version |
| --- | --- | --- | --- |
| 9.0.x | 8.0.x | 9.0.x | 7.1.x |

## Setup

Before you can use Appcelerator Services in your application you need to:

* Create an application in Dashboard

* Download the SDK

* Get the APS application key

### Register an APS SDK application

Appcelerator Platform Services (APS) SDK for iOS and Android provides support for Appcelerator Analytics and Cloud services for your Android applications built with the native Android APIs and Java and iOS applications built with the native iOS APIs and Objective-C or Swift.

To register an APS SDK application for services:

1. Sign in to the [AMPLIFY Platform](https://platform.axway.com/).

2. Click the Add menu (**+**) and select **Register App for Services** to open the _Register App for Services_ form.

3. Enter the **Name** of the application.

4. Select **APS SDK** from the _Type_ selection menu.

    ![RegisterAppForService_latest_APSSDK](/Images/appc/download/attachments/60148494/RegisterAppForService_latest_APSSDK.png)
5. Select a **Platform** (**Andriod** or **iOS**).

6. Optionally, enter a unique **Identifier** for your application.

7. Optionally, enter a **Description** for your application.

8. Select **Services** for your application by selecting or deselecting the check-boxes for the following:

    * Analytics

    * Provision Cloud Services (Mobile Backend Services)

9. Add teams to the application from your organization by clicking the add (**+**) button in the Assign Teams list.

10. Click **OK**.

Appcelerator Dashboard displays the **Services** tab for your application. Follow the directions to add Platform Services to your application.

### Register an API or Microservice application

To register an API or microservice application:

1. Sign in to the [AMPLIFY Platform](https://platform.axway.com/).

2. Click the Add menu (**+**) and select **Register App for Services** to open the _Register App for Services_ form.

3. Enter the **Name** of the application.

4. Select **API/Microservice** from the _Type_ selection menu.

    ![RegisterAppForService_latest_API](/Images/appc/download/attachments/60148494/RegisterAppForService_latest_API.png)
5. Enter a **Platform** for your application.

6. Optionally, enter a unique **Identifier** for your application.

7. Optionally, enter a **Description** for your application.

8. Select **Services** for your application by selecting or deselecting the check-boxes for the following:

    * Analytics

    * Provision Cloud Services (Mobile Backend Services)

9. Add teams to the application from your organization by clicking the add (**+**) button in the Assign Teams list.

10. Click **OK**.

### Register a Website or Web application

To register a Website or Web application:

1. Sign in to the [AMPLIFY Platform](https://platform.axway.com/).

2. Click the Add menu (**+**) and select **Register App for Services** to open the _Register App for Services_ form.

3. Enter the **Name** of the application.

4. Select **Website/Web App** from the _Type_ selection menu.

    ![RegisterAppForService_latest_Web](/Images/appc/download/attachments/60148494/RegisterAppForService_latest_Web.png)
5. Enter a **Platform** for your application.

6. Optionally, enter a unique **Identifier** for your application.

7. Optionally, enter a **Description** for your application.

8. Select **Services** for your application by selecting or deselecting the check-boxes for the following:

    * Analytics

    * Provision Cloud Services (Mobile Backend Services)

9. Add teams to the application from your organization by clicking the add (**+**) button in the Assign Teams list.

10. Click **OK**.

### Register a Custom application

To register a custom application (other than APS SDK, API/Microservice, or Website/Web applications):

1. Sign in to the [AMPLIFY Platform](https://platform.axway.com/).

2. Click the Add menu (**+**) and select **Register App for Services** to open the _Register App for Services_ form.

3. Enter the **Name** of the application.

4. Select **Other** from the _Type_ selection menu.

    ![RegisterAppForService_latest_Other](/Images/appc/download/attachments/60148494/RegisterAppForService_latest_Other.png)
5. Enter a **Platform** for your application.

6. Optionally, enter a unique **Identifier** for your application.

7. Optionally, enter a **Description** for your application.

8. Select **Services** for your application by selecting or deselecting the check-boxes for the following:

    * Analytics

    * Provision Cloud Services (Mobile Backend Services)

9. Add teams to the application from your organization by clicking the add (**+**) button in the Assign Teams list.

10. Click **OK**.

Dashboard displays the **Platform Services** tab for your application. In the tab, you can download the APS SDK, and get code snippets to copy and paste into your application.

For more information, refer to [Managing Non-Titanium Client Applications in Dashboard](/docs/appc/Appcelerator_Dashboard/Appcelerator_Dashboard_Guide/Managing_Applications/Managing_Client_Applications/Managing_Non-Titanium_Client_Applications_in_Dashboard/).

## Quick Tutorial

The following tutorial demonstrates the basic setup and usage of Analytics and Cloud libraries in a Swift Xcode project. To complete the tutorial, you will need your APS application key for the Cloud and Analytics services. [Download](https://github.com/appcelerator-developer-relations/APSiOSSwift) a complete version of the project.

**To create a basic application using APS**:

1. In Xcode, create a new iOS Project (Single View Application). When prompted for options, select **Swift** in the **Language** drop-down.

2. Create a Header File and name it <PROJECT\_NAME>-Bridging-Header.h. Make sure the main project's application target folder is selected, then from the menu, select **File** > **New** > **File...** or drag a **Header File** from the **File Template** library to the application target folder. The application target folder is a folder under the root project folder and will be named the same as the project if the name has not been changed.
    ![BridgeHeadingFile](/Images/appc/download/attachments/43298728/BridgeHeadingFile.png)

3. Unzip the appcelerator-sdk-ios-<VERSION>.zip file and drag the Appcelerator.framework folder into the root project folder.

4. Select **Copy items into destination…** and click **Finish**.

5. Select your project in the Project Navigator and click the **Build Phases** tab.

6. Expand the **Link Binary With Libraries** section and add the libsqlite3.tbd and libz.tbd frameworks. Before Xcode 7, the framework extension is dylib rather than tbd.

7. Click the **Build Settings** tab, then click the **All** button in the top-left corner of the tab.

8. If you are using Xcode 7, you will need to disable bit code since some third-party libraries do not have bit code enabled. Expand the **Build Options** section and set **Enable Bitcode** to **No**.

9. Expand the **Linking** section and add \-ObjC to Other Linker Flags.

10. Expand the **Swift Compiler - Code Generation** section (near the bottom) and add the bridging header file (with the relative path from the root folder) to **Objective-C Bridging Header**, for example, <PROJECT\_NAME\>/<PROJECT\_NAME>-Bridging-Header.h.
    ![SwiftCompiler](/Images/appc/download/attachments/43298728/SwiftCompiler.png)

11. Open the bridging header file and add the following import statement:

    ```
    #import <Appcelerator/Appcelerator.h>
    ```

12. Open the application delegate file (AppDelegate.swift) and add the following initialization code to the application() method:

    ```
    APSServiceManager.sharedInstance().enableWithAppKey("APS_APP_KEY");
    ```

    The iOS application is now ready to make method calls using the APS SDK APIs.

If the application attempts to make APS SDK API calls without first setting the application key, the application will raise an exception and crash.

*Bridging Header File*

Alternatively, to have Xcode automatically create a bridging header file and add the build flag:

1. Skip steps 2 and 9 in the previous directions.

2. After step 8, create an Objective-C file. (From the menu, select **File** > **New** > **File...** or drag an Objective-C file from the **File Template** library to the application target folder.)

3. After creating the file, a dialog appears with the message "Would you like to configure an Objective-C bridging header?" Click **Yes**.

4. Xcode creates the header file and adds it to the build flag. Delete the Objective-C file you just created.

5. Follow steps 10 and 11.

### Modify the Application

Customize the application's UI to display a picker, text field and button, and add some logic to respond to user interaction. The picker will display a list of available user accounts. The user can enter their password in the text field, then click the button to log in.

1. Open your project's Main.storyboard file.

2. Drag a Picker View, Text Field, and Button from the Object library to the view.

3. Open the **Assistant Editor**. (From the menu, select **View** > **Assistant Editor** \> **Show Assistant Editor** or click the **Assistant Editor** button in the top-right corner.)

4. In the right pane, display the ViewController.swift file.

5. Control-drag the Picker View to the **View Controller** icon at the top of the view. Select **dataSource**. Repeat for the **delegate** option.

    ![ViewController](/Images/appc/download/attachments/43298728/ViewController.png)

6. Drag the Picker View to the header file to create an IBOutlet. Name the outlet picker and click **Connect**. Repeat the same procedure for the Text Field and name it textField.

    ![OutletCollection](/Images/appc/download/attachments/43298728/OutletCollection.png)

7. In the ViewController.swift file:

    1. Declare the View Controller to implement the UIPickerViewDelegate, UIPickerViewDataSource, and UITextFieldDelegate protocols.

    2. Add a Dictionary array called usernames to keep track of the Picker View's data source and a String variable called username to reference the current selection.

    3. Create an IBAction callback for the button named doClick. In the following sections, you will add code to this handler that calls Cloud and Analytics services.

    4. Implement the methods of UIPickerViewDelegate, UIPickerViewDataSource and UITextFieldDelegate protocols. Add the following code to the file:

    *ViewController.swift*

    ```swift
    import UIKit

    class ViewController: UIViewController, UIPickerViewDelegate, UIPickerViewDataSource, UITextFieldDelegate {
        @IBOutlet weak var textField: UITextField!
        @IBOutlet weak var picker: UIPickerView!

        // Add these variables
        var username: String = ""
        var usernames: [Dictionary<String,AnyObject>] = []

        override func viewDidLoad() {
            super.viewDidLoad()

            // Add these statements to dismiss the keyboard
            self.textField.delegate = self
            self.textField.resignFirstResponder()
        }

        override func didReceiveMemoryWarning() {
            super.didReceiveMemoryWarning()
        }

        // Add these methods

        @IBAction func onClick(sender: UIButton) {

        }

        // MARK: Picker DataSource/Delegate
        func numberOfComponentsInPickerView(pickerView: UIPickerView) -> Int {
            return 1;
        }

        func pickerView(pickerView: UIPickerView, numberOfRowsInComponent component: Int) -> Int {
            return self.usernames.count
        }

        func pickerView(pickerView: UIPickerView, titleForRow row: Int, forComponent component: Int) -> String! {
            return self.usernames[row]["username"] as String
        }

        func pickerView(pickerView: UIPickerView, didSelectRow row: Int, inComponent component: Int) {
            self.username = self.usernames[row]["username"] as String
        }

        // MARK: TextField Delegate
        func textFieldShouldBeginEditing(textField: UITextField) -> Bool {
            return true
        }

        func textFieldShouldReturn(textField: UITextField) -> Bool {
            return true
        }
    }
    ```

8. Control-drag the Button to the onClick() method to create an action connection.

    ![ConnectAction](/Images/appc/download/attachments/43298728/ConnectAction.png)

### Send an Analytics Feature Event

The Analytics library automatically captures and sends application life-cycle events to the backend Analytics service. You can also send custom analytics events, as shown in this example. You can use feature events as one type of custom events.

In the doClick method, add a APSAnalytics.sharedInstance().sendAppFeatureEvent() method call to send a feature event with the string "sample.feature.login". The optional payload parameter is set to nil for this example, but it lets you send additional data along with the event.

*ViewController.swift*

```swift
APSAnalytics.sharedInstance().sendAppFeatureEvent("sample.feature.login", payload: nil)
```

### Query Cloud Users

To use the APS Cloud component, most of the methods require a user to be logged in. This sample uses the Picker View to select a Cloud user account. To populate the Picker View values, the application needs to retrieve a list of users. Call the APSUsers.query() method to retrieve a list of user accounts from inside the viewDidLoad() method.

Every APS Cloud method includes a withBlock parameter that specifies the callback to handle the server response. The callback is passed an APSResponse object that contains response metadata (such as success or failure) and the response payload.

*ViewController.swift*

```swift
APSUsers.query(nil, {(e: APSResponse!) -> Void in
    if (e.success) {
        self.usernames = e.valueForKey("response")?.valueForKey("users") as [Dictionary<String,AnyObject>]
        self.picker.reloadAllComponents()
    } else {
        var alert: UIAlertView = UIAlertView(title: "Error", message: "Unable to retrieve user accounts!", delegate: nil, cancelButtonTitle: "OK")
        alert.show()
    }
})
```

### Log in to a Cloud Account

To log in to a Cloud account, you need the username and password. Since the application was modified to get all available user accounts and populate the Picker View, the application needs to get the current value of the picker and the text entered in the Text Field. These values are passed to the APSUsers.login() method. Modify the doClick method to login to a Cloud user account.

*ViewController.swift*

```swift
@IBAction func onClick(sender: UIButton) {
    // Send analytics feature event
    APSAnalytics.sharedInstance().sendAppFeatureEvent("sample.feature.login", payload: nil)

    // Login to a Cloud account
    var params = [
        "login" : self.username,
        "password" : self.textField.text
    ]
    APSUsers.login(params, { (e: APSResponse!) -> Void in
        if (e.success) {
            NSLog("Successfully logged in as %@", self.username)
        } else {
            NSLog("ERROR: Failed to log in!")
        }
    })
}
```

### Set a Username for Crash Logs

To help differentiate crash logs, use the username property. When the application successfully logs in to the Cloud user account, the application sets the username property.

*ViewController.swift*

```swift
@IBAction func onClick(sender: UIButton) {

    APSUsers.login(params, { (e: APSResponse!) -> Void in
        if (e.success) {
            NSLog("Successfully logged in as %@", self.username)
            // Add this Performance call
            APSPerformance.sharedInstance().username = self.username
        } else {
            NSLog("ERROR: Failed to log in!")
        }
    })
}
```

### Testing the Tutorial Sample

Before testing the sample, you need to create user accounts for the application to query. To create Cloud user accounts:

1. Login to the [AMPLIFY Platform](https://platform.axway.com/).

2. On the Dashboard tile, select **Go to Dashboard**.

3. Select your application from the Projects menu.

4. In the left navigation bar, click **Manage** **Data**.

5. Click **Users**, then the **Create User** button.

6. In the **Username** field, enter the user's username.

7. In the **Password** field, enter the new user's password (four-character minimum).

8. Click **Save Changes**.

To create a Cloud user account, you only need a username or e-mail address and a password.

For more information about managing Cloud user accounts, see [Managing Organizations](/docs/appc/Appcelerator_Dashboard/Appcelerator_Dashboard_Guide/Managing_Organizations/).

After you have created a few Cloud user accounts, build the sample and launch it on either a device or emulator.

Once the application launches:

1. Click on the Picker. You should see a list of all the Cloud user accounts you added.

2. Select a user account from the Picker and enter that user's password. Click the Button. In the log output, you should see an info log that login command was successful or not.

3. Go back to the [Dashboard](https://platform.axway.com/).

4. In Dashboard, select your application from the **Apps** menu in the upper-left corner.

5. In the left navbar, select **Analytics**.

6. In the Real-Time view, you should see at least one active session.

7. In the left navbar, click **Events**. You should see the "sample.feature.login" feature event.

## Next Steps for Appcelerator Analytics and Cloud

This tutorial only covers a small portion of what the Analytics and Cloud services can provide. For more in-depth information about these features, see the following topics. Note that these guides were written for Objective-C projects. You will need to adapt the API calls for Swift.

* [APS Analytics for iOS](/docs/appc/AMPLIFY_Appcelerator_Services/AMPLIFY_Appcelerator_Platform_Services_How-tos/AMPLIFY_Appcelerator_Services_Native_SDKs/AMPLIFY_Appcelerator_Platform_Services_for_iOS/APS_Analytics_for_iOS/)

* [APS Cloud for iOS](/arrowdb/latest/#!/guide/ios)
