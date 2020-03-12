{"title":"Test Best Practices","weight":"20"} 

Enterprise Subscription Required!

This AMPLIFY Appcelerator Services feature requires an Enterprise Subscription.

*   [Introduction](#Introduction)
    
*   [App Action Life Cycle](#AppActionLifeCycle)
    
    *   [1\. Pre-Waits](#1.Pre-Waits)
        
    *   [2\. Inputs](#2.Inputs)
        
    *   [3\. Action](#3.Action)
        
    *   [4\. Post-Waits](#4.Post-Waits)
        
    *   [5\. Output](#5.Output)
        
    *   [6\. Validation](#6.Validation)
        
    *   [7\. Property Sets](#7.PropertySets)
        
*   [Debugging Best Practices](#DebuggingBestPractices)
    
    *   [Capture a screenshot and XML hierarchy for every failed action](#CaptureascreenshotandXMLhierarchyforeveryfailedaction)
        
    *   [Enable Heads Up Display](#EnableHeadsUpDisplay)
        
    *   [Verify that elements are visible and present](#Verifythatelementsarevisibleandpresent)
        
    *   [Capture the text contents of a screen element](#Capturethetextcontentsofascreenelement)
        
*   [Clip Building Best Practices](#ClipBuildingBestPractices)
    
    *   [Manage variable timing](#Managevariabletiming)
        
    *   [Validation against elements outside the screen](#Validationagainstelementsoutsidethescreen)
        
    *   [Validations](#Validations)
        
    *   [Group and name actions](#Groupandnameactions)
        
    *   [Conditional testing](#Conditionaltesting)
        

## Introduction

This Best Practices guide serves as a quick reference for handling common test clip and composition creation requirements.

This document provides an outline of the order of operations on mobile device events, which is very important to understand when you are creating and enhancing clips for use as repeatable functional test assets.

Some operations require different approaches, depending on the application development framework. Because of the differences in application architecture, there is not always a "one size fits all" approach, and the tester must use techniques that leverage the appropriate infrastructure of the application.

## App Action Life Cycle

It is critical to understand the order of events when an app action is triggered during replay. You must choose wisely when creating your validations or waits.

The sequence of events is:

### 1\. Pre-Waits

A Pre-Wait is a conditional statement that stops the action flow until the condition is met.

Use pre-waits:

*   To verify that the app is in the right state to receive inputs, for example, to check that proper elements are displayed on the screen.
    
*   To verify that any backend calls are finalized and proper data is returned.
    

### 2\. Inputs

Any inputs required by the action are loaded. Inputs can be static, as recorded, or dynamic (from seed data or scripts). Mandatory inputs vary depending on the type of action (tap, pan, type, etc.)

### 3\. Action

An Action (tap, pan, type, etc.) is sent to the device with the proper inputs.

### 4\. Post-Waits

A Post-Wait is a conditional statement that stops the action flow until the condition is met. Implicit waits are automatically added as needed, such as **waitForViewChange**, **waitForGestureComplete**, etc.

### 5\. Output

Outputs capture screen data, element properties, an XML hierarchy of the screen, etc., which are useful for tracing, debugging and reporting. A single action can have multiple outputs.

### 6\. Validation

Validations verify some content or an event occurred as expected, and have a corresponding failure action. Action validations can range from simple boolean conditions to more complex conditions. A single action can have multiple validations.

### 7\. Property Sets

Property Sets provide the ability to take text or data from the mobile app that you are testing and store it in a custom property for use in a subsequent action. Use Property Sets to store the value of an input, the text inside of a view, or even complex values, such as the result of a JavaScript expression, for later use.

## Debugging Best Practices

### Capture a screenshot and XML hierarchy for every failed action

For debugging purposes, we recommend using the **outputXmlHierarchy** and **captureScreenshot** Outputs command for your application framework to output the XML source content of the screen, as well as capturing a screenshot, so that the tester can see the screen as the user would when the failure occurs. These commands collect extra information, which may significantly slow down a CIU build, as well as add a lot of storage overhead in the test results and consume more wireless network bandwidth. Use the **Only if there is an error** checkbox to only capture this information when a failure occurs.

You can either add these commands individually to an action in your test case or at the Target level to capture the debugging information for every action within the clip.

To add an output command for an action in a test clip, after the action has been added to the clip:

1.  Click on the **Outputs** icon (magenta arrow).
    
2.  Click the **Add** icon (green plus sign) to create a new output command.
    
3.  In the **Command** drop-down box, select either **captureScreenshot** or **outputXmlHierarchy**.
    
4.  Enable the **Only if there is an error** check box.
    

To add the output command at the target level:

1.  Click the **Central** tab.
    
2.  In the left navigation pane, click **Targets**, which lists all targets (test device/test clip pair).
    
3.  Locate the test device/test clip pair you want to edit and double-click to open it in the **Target** editor.
    
4.  Under **Runtime Options**, click **Command applied to every action**.
    
5.  Under the **Output** sections in the main pane, click the Add icon (green plus sign) to create a new output command.
    
6.  In the **Command** drop-down box, select either **captureScreenshot** or **outputXmlHierarchy**.
    
7.  Enable the **Only if there is an error** check box.
    

![worddav80771c669a63014bd447c5e4ffb8da1f](/Images/appc/download/attachments/43298699/worddav80771c669a63014bd447c5e4ffb8da1f.png)  
After running a test clip in the **Composition** editor, highlight the action for which you want to review the captured screen contents in the output for the specified step. Navigate in the result, expand the Output section, and scroll down to the panel containing the captured screen/element contents:  
![worddav5add0f20c280b5d2f5e0903b64e5cb33](/Images/appc/download/attachments/43298699/worddav5add0f20c280b5d2f5e0903b64e5cb33.png)  
  
For XML output content, you can copy and paste the content to your favorite editor to search the content for the information that you are looking for.

### Enable Heads Up Display

Heads Up Display (HUD) displays visual enhancements during playback. It shows semi-transparent dots and color-coded panels that display useful clip element details about user actions on the device screen while playback occurs.  
It can be set at the Target level, or it can be enabled inside a clip by dragging and dropping a **hudOn** or **hudOff** action anywhere in the clip:

To enable at the Target level:

1.  Click the **Central** tab.
    
2.  In the left navigation pane, click **Targets**, which lists all targets (test device/test clip pair).
    
3.  Locate the test device/test clip pair you want to edit and double-click to open it in the **Target** editor.
    
4.  Click **Target Info**.
    
5.  Under the **Settings** sections, enable the **Enable HUD** checkbox.
    

![worddav47e306be31527f819b81fb456134580e](/Images/appc/download/attachments/43298699/worddav47e306be31527f819b81fb456134580e.png)  
  
  
To enable and disable HUD in a test clip, open the clip in the **Test Clip** editor, then:

1.  Click the **Messages / Actions** tab in the lower pane.
    
2.  In the **Actions** section, locate either the **hudOn** or the **hudOff** action and drag-and-drop it to the main pane, with the list of test steps, where you want to enable or disable HUD.
    

### Verify that elements are visible and present

In many of your clips, you will want to tap on an element, validate that an element is visible, or wait for an element to be visible before performing any other step in the test. Sometimes you will get an error because the element is not present or visible.

An element can be present in the XML hierarchy but not visible on the screen. Use either the **verifyElementVisible** Validation, or the **outputElementPresent** or **outputElementVisible** Output commands.

*   Use the appropriate output command to check whether the element is present.
    
*   Capture a screenshot on that action to help assess if the locator is visible at this particular step in the test.
    
*   Output the screen source contents to help assess if the element exists in the current page source contents or not.
    
*   Reference the examples above, in the Debugging section of this document, for suggestions on the appropriate Commands to output the screen source contents.
    

### Capture the text contents of a screen element

You can capture a screen element's text, then review it in the test composition results and optionally save it for later use. There are a number of things that you can do with the captured text. It could be parsed with JavaScript, saved as an array of property values, or used in subsequent steps or a loop.

To capture text, use the **storeElementText** or similar Property Sets command. You can either add the Property Sets to an existing action or add a **noOp** action to add the Property Sets. While creating a test clip in the clip editor:

1.  Click the **Messages / Actions** tab in the lower pane.
    
2.  In the **Actions** section, locate the **noOp** action and drag-and-drop it to the main pane, with the list of test steps, where to capture text.
    
3.  Click the **Selected** tab in the lower pane to edit the action.
    
4.  In the lower pane, click on the **Property Sets** icon (green checkmark).
    
5.  Click the **Add** icon (green plus sign) to create a new property sets command.
    
6.  In the **Command** drop-down, select **storeElementText** or a similar command.
    
7.  Next to the **Locator** text field, click the Locator Tool icon. A blue border appears around your application.
    
8.  In the application, click the element to capture text from. A textbox appears with several labels. Click the blue up arrow in the top-right corner of the box. The **Locator** text field populates with a value of the element.
    
9.  Use the **Property to set** field to optionally save the text to a property. Click the ISSE Editor icon next to it to open the ISSE editor.
    
10.  In the ISSE Editor, select either to save the text to a Target or Clip custom property or to save it to a property of a clip action. Note that you need to create a custom property before selecting it.
    

## Clip Building Best Practices

### Manage variable timing

When you transition between screens or perform an action, such as logging in to an account, the application might make a call to a backend server before proceeding. The response time of the backend may vary depending on many factors (network condition, volume on the server, etc.). You cannot rely on time delays for any wait actions.

For each screen transition, you must identify the right element(s) to wait on before proceeding with the following steps.  
There are two main scenarios when you transition from one screen to the next:

1.  You know the exact page you are transitioning to and there is only one possible page. In this case, use the **waitForElementVisible** Pre-Action Wait command on the next action to wait for an element in the next page.
    
2.  You do NOT know what page is next and there is more than one possible page. In this case, use the **waitForNotElementVisible** Post-Action Wait command for an element on the current screen to wait until that element disappears from the screen.
    

### Validation against elements outside the screen

Only elements that are displayed on the screen are part of the XML hierarchy. Elements that are NOT displayed on the screen are NOT part of the XML hierarchy and cannot be used with the validation or wait commands unless you scroll down to make them visible.

Use the **scrollToVisible** action to scroll until the view and element you specify are visible on the screen. If the element never becomes visible, the **scrollToVisible** action scrolls until the bottom of the screen is reached, marks the action as a non-fatal failure, and will not log a failure against the composition, so the **scrollToVisible** action does not guarantee that the element is visible after that action is completed

To add the **scrollToVisible** action to a test clip, while creating the test clip in the **Test Clip** editor:

1.  Click the **Messages / Actions** tab in the lower pane.
    
2.  In the **Actions** section, locate **scrollToVisible** action and drag-and-drop it to the main pane, with the list of test steps, where you want to scroll.
    
3.  Click the **Selected** tab in the lower pane to edit the action.
    
4.  Next to the **Scroll View** **Locator** text field, click the Locator Tool icon. A blue border appears around your application.
    
5.  In the application, click the view to scroll. A textbox appears with several labels. Click the blue up arrow in the top-right corner of the box. The text field populates with a value of the view, such as 'classname=UITableView'.
    
6.  Next to the **Element** **Locator** text field, click the Locator Tool icon. A blue border appears around your application.
    
7.  In the application, click the element you want to scroll to scroll. A textbox appears with several labels. Click the blue up arrow in the top-right corner of the box. The text field populates with a value of the element, such as 'classname=UILabel' or 'text="Row X"'.
    
8.  In the **Scroll Direction** drop-down, select to either scroll up or down.
    

You may need to manually enter the Scroll View Locator if the scroll view uses the entire screen.

![worddavfa01951a80e64f744137b5faa3ae1470](/Images/appc/download/attachments/43298699/worddavfa01951a80e64f744137b5faa3ae1470.png)

### Validations

As a general rule, the validations (particularly those associated with specific test case requirements) should always be in separate actions in the clip to make it easier to identify their location and check their status.

Add a **noOp** (No Operation) action to the location where you want to perform the validation(s), then rename the action to something meaningful (such as a test requirement step/validation identifier) and add the appropriate validation action(s):

1.  Click the **Messages / Actions** tab in the lower pane.
    
2.  In the **Actions** section, locate the **noOp** action and drag-and-drop it to the main pane, with the list of test steps, where to perform a validation.
    
3.  Click the **Selected** tab in the lower pane to edit the action.
    
4.  In the lower pane, click on the **Validations** icon (green checkmark).
    
5.  Click the Add icon (green plus sign) to create a new validation.
    

![worddav42620e7ca5e85aba8f01e8cfbf457be3](/Images/appc/download/attachments/43298699/worddav42620e7ca5e85aba8f01e8cfbf457be3.png)

### Group and name actions

The actions inside a clip can be named and grouped in a logical manner to make it more readable. To name an action, click the action's name label to make it editable and enter a new name for the action.

To group actions together:

1.  Click the **Add New Clip Element** button.
    
2.  Select **Add a New Group**. A new group appears.
    
3.  Drag-and-drop actions into the group.
    
4.  Click the name label of the group to make it editable and enter a name for the group.
    

In this example, actions are named and separated into two groups: "Environment Selection" and "Login".  
![worddavde6deb1e3fa8cbe117d96d2ebce7c12b](/Images/appc/download/attachments/43298699/worddavde6deb1e3fa8cbe117d96d2ebce7c12b.png)

### Conditional testing

Often a test needs to branch its execution based on various conditions. For example, on startup, an application may display a login form that needs to be submitted for the test to continue. For a test to do this, it first needs to determine if the login screen is being displayed and, if so, tap the Login button.

You use an [If-Then-Else](http://cloudlink.soasta.com/t5/Knowledge-Base/Creating-If-Then-Else/ba-p/684) clip element for this purpose. It checks for a condition and, if the condition is true, executes its "then" block statements. You can optionally add an "else " clause whose statements are executed if the condition is not met. The following steps demonstrate how to use an If-Then-Else clip to test for the presence of an application's login screen. If it's determined the login screen is being displayed, the login button is tapped.

![login-screen](/Images/appc/download/attachments/43298699/login-screen.png)

Locating a UI element on the screen is accomplished with two Test components: Accessors and Locators. An accessor is an action that returns a value–in this case, a reference to an on-screen UI element. A locator is a string you pass to the accessor identifying the UI element you want to access. Locators can [take several forms](http://cloudlink.soasta.com/t5/Knowledge-Base/TouchTest-Location-Strategies/ba-p/8768), such as a text string, an XPath expression, or runtime class name, to name a few.

**To use an If-Then-Else clip element**:

1.  In the Clip Editor, select **Add an If-Then-Else** from the **Add New Clip Element** menu.
    
    ![image2014-1-20_15_24_45](/Images/appc/download/attachments/43298699/image2014-1-20_15_24_45.png)
2.  In the new clip element, select the **Accessor** conditional type. An accessor makes an action’s return value usable—as a simple output, something to wait on, validate, or to use in a property set.
    
    ![image2014-1-20_16_2_48](/Images/appc/download/attachments/43298699/image2014-1-20_16_2_48.png)
    
3.  Select **isElementPresent** from the Accessor type menu and in the **Locator** field enter text=Please login. This corresponds to the text on the login screen of the test application (shown above).
    
    ![image2014-1-20_21_4_18](/Images/appc/download/attachments/43298699/image2014-1-20_21_4_18.png)
    
    If the isElementPresent accessor is located, we want to add an action to tap the **Login** button.
    
4.  Drag a **Tap** action from the **Messages/Actions** pane at the bottom of the screen and drop it inside the **THEN** block.
    
    ![image2014-1-20_20_28_48](/Images/appc/download/attachments/43298699/image2014-1-20_20_28_48.png)
5.  Expand the Tap input action and enter **text=Login** in the Locator input. This identifies the button to tap.
    
    ![tap-it](/Images/appc/download/attachments/43298699/tap-it.png)
6.  Save the clip.
    
7.  To add an **Else** clause, click the **Add** button ( ![image2014-1-20_17_26_30](/Images/appc/download/attachments/43298699/image2014-1-20_17_26_30.png) ) on the far right of the Then row. You can then add clip elements or actions to execute if the tested condition is not true.
    
    ![then_row](/Images/appc/download/attachments/43298699/then_row.png)

You can also create an If-Then-Else clip from an existing action, as opposed to dragging a Tap action from the Message/Actions tab. This technique is useful, for example, when you've recorded a test and later edit the test to include the If-Then-Else clip.

**To wrap an existing clip element in an If-Then-Else clip:**

1.  Right-click on the clip action you want to execute conditionally (in this case, an App Action that performs a Tap).
    
2.  Select **Create an If-Then-Else** from the context menu.
    
    ![if-else-right-click](/Images/appc/download/attachments/43298699/if-else-right-click.png)

The App Action is automatically wrapped in an If-Then-Else statement.

![image2014-1-21_13_47_56](/Images/appc/download/attachments/43298699/image2014-1-21_13_47_56.png)

**See also (from the Soasta Knowledge Base):**

*   [Creating If-Then-Else](http://cloudlink.soasta.com/t5/Knowledge-Base/Creating-If-Then-Else/ba-p/684)
    
*   [TouchTest Location Strategies](http://cloudlink.soasta.com/t5/Knowledge-Base/TouchTest-Location-Strategies/ba-p/8768)