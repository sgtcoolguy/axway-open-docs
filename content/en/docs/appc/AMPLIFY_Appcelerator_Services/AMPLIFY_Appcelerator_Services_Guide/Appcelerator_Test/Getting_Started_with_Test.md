{"title":"Getting Started with Test","weight":"10"} 

Enterprise Subscription Required!

This AMPLIFY Appcelerator Services feature requires an Enterprise Subscription.

*   [Enabling Appcelerator Services](#EnablingAppceleratorServicesenable_appc_services)
    
*   [Installing the TouchTest Agent](#InstallingtheTouchTestAgent)
    
    *   [Device and OS requirements](#DeviceandOSrequirements)
        
    *   [TouchTest Agent URL](#TouchTestAgentURL)
        
    *   [Installing TouchTest Agent on an Android device or emulator](#InstallingTouchTestAgentonanAndroiddeviceoremulator)
        
    *   [Installing TouchTest Agent on an iOS device or simulator](#InstallingTouchTestAgentonaniOSdeviceorsimulator)
        
        *   [Finding your system's Hardware UUID](#Findingyoursystem'sHardwareUUID)
            
    *   [Launching the TouchTest Agent](#LaunchingtheTouchTestAgent)
        
    *   [TouchTest Agent user name](#TouchTestAgentusernameusername)
        
        *   [Locating your organization's ID](#Locatingyourorganization'sIDlocateid)
            
    *   [Approving devices and simulators](#Approvingdevicesandsimulatorsapproval)
        
*   [Testing basics](#Testingbasics)
    
    *   [Installing the TouchTest-enabled application](#InstallingtheTouchTest-enabledapplication)
        
    *   [Recording a Test Clip](#RecordingaTestCliprecord_test_clip)
        
    *   [Playing a composition](#Playingacomposition)
        
    *   [Result Details dashboard](#ResultDetailsdashboard)
        
    *   [Locating UI elements](#LocatingUIelements)
        
        *   [Using the Locator tool](#UsingtheLocatortoollocator_tool)
            
        *   [Locator reference](#Locatorreference)
            
    *   [Editing App Action properties](#EditingAppActionproperties)
        
*   [Production deployment](#Productiondeployment)
    
*   [Further reading](#Furtherreading)
    

This document explains the steps required to get started recording test clips, and composing and playing test compositions on a device, simulator, or emulator.

## Enabling Appcelerator Services

To use the Test service to test an application, you must enable Appcelerator Services in your project. This adds the TouchTest module to your project, and the code required to load and initialize it. (For specific code and configuration changes, see [Platform Services](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Titanium_Development/Platform_Services/)). Do not modify these changes or you may disable the Test service in your application.

For native Android and iOS applications, use the appcelerator-test utility to enable the Appcelerator Test service. For instructions, see [Appcelerator Test CLI Reference](/docs/appc/AMPLIFY_Appcelerator_Services/AMPLIFY_Appcelerator_Platform_Services_How-tos/AMPLIFY_Appcelerator_Services_Native_SDKs/Appcelerator_Test_CLI_Reference/).

For Titanium applications, use Appcelerator Studio to enable Appcelerator Services when creating a new project by selecting an option in the new project dialog, or in an existing project. If you have an existing Titanium Studio application, you'll first need to import that application into Appcelerator Studio.

 **![enable_services](/Images/appc/download/attachments/43298707/enable_services.png)** 

**To enable Appcelerator Services in a new project:**

1.  In Appcelerator Studio, create a new Mobile App Project (**File** \> **New** \> **Mobile App Project**).
    
2.  Check the **Appcelerator Services** check box in the Mobile App Project wizard dialog.
    

**To enable Appcelerator Services in an existing Appcelerator Studio project** :

1.  Open the project's tiapp.xml file.
    
2.  Click **Enable...** in the Appcelerator Services section,
    
    ![services_not_enabled](/Images/appc/download/attachments/43298707/services_not_enabled.png)

A green check mark appears next to each service that was successfully enabled.  
  
![image2014-3-14_17_54_39](/Images/appc/download/attachments/43298707/image2014-3-14_17_54_39.png)

## Installing the TouchTest Agent

To run tests on a device you need to install the **TouchTest Agent** a light-weight software agent that controls the device during test recording and playback. Once installed you also need to register your device with the Test service, and have the device approved by an administrator (see [Approving devices and simulators](#approval)).

### Device and OS requirements

TouchTest Agent is supported on the following platforms:

*   iOS devices and simulators running iOS 5.0 and later
    
*   Android devices running Android 2.3.3 and later
    
*   Android emulators running Android 2.3.5 and later
    

### TouchTest Agent URL

You use the TouchTest Agent URL to start the installation and registration process and to access:

*   **TouchTest Agent URL**: **[http://appctest-2.appcelerator.com/concerto/touchtest](http://appctest-2.appcelerator.com/concerto/touchtest)**
    
*   **QR code**:
    
    ![qrcode](/Images/appc/download/attachments/37523016/qrcode.png)

Note to VPC customers

Enterprise customers who are running Test in a Virtual Private Cloud (VPC) must use the custom TouchTest Agent URL provided to them by Appcelerator.

### Installing TouchTest Agent on an Android device or emulator

The TouchTest Agent application supports devices running Android 2.3.3 and later, and Android emulators running 2.3.5 and later. The install steps are the same for Android devices and emulators.

**To install TouchTest Agent on an Android device or emulator**:

1.  Point your device's or emulator's web browser to the [TouchTest Agent URL](#anchorurl) ( **http://appctest-2.appcelerator.com/concerto/touchtest** ).
    
2.  In the login form enter your enter AMPLIFY Appcelerator Services credentials. You must append your organization ID to your login name (see [Logging into TouchTest Agent](#loggingin)).
    
3.  Click **Tap Here to Download TouchTest Agent.**
    
4.  Open the APK file that was downloaded to install the TouchTest Agent.
    
5.  Open the TouchTest Agent application.
    
6.  In the **TouchTest Agent URL** field enter the [TouchTest Agent URL](#agenturl) and click Go.
    
7.  Enter your AMPLIFY Appcelerator Services credentials. You must append your organization ID to your login name (see [Logging into TouchTest Agent](#loggingin)).
    
8.  On successful login, enter a name for your device and click **Submit for Approval**.
    
9.  Once the device [has been approved](#approval), the TouchTest Agent displays its current connection status to the Test web service, as well as the current TouchTest URL, user name, and the TouchTest Agent build number.
    

You can now record a clip on the device.

### Installing TouchTest Agent on an iOS device or simulator

On iOS, the TouchTest Agent runs as a web application in mobile Safari. The steps for installing TouchTest Agent on an iOS device and simulator are slightly different. Also, installing TouchTest Agent on a simulator running iOS 6 or earlier requires providing the Mac system's hardware UUID.

**To install on an iOS device:**

1.  Point the device's Safari browser at the [TouchTest Agent URL](#anchorurl) ( **http://appctest-2.appcelerator.com/concerto/touchtest** ).
    
2.  Enter your AMPLIFY Appcelerator Services credentials and log in.
    
3.  Click **Register Device**. The Install Profile dialog opens asking you to install the **TouchTest Device Registration** profile.
    
4.  Click **Install** in the Install Profile dialog, then click **Install Now** in the confirmation dialog. (You may also be prompted for a passcode by the device if that security feature is enabled.)
    
5.  Enter a name for your device and click **Submit for Approval**.
    
6.  Once the device [has been approved](#approval), the TouchTest Agent displays the current connection status to the Test web service, TouchTest URL, user name, and TouchTest Agent build number.
    

**To install on an iOS simulator:**

1.  Point the simulator's web browser at the [TouchTest Agent URL](#anchorurl) ( **http://appctest-2.appcelerator.com/concerto/touchtest** ).
    
2.  Click **Tap here if this is a simulator**.
    
3.  Enter your AMPLIFY Appcelerator Services credentials and log in.
    
4.  Click **Register** **Simulator**.
    
5.  For simulators running **iOS 6 or earlier**, provide your computer's hardware UUID.
    
6.  Provide a name for your device and click **Submit for Approval**. (The name must be unique among other registered devices in your organization.)
    
7.  Once the device [has been approved](#approval), the TouchTest Agent displays the current connection status to the Test web service, TouchTest URL, user name, and TouchTest Agent build number.
    

#### Finding your system's Hardware UUID

To register an iOS simulator running iOS 6 or earlier, you need to provide your system's Hardware UUID.

![image2014-3-17_17_14_48](/Images/appc/download/attachments/43298707/image2014-3-17_17_14_48.png)

**To find your UUID for your Mac OS system:**

1.  From the Apple menu, select **About this Mac**.
    
2.  In the window that opens click **More Info**...
    
3.  Click **System Report**...
    
4.  Select **Hardware** in the left-hand pane.
    
5.  In the Hardware Overview section in the right-hand pane, locate the **Hardware UUID** item.
    
6.  Copy it to your clipboard and paste into the **Mac Hardware UUID** field in Safari.
    
7.  Click **Save UUID and Proceed**.
    

### Launching the TouchTest Agent

To record or playback a test, the TouchTest Agent must be running on the test device. These steps assume you've already installed the TouchTest Agent and had your device registered and approved (see [Installing the TouchTest Agent](#InstallingtheTouchTestAgent) for instructions).

**To start the TouchTest Agent on your device, simulator, or emulator:**

1.  Close the installed application to test, if it's open.
    
2.  Open the TouchTest Agent:
    
    *   On Android, open the TouchTest Agent application that you installed.
        
    *   On iOS, open Safari and navigate to the [TouchTest Agent URL](#agenturl).
        
3.  Provide your AMPLIFY Appcelerator Services login credentials, if prompted (see [TouchTest Agent user name](#loggingin)).
    

When launched, the TouchTest Agent displays its current connection status. Make sure the **Status** field says "Connected", as shown below. You're now ready to record a clip.

![ios_agent_connected](/Images/appc/download/attachments/43298707/ios_agent_connected.png)

### TouchTest Agent user name

When logging in to the TouchTest Agent, the user name you provide must be followed by a forward slash (**/**) and your organization's ID (see [Locating your organization's ID](#locateid)). For example, if your primary login name is "user@appcelerator.com", and your organization ID is "12345", then your login name would be "user@apppcelerator.com/12345".

![image2014-3-11_15_5_26](/Images/appc/download/attachments/43298707/image2014-3-11_15_5_26.png)

#### Locating your organization's ID

You can locate your organization ID in the My Profile screen in Dashboard, or inside the project's tiapp.xml file in Appcelerator Studio.

**To find your organization's ID in Dashboard**:

1.  Login to the [AMPLIFY Platform](https://platform.axway.com/).
    
2.  On the Dashboard tile, select **Go to Dashboard**.
    
3.  Click on your name located in the top-right corner to open the Profile menu.
    
4.  Do one of the following:
    
    *   If you are a member of **one** organization, click **My Profile** in the Profile menu to open your profile page. The organization ID is shown in parentheses next to the organization name.
        
        ![profile_org_id](/Images/appc/download/attachments/43298707/profile_org_id.png)
    *   If you are a member of **more than one** organization, the Profile menu displays the names and IDs for each organization you belong to, as shown below:
        
        ![image2014-3-11_15_12_16](/Images/appc/download/attachments/43298707/image2014-3-11_15_12_16.png)

**To find your organization's ID in Appcelerator Studio**:

1.  In Appcelerator Studio open the project's tiapp.xml file. Make sure to select the Overview tab in the lower-left corner of the editor window.
    
2.  In the Appcelerator Services section, locate the organization ID in parentheses after the organization name:
    
    ![image2014-3-18_15_22_23](/Images/appc/download/attachments/43298707/image2014-3-18_15_22_23.png)

### Approving devices and simulators

Each new device or simulator that's registered must first be approved before it can be used with Appcelerator Test. If you have administrator privileges for Dashboard, you can approve devices by following the steps below. If you do not have administrator privileges, contact your administrator to have your device approved.

Once a device has been registered, it cannot be unregistered; that is, it cannot be removed from the list of authorized devices for Appcelerator Test.

**To approve a newly registered device or simulator:**

1.  Open the Appcelerator Test dashboard in your browser.
    
2.  Select **Device Clouds** from the left pane.
    
3.  In the right pane, locate the newly registered device whose status is **Pending Approval**, and click **Approve**. Once approved, the device's status changes to **Connected**, if the TouchTest Agent is open on the device.
    
    ![image2014-3-12_10_19_19](/Images/appc/download/attachments/43298707/image2014-3-12_10_19_19.png)

## Testing basics

Once your device or simulator has the TouchTest Agent installed and has been approved by a Test administrator, you're ready to start creating and playing back tests.

### Installing the TouchTest-enabled application

Once you've created a TouchTest-enabled project in Appcelerator Studio (by [enabling Appcelerator Services](#enable_appc_services)), the next step is to build and install the application on the test device, simulator, or emulator. You can use either the **Run** or **Test** commands to build and install the application on the target device.

The Test command displays a dialog with instructions and information about your Test environment, including the TouchTest Agent URL and login name.

You must rebuild the application and re-install it on the target device after making any changes that affect testing.

### Recording a Test Clip

A **clip** is the basic building block of a test. You create clips in the **Clip Editor**. Clips are composed of App Actions – taps, gestures, text inputs, and so forth – that simulate actions a user takes in an application. When you record a test clip, the actions you take on a device are automatically added as App Actions in the test clip.

For example, the following screenshot shows a test clip containing four recorded actions: a **tap** operation, followed a **type** operation, followed by two more **tap** operations.

![image2014-3-4_16_46_47](/Images/appc/download/attachments/43298707/image2014-3-4_16_46_47.png)

Typically a recorded test clip is a starting point for you to refine, add validations, inputs, outputs and so forth.

**To record a test clip**:

1.  On the test device, open the TouchTest Agent and ensure its connected to the Test service (see [Launching the TouchTest Agent](#LaunchingtheTouchTestAgent)).
    
2.  Open [Dashboard](https://platform.axway.com/) and click the **Test** tab.
    
3.  Select the application to test from the Application menu in the upper-left corner.
    
    To quickly access the Test tab for your application from Appcelerator Studio, click the Details link next to the Test entry in your project's tiapp.xml file.
    
    ![image2014-3-11_15_48_59](/Images/appc/download/attachments/43298707/image2014-3-11_15_48_59.png)
    
4.  With your application selected, on the **Central** tab select **Clips** in the left navigation, then click the **New** button. The **Clip Editor** opens a new untitled clip.
    
5.  In the Clip Editor, click the **Record** menu and select **Record Mobile App**.
    
6.  In the **Choose a Device Agent and Mobile App** dialog select the test device from the upper pane, and the application to test, and click **Record**.  
    ![choose_agent_app](/Images/appc/download/attachments/43298707/choose_agent_app.png)
    
7.  The test application launches on the device. Perform actions on the device according to your test scenario – tap buttons, input text, perform gestures, and so forth. Your actions are recorded as App Actions in the Clip Editor.
    
    ![image2014-3-4_16_46_47](/Images/appc/download/attachments/43298707/image2014-3-4_16_46_47.png)
8.  When finished recording, click the **Record** button in the Test tab in Dashboard again to stop recording.
    
9.  Click **Save** or **Save As** in the toolbar, give the clip a name or accept the default, and click **Save**.
    

To playback a test clip that you've recorded, it needs to be added to a **test composition**. See [Creating a composition](#Creatingacomposition).

A test composition is an actual test that's executed on the device. A composition consists of one or more clips arranged on _tracks_. You  edit compositions in the Composition Editor. You can organize tracks in the desired sequence, select target devices on a per-track or per-clip basis, and other settings. The Composition Editor is also the player, debugger, and dashboard where test results are displayed. Each of these functions is presented in separate tabs named **Edit**, **Debug**, **Play**, and **Results**, as shown below.

![image2014-3-18_16_13_21](/Images/appc/download/attachments/43298707/image2014-3-18_16_13_21.png)

**To create a composition from the Clip Editor:**

1.  With your test clip open in the Clip Editor, click Use in Composition Editor menu in the upper-right corner of the Clip Editor toolbar.
    
    ![image2014-3-17_13_30_53](/Images/appc/download/attachments/43298707/image2014-3-17_13_30_53.png)  
    An explanation of menu items:
    
    *   **Open in Test Composition** – Adds the clip to a new draft composition where additional composition parameters can be set before proceeding to play.
        
    *   **Play in Test Composition** – Adds this clip to a new draft composition that immediately begins playback.
        
    *   **Debug in Test Composition** – Adds this clip to a new draft composition where it can be debugged.
        
2.  The Composition Editor opens with a draft test composition that has the recorded test clip in **Track 1**.**Tip**: Double-click the track name to edit it.
    
    ![image2014-3-17_13_8_59](/Images/appc/download/attachments/43298707/image2014-3-17_13_8_59.png)
    
    By default, the device that was used to record the clip is automatically selected as the playback device (**iPhone 7 simulator**, in the above screenshot). You can select a connected device by clicking the Device pop-up menu.
    
    ![image2014-3-17_13_6_6](/Images/appc/download/attachments/43298707/image2014-3-17_13_6_6.png)
    
3.  Click **Save** or **Save As** Composition Editor toolbar and give the test composition a name or accept the default name.
    

You can also create an empty test composition and add existing test clips to it.**  
To create an empty test composition**:

1.  On the **Central** tab select **Composition** from the left navigation and then click the **New** button. The Composition Editor opens a new untitled composition.
    
2.  Click the Composition Builder tab to open it, if not already open.
    
3.  Drag a test clip from the Composition Builder panel and drop it on the existing Track 1. Repeat to add more test clips.
    
    ![image2014-3-17_16_36_17](/Images/appc/download/attachments/43298707/image2014-3-17_16_36_17.png)
4.  Save the composition.
    

### Playing a composition

During playback, the actions in the test clip are repeated precisely as when they were recorded.

**To play a test composition open in the Composition Editor**:

1.  Make sure the TouchTest Agent is open on your test device and its status is “Connected”.
    
2.  In the Composition Editor, click **Play** to run the test composition. The app actions performed when the clip was created are played back on the device. Once playback has started on the device, the [Result Details dashboard](#ResultDetailsdashboard) opens.
    

### Result Details dashboard

The Result Details dashboard displays the results from playback of a test composition. Results are posted continuously as playback progresses. If the composition fails for any reason, the dashboard clearly indicates the error and provides details as to what caused it. Results are displayed in a cover-flow view and in an expandable tree control on the left. As play continues, the focus is set to the last executed element. Clicking an element during play will pin the focus on that element.

![image2014-3-13_10_40_14](/Images/appc/download/attachments/43298707/image2014-3-13_10_40_14.png)

### Locating UI elements

Most app actions (with a few exceptions) have a **Locator** input property that identifies the UI element to apply the action too. A locator can take several forms, such as by the element's class name (UIButton, for example), the text it contains, an XPath expression, or by a unique ID the developer assigns to a UI view (see [Using touchTestIDs](#using_touchtestids) ). For a complete list of locators, you can use, see the [Locator reference](#Locatorreference).

For example, suppose an application contains an input text field with the placeholder text "What do you need to do?", as in the Alloy Todos sample application.

To locate this element you can use the **placeholder** locator, which returns the element whose placeholder text matches the provided string.

![image2014-3-12_15_19_7](/Images/appc/download/attachments/43298707/image2014-3-12_15_19_7.png)

Using touchTestIDs

TouchTestIds are strings set by the developer to identify views in the application for testing. Using touchTestIDs makes tests easier to create and maintain since you're not relying on class names or text strings that may change. They also improve playback performance of your tests.

As an example, consider a test clip that uses an input text field's placeholder text to locate it for a **type** action.

![image2014-3-12_15_19_70](/Images/appc/download/attachments/43298707/image2014-3-12_15_19_70.png) This approach will continue to work unless the placeholder text is changed to another string ("What to do?"). Of course, you can always update the locator to match the new placeholder value. A better approach is for the developer to assign a touchTestId property to the view. For example:

Alloy app

`<``TextField`  `touchTestId``=``"todoInput"`  `hintText``=``"What do you need to do?"``></``TextField``>`

JavaScript

`var` `textfield = Titanium.UI.createTextField({`

`touchTestId:` `"todoInput"``,`

`hintText:` `"What do you need to do?"`

`})`

When creating the test, you can specify the TextField element with the locator id=todo Input.

![image2014-3-19_15_5_48](/Images/appc/download/attachments/43298707/image2014-3-19_15_5_48.png)

You can use the [Locator tool](#locator_tool) to determine an element's touchTestIDs if any.

#### Using the Locator tool

You can use the Locator tool to determine all the available locators, including touchTestIDs, that are available to locate a given UI element.

**To use the Locator tool:**

1.  Open the TouchTest Agent on the target device.
    
2.  In the Clip Editor, expand the action whose Locator property you want to inspect. The Locator Tool is initially disabled.
    
    ![image2014-3-12_14_25_47](/Images/appc/download/attachments/43298707/image2014-3-12_14_25_47.png)
3.  From the Record menu, select **Record Mobile App**. Accept the currently selected Device Agent/Mobile App combination.
    
4.  Click the Locator tool to enter Touch Locator mode.
    
5.  In the application, select the desired UI element. The currently selected element is surrounded with a blue highlight, and a pop-up appears listing the element's available locators. For example, in the screenshot below the UITableView element has two locators: the touchTestId of **todoTable**, or the class name of **UITableView**.
    
    ![image2014-3-12_14_20_33](/Images/appc/download/attachments/43298707/image2014-3-12_14_20_33.png)
6.  Tap the **Use** ![image2014-3-12_15_1_9](/Images/appc/download/thumbnails/43298707/image2014-3-12_15_1_9.png) button in the top-right corner of the pop-up to complete the selection. In the Clip Editor, the Locator drop-down now contains all possible locator values for that element, for easy access.
    
    ![image2014-3-12_14_36_35](/Images/appc/download/attachments/43298707/image2014-3-12_14_36_35.png)

#### Locator reference

The following table lists the different types of locators you can use to identify UI elements in your application.

Locator name

Description

kindof

Locates elements that are a subclass of the specified class. For example, kindof=UIButton will find UIButtons, as well as UIRoundedRectButtons.

classname

Locates elements that are of the specified class. For example, classname=UIButton will find only UIButtons but not UIRoundedRectButtons.

xpath

Locates any element that matches the specified Xpath. Use the outputXmlHierarchy accessor to see the XML to which the XPath is applied. Usage:

*   //UITableView//UILabel\[@text="Carbon"\]
    
*   //UITableViewCell\[UITableViewCellContentView/UILabel\[@text="Pickers"\]\]/UIButton
    
*   //UIDatePicker\[@touchTestId="DatePicker"\]//UIPickerTableView\[0\]
    

partialText

Locates elements that contain the specified text. Usage: partialText=for all good men

textStartsWith

Locates elements that have text that starts with the specified text. Usage: textStartsWith=Now is the time

textEndWith

Locates elements that have text that ends with the specified text.

Usage: textEndsWith=aid of their country.

text

Locates elements that have text that matches the specified text exactly.

Usage: text=Login

index

Locates elements that have the specified index in the view hierarchy. It's usually used in conjunction with other locator strategies and is assumed if no strategy is given (ie. UIButton\[2\] is the same as UIButton\[index=2\].

placeholder

Locates elements that have a placeholder property that matches the specified text.

Usage: placeholder=User name

touchTestId

Locates elements that have a touchTestId property that matches the specified text. See [Using touchTestIDs](#using_touchtestids) for more information.

Usage: id=addItem\_btn

accessibilityLabel

Locates elements that have an accessibility label that matches the specified text. Accessibility labels can only be used when the device has the VoiceOver accessibility feature turned on.

Usage: accessibilityLabel=User name

tag

Locates elements that have a tag property that matches the specified integer. Tags are an integer set by the developer to identify views in the application.

Usage: tag=20

### Editing App Action properties

During a recording, your actions are recorded as App Actions in the Clip Editor. After recording, you can edit properties of the recorded actions to modify their behavior, timing, and output.

You can view App Actions in a list or icon format.

![image2014-3-13_15_54_37](/Images/appc/download/attachments/43298707/image2014-3-13_15_54_37.png)

Double-clicking an action opens a bottom tab where you can edit the action's properties.

![image2014-3-13_15_14_55](/Images/appc/download/attachments/43298707/image2014-3-13_15_14_55.png)

Each action has the following properties and commands you can use to configure its behavior:

*   **Inputs** are arguments you pass to the action that configure its behavior. Some inputs are common to all actions such as Locators.
    
*   **Waits** are commands that tell TouchTest not to execute an Action until a condition is met (a _pre-action wait_), or to not continue processing the outputs, validations and property sets of the Action until a condition is met (_post-action waits_). See [Waits for Browser or App Actions](http://cloudlink.soasta.com/t5/Knowledge-Base/Waits-for-Browser-or-App-Actions/ba-p/94) in the SOASTA knowledge base for more information.
    
*   **Outputs** specify what is to be shown in the Result Viewer for a given Action. Commonly used outputs include **captureScreenshot** and **outputXMLHierarchy.** A single Action can have an unlimited number of outputs. See [Outputs for Browser or App Actions](http://cloudlink.soasta.com/t5/Knowledge-Base/Outputs-for-Browser-or-App-Actions/ba-p/96) in the SOASTA knowledge base for more information.[](http://cloudlink.soasta.com/t5/Knowledge-Base/Outputs-for-Browser-or-App-Actions/ba-p/96)
    
*   **Validations** verify that content appeared or an event occurred as expected. Each validation has a corresponding Failure Action. App Action validations can range from simple true/false conditions to more complex conditions. A single App Action can have an unlimited number of validations. Validation failures are exposed in the Results Dashboard. See [Validations for Browser or App Actions](http://cloudlink.soasta.com/t5/Knowledge-Base/Validations-for-Browser-or-App-Actions/ba-p/98) in the SOASTA knowledge base for more information.
    
*   **Property Sets** give you the ability to take text or data from the app you are testing and store it in a custom property for use in a subsequent action or message. See [Property Sets in a Browser or App Action](http://cloudlink.soasta.com/t5/Knowledge-Base/Property-Sets-in-a-Browser-or-App-Action/ba-p/102) in the SOASTA knowledge base for more information.
    

You can also view and edit an action's properties in the list view.

![image2014-3-13_15_10_22](/Images/appc/download/attachments/43298707/image2014-3-13_15_10_22.png)

## Production deployment

Before deploying your application to production, remove the Test module from the application. For App Store submissions, your application will be rejected if the Test module is included in your published app.

**To disable the Test module for production builds**:

1.  Open your application's tiapp.xml in the **Overview** tab.
    
2.  In the **Modules** section, double-click the **com.soasta.touchtest** module. A dialog appears.
    
3.  Click the **Deployment Type** link next to the iOS item to expand it.
    
4.  Uncheck **Production** and make sure either **Development,** **Test** or both items are checked. (If all items are unchecked, it will behave the same as if all items were checked, so make sure at least one item is checked.)
    
    ![image2014-3-19_15_42_54](/Images/appc/download/attachments/43298707/image2014-3-19_15_42_54.png)
5.  Click **OK**.
    
6.  Build and package your application.
    

## Further reading

*   [About App Actions](http://cloudlink.soasta.com/t5/Knowledge-Base/App-Actions/ba-p/5150)
    
*   [Waits for Browser or App Actions](http://cloudlink.soasta.com/t5/Knowledge-Base/Waits-for-Browser-or-App-Actions/ba-p/94)
    
*   [Outputs for Browser or App Actions](http://cloudlink.soasta.com/t5/Knowledge-Base/Outputs-for-Browser-or-App-Actions/ba-p/96)[](http://cloudlink.soasta.com/t5/Knowledge-Base/Outputs-for-Browser-or-App-Actions/ba-p/96)
    
*   [Validations for Browser or App Actions](http://cloudlink.soasta.com/t5/Knowledge-Base/Validations-for-Browser-or-App-Actions/ba-p/98)
    
*   [User-Defined Validations for Messages](http://cloudlink.soasta.com/t5/Knowledge-Base/User-Defined-Validations-for-Messages/ba-p/294)
    
*   [Property Sets in a Browser or App Action](http://cloudlink.soasta.com/t5/Knowledge-Base/Property-Sets-in-a-Browser-or-App-Action/ba-p/102)
    
*   [TouchTest™ for Appcelerator iOS Tutorial](http://cdn.soasta.com/productresource/download/SOASTA_TouchTest_Appcelerator_Android_Tutorial.pdf) (PDF) Start on page 21, "Recording a TouchTest Scenario"
    
*   [TouchTest™ for Appcelerator Android Tutorial](http://cdn.soasta.com/productresource/download/SOASTA_TouchTest_Appcelerator_Android_Tutorial.pdf) (PDF) Start on page 20, "Recording a TouchTest Scenario")