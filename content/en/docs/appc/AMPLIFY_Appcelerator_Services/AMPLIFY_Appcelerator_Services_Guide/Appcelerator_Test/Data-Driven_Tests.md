{"title":"Data-Driven Tests","weight":"40"} 

Enterprise Subscription Required!

This AMPLIFY Appcelerator Services feature requires an Enterprise Subscription.

*   [Introduction](#Introduction)
    
*   [Create a Data-Driven Test](#CreateaData-DrivenTest)
    
    *   [Create the Seed Data](#CreatetheSeedData)
        
    *   [Create a Test Clip](#CreateaTestClip)
        
    *   [Modify the Test Clip to Use the Seed Data](#ModifytheTestCliptoUsetheSeedData)
        
    *   [Create a Test Composition to Loop over Seed Data](#CreateaTestCompositiontoLoopoverSeedData)
        

## Introduction

This page describes how to use static or dynamic data sets to input values into an application and validate values returned by the application. These directions assume you are familiar with Appcelerator Test and have already registered your device(s) and know how to create a test clip. For information on getting started with Appcelerator Test, see [Getting Started with Test](/docs/appc/AMPLIFY_Appcelerator_Services/AMPLIFY_Appcelerator_Services_Guide/Appcelerator_Test/Getting_Started_with_Test/).

## Create a Data-Driven Test

The following steps outline how to create a data-driven test.

1.  Login to the [AMPLIFY Platform](https://platform.axway.com/).
    
2.  On the Dashboard tile, select **Go to Dashboard**.
    
3.  Select an application to test from the Projects menu, and click on the **Test** tab.
    
4.  Create seed data with input values and validation values.
    
5.  Create a test clip that receives input data (manually) and presents the validation data on a screen, for example, entering a stock symbol and checking the company name.
    
6.  Modify the clip so that the input is retrieved from the seed data and to validate data from the seed data.
    
7.  Create a composition that loops over the seed data set.
    

### Create the Seed Data

You need to create seed data that contains input values and corresponding output values to validate your application. You can either manually create the data set or import data from a local or remote CSV file. If you want to import data from a remote source, skip to the "Create a Test Clip" section.

1.  In the Appcelerator Test Dashboard, in the **Central** tab, select the **New** button ![NewButton](/Images/appc/download/attachments/37523016/NewButton.png) (click on the down arrow), then **New Seed Data**. The **Seed Data Editor** tab opens.
    
2.  In the **Seed Data Editor** tab, enter a name and optionally a description for your data set.
    
3.  If you want to encrypt your data, check **The data should be encrypted** checkbox and enter a password in the key textbox. When using this option, you will be prompted for the password when editing your seed data and running your test clip.
    
4.  Choose to either import a CSV file or manually enter your data:
    
    *   To import a CSV file, click the **Import a CSV file** radio button, then click **Choose file** to select a CSV file to import.  
        If the first row contains column headings, check the **First row contains the column names** checkbox.
        
    *   To manually enter your data, click **Create a Seed Data Object**.
        
5.  Click the right green arrow button to proceed to the next step.
    
    *   If you chose to import data, your data will be populated. You can optionally edit the values.
        
    *   If you chose to manually enter your data, create your data columns and enter your data values.
        
6.  Once done, click **Finish**.
    

If you need to edit your seed data again, in the **Central** tab, click **Seed Data** in the left navigation pane, which lists all of your data sets in the right pane. Double-click the entry you want to edit to open the data with the **Seed Data Editor**.

### Create a Test Clip

First, create a basic test clip where you input a data value into the application then receive a result. To create a basic test case, see Test: Create a Test Clip. Be sure to create a validation step to check the value of the result.

For example, in this simple test, a user enters a value in a text field and clicks a button to submit it, then the application performs a calculation and displays a result.

![SampleApp](/Images/appc/download/attachments/43298701/SampleApp.png)

Resources/app.js

`function calcFib(val) {`

`if` `(val ==` `0` `|| val ==` `1``){`

`return`  `1``;`

`}`

`else` `{`

`return` `calcFib(val -` `1``) + calcFib(val -` `2``);`

`}`

`}`

`var intRegex = /^\d+$/;`

`function submitValue(){`

`var val = textField.value;`

`if``(val && intRegex.test(val)) {`

`label2.text = calcFib(val);`

`win2.open();`

`win1.close();`

`textField.value =` `""``;`

`}`

`}`

`var win2 = Ti.UI.createWindow({`

`backgroundColor:` `'white'`

`});`

`var label2 = Ti.UI.createLabel({`

`font: {fontSize:` `'24dp'``, fontWeight:` `'bold'``}`

`});`

`win2.add(label2);`

`var win1 = Ti.UI.createWindow({`

`backgroundColor:` `'white'`

`});`

`var label1 = Ti.UI.createLabel({`

`top:` `'10dp'``,`

`font: {fontSize:` `'14dp'``},`

`text:` `'Enter a positive integer:'`

`});`

`var textField = Ti.UI.createTextField({`

`width:` `'100dp'``,`

`height:` `'25dp'``,`

`borderWidth:` `'1'``,`

`top:` `'50dp'``,`

`keyboardType: Ti.UI.KEYBOARD_NUMBER_PAD`

`});`

`var button = Ti.UI.createButton({`

`title:` `'Calculate'``,`

`top:` `'100dp'`

`});`

`button.addEventListener(``'click'``, submitValue)`

`win1.add(label1);`

`win1.add(textField);`

`win1.add(button);`

`win1.open();`

To create the test clip for this example, once you have connected your device and started recording:

1.  In the application, click the text field. A tap action appears in the test clip.
    
2.  You can optionally edit the action to wait for the text field to appear before proceeding to enter data.
    
    1.  When the action is populated, a configuration box appears. Click on the Wait icon (set of hourglasses).
        
    2.  Under the **Waits before the action** section, click the Add icon (green plus sign) to create a new pre-action wait.
        
    3.  In the **Command** drop-down box, select **waitForElementPresent**.
        
    4.  Next to the **Locator** text field, click the Locator Tool icon ![LocatorIcon](/Images/appc/download/attachments/43298701/LocatorIcon.png) . A blue border appears around your application.
        
    5.  In the application, click the text field. A textbox appears with several labels. Click the blue up arrow in the top-right corner of the box. The **Locator** text field populates with a value similar to **classname=UIFieldEditor** or **classname=TiTextField**. You are done creating the pre-action wait condition.
        
        ![WaitForPreAction](/Images/appc/download/attachments/43298701/WaitForPreAction.png)
3.  In the application, enter a value in the text field, then click the **Calculate** button. The application opens a resulting value in a new window, and a type and tap action appear in the test clip.
    
4.  Edit the action to wait for a post-action condition and to check for a value.
    
5.  To create a post-action wait condition:
    
    1.  When the tap action is populated, a configuration box appears. Click on the Wait icon (set of hourglasses).
        
    2.  Under the **Waits after the action** section, click the Add icon (green plus sign) to create a new post-action wait.
        
    3.  In the **Command** drop-down box, select **waitForElementPresent**.
        
    4.  Next to the **Locator** text field, click the Locator Tool icon ![LocatorIcon](/Images/appc/download/attachments/43298701/LocatorIcon.png) . A blue border appears around your application.
        
    5.  In the application, click the result label. A textbox appears with several labels. Click the blue up arrow in the top-right corner of the box. The **Locator** text field populates with a value similar to **classname=UILabel**.
        
        ![WaitForPostAction](/Images/appc/download/attachments/43298701/WaitForPostAction.png)
6.  To create a validation condition:
    
    1.  In the configuration box, click on the Validations icon (green checkmark).
        
    2.  Click the Add icon (green plus sign) to create a new validate condition.
        
    3.  In the **Command** drop-down box, select **waitForElementPropertyValue**.
        
    4.  Next to the **Locator** field, click the Locator Tool icon ![LocatorIcon](/Images/appc/download/attachments/43298701/LocatorIcon.png) . A blue border appears around your application.
        
    5.  In the application, click the result label. A textbox appears with several labels. Click the blue up arrow in the top-right corner of the box. The **Locator** field populates with a value similar to **classname=UILabel**.
        
    6.  In the **Property** field, enter **text**.
        
    7.  In the field with **Exact Match** selected in the drop-down box, enter the value of the result.
        
        ![ValidationAction](/Images/appc/download/attachments/43298701/ValidationAction.png)
7.  To test that the clip has been set up to receive manually entered data and to check the value of the result. Run the test clip in a test composition to verify it works before proceeding to the next step.
    

The previous procedure is only a simple example of using pre-action wait conditions, post-action wait conditions and validation condition. There are many different commands you can use for these actions.

### Modify the Test Clip to Use the Seed Data

Next, modify the test clip to use the seed data. You need to add the seed data as a custom property of the test clip and change the input value and result value to use the seed data.

First, add the seed data to the test clip:

1.  If your test clip is not already opened in the **Clip Editor** tab, in the **Central** tab, click **Clips** in the left navigation pane, which lists all of your test clips. Double-click the clip you want to edit to open it in the Clip Editor.
    
2.  Click the **Properties** tab.
    
3.  Select **Clip Custom Properties**.
    
4.  Click the Add icon (green plus sign) to create a new custom property.
    
5.  If you desire, change the name of the property. By default, the first name is **clipProp**.
    
6.  To use seed data that you either created manually or imported from a local CSV file:
    
    1.  In the **Value** drop-down box, select **Seed Data: Repository**.
        
    2.  In the **Seed data object** drop-down box, select the seed data object you created.
        
    3.  Skip to the next step pertaining to remote CSV data.
        
7.  To use seed data from a remote CSV file:
    
    1.  In the **Value** drop-down box, select **Seed Data: Repository**.
        
    2.  In the **URL** field, enter the URL of where the data file is located. Check the **Column names are in the first-row** check box if the first row of the file is the column headings.
        
8.  Scroll to the bottom of the custom properties to the **Data** section.
    
9.  In the **Row traversal type** drop-down box, select **Sequential**.
    
10.  In the **EOF action** drop-down box, select **Stop Track and Drain**, which will try to run the track one last time when it reaches the end of the seed data, but returns a **Completed Result** when the composition finishes.
    
    ![ClipProperty](/Images/appc/download/attachments/43298701/ClipProperty.png)
    

Next, use the seed data to input data into the application:

1.  Double-click the action where the test clip enters the input value. This should be a "type" action.
    
2.  Make sure **Inputs** is selected in the lower pane.
    
3.  Erase the input value in the **Text** field and click the ISSE Editor icon ![IsseIcon](/Images/appc/download/attachments/43298701/IsseIcon.png) next to it to open the ISSE editor.
    
4.  Make sure **Property** is selected in the top row and **Custom** is selected in the right section of the editor.
    
5.  In the right section of the editor, select the property with your seed data and in the **Modifier(s)** drop-down box, select the column you want to use. If the column has a title, this is the name of the column (may appear as random characters for encrypted data). If the column is not titled, you need to select the column number.
    
6.  Click the **OK** button. The field now contains a property.
    
    ![IsseEditor](/Images/appc/download/attachments/43298701/IsseEditor.png)
    

Finally, use the seed data to validate the result from the application:

1.  Double-click the action where the test clip validates the result value. In the simple example, this is in the last "tap" action.
    
2.  Select **Validations** in the lower pane.
    
3.  Erase the result value in the field and click the ISSE Editor icon ![IsseIcon](/Images/appc/download/attachments/43298701/IsseIcon.png) next to it to open the ISSE editor.
    
4.  Make sure **Property** is selected in the top row and **Custom** is selected in the right section of the editor.
    
5.  In the right section of the editor, select the property with your seed data and in the **Modifier(s)** drop-down box, select the column you want to use. If the column has a title, this is the name of the column (may appear as random characters for encrypted data). If the column is not titled, you need to select the column number.
    
6.  Click the **OK** button. The field now contains a property.
    

To verify the test clip is using seed data correctly, run the test clip in a test composition. The test composition runs the test clip once with the first row of the seed data.

### Create a Test Composition to Loop over Seed Data

Finally, you need to create a test composition that loops over the test clip. You need to modify the band and track properties before adding the test clip. Do not use the **Open in Test Composition** or **Play in Test Composition** options from the Test Clip Editor. You cannot edit the band properties once the test clip has been added.

1.  In the **Central** tab, select the **New** button ![NewButton](/Images/appc/download/attachments/37523016/NewButton.png) (click on the down arrow), then New Test Composition. The **Test Composition** Editor tab opens .
    
2.  Right-click on the **Sequenced Band** label and select **Change timing type**. This changes the band from sequenced to timed, which allows the track to be looped.
    
    ![BandTiming](/Images/appc/download/attachments/43298701/BandTiming.png)
3.  Click the **Properties** tab in the lower pane.
    
4.  Check the **Enable Repeat** checkbox.
    
5.  In the **Repeat Method** drop-down box, select **Infinite**, which loops over the seed data until the EOF event.
    
    ![TrackProperties](/Images/appc/download/attachments/43298701/TrackProperties.png)
6.  Click the **Composition Build** tab in the lower pane.
    
7.  Locate and drag the test clip to the test track or band to add it to the test composition.
    
8.  Click the Play icon to start the test.
    

The editor switches to the **Play** tab. The test clip executes repeatedly until the seed data runs out.