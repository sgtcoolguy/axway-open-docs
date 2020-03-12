{"title":"Integrating Test with Jenkins","weight":"50"} 

# Integrating Test with Jenkins

Enterprise Subscription Required!

This AMPLIFY Appcelerator Services feature requires an Enterprise Subscription.

*   [Introduction](#Introduction)
    
*   [Integration Overview](#IntegrationOverview)
    
    *   [Create an Application with Appcelerator Test Enabled](#CreateanApplicationwithAppceleratorTestEnabled)
        
    *   [Setup a Device Farm](#SetupaDeviceFarm)
        
    *   [Setup the Test Composition](#SetuptheTestComposition)
        
    *   [Setup Jenkins to Use Appcelerator Test](#SetupJenkinstoUseAppceleratorTest)
        
        *   [Titanium Prerequisites](#TitaniumPrerequisites)
            
        *   [Install and Configure the SOASTA Plugin](#InstallandConfiguretheSOASTAPlugin)
            
        *   [Install the iOS App Installer Utility](#InstalltheiOSAppInstallerUtility)
            
        *   [Install the scommand Utility](#InstallthescommandUtility)
            
    *   [Setup the Continuous Integration Job](#SetuptheContinuousIntegrationJob)
        
        *   [Example iOS Device Shell Script](#ExampleiOSDeviceShellScript)
            
        *   [Example iOS Simulator Shell Script](#ExampleiOSSimulatorShellScript)
            
        *   [Example Android Device Shell Script](#ExampleAndroidDeviceShellScript)
            
        *   [Example Android Emulator Shell Script](#ExampleAndroidEmulatorShellScript)
            
    *   [View Test Results](#ViewTestResults)
        
*   [References](#References)
    

## Introduction

This guide walks through the steps of integrating the Appcelerator Test with the Jenkins continuous integration tool. The primary focus of this document is to integrate Appcelerator Test with Jenkins and briefly discusses how to set up Jenkins to build a Titanium application and assumes you have a working Jenkins setup. These directions assume the same computer builds the application, installs it to a mobile device and runs the Jenkins tool.

For information on getting started with Appcelerator Test, see [Appcelerator Test](/docs/appc/AMPLIFY_Appcelerator_Services/AMPLIFY_Appcelerator_Services_Guide/Appcelerator_Test/).

For information on getting started with Jenkins, see [Use Jenkins](https://wiki.jenkins-ci.org/display/JENKINS/Use+Jenkins).

## Integration Overview

The following steps outline how to integrate Appcelerator Test with Jenkins with details discussed further in the sections below.

1.  Create an Application with Appcelerator Test Enabled
    
2.  Setup a Device Farm (or use the Android Emulator and iOS Simulator)
    
    1.  Register devices (see [Appcelerator Test](/docs/appc/AMPLIFY_Appcelerator_Services/AMPLIFY_Appcelerator_Services_Guide/Appcelerator_Test/) for more information)
        
    2.  Connect devices to the farm server via USB
        
    3.  Connect devices to Appcelerator Test (see [Appcelerator Test](/docs/appc/AMPLIFY_Appcelerator_Services/AMPLIFY_Appcelerator_Services_Guide/Appcelerator_Test/) for more information)
        
    4.  Verify the devices do not fall asleep (auto-lock off for iOS devices)
        
3.  Setup the Test Composition (see [Appcelerator Test](/docs/appc/AMPLIFY_Appcelerator_Services/AMPLIFY_Appcelerator_Services_Guide/Appcelerator_Test/) for more information)
    
4.  Setup the Jenkins Server to Use Appcelerator Test
    
    1.  Install and Configure the SOASTA plugin
        
    2.  Install the iOS App Installer (for testing on iOS devices)
        
    3.  Install the Command Utility
        
5.  Setup the CI Job
    

### Create an Application with Appcelerator Test Enabled

The Appcelerator Test service needs to be always enabled for your project in order to use it. If you are using a version control system, such as Git or CVS, to make it easier to perform continuous builds, save the Appcelerator Test modules and tiapp.xml file modifications to your project as part of your codebase. Save the following directories and the tiapp.xml file to your project:

*   modules/android/com.soasta.touchtest
    
*   modules/iphone/com.soasta.touchtest
    
*   plugins/com.soasta.touchtest.android
    

If you do not want to save these files as part of your project, you can copy in the Appcelerator Test modules and modify the tiapp.xml file to enable Appcelerator Test. This requires that the application was created with Appcelerator Studio to generate a Test project with GUIDs in the Appcelerator Test dashboard. This GUID needs to be added to the tiapp.xml file to connect it with Appcelerator Test. For details about the tiapp.xml modifications, see [Platform Services](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Titanium_Development/Platform_Services/).

### Setup a Device Farm

To set up a device farm, you need to register each device with Appcelerator Test and connect them to a server using a USB connection. You need a USB connection to install the application to the device using the Android Debug Bridge or iOS App Installer utilities. For iOS testing, the server needs to be running Mac OS X. For information on registering devices with Appcelerator Test, see [Test: Register a Device or Simulator](/docs/appc/AMPLIFY_Appcelerator_Services/AMPLIFY_Appcelerator_Services_Guide/Appcelerator_Test/#RegisteraDeviceorSimulator).

Each device needs to have a WiFi or data connection enabled to connect to Appcelerator Test:

*   For Android devices, launch the TouchTest Agent.
    
*   For iOS devices, launch Safari and log in to [http://appctest-2.appcelerator.com/concerto/touchtest](http://appctest-2.appcelerator.com/concerto/touchtest.).
    

Verify the devices do not fall asleep:

*   For Android devices, as long as the device is plugged in (charging) and the TouchTest Agent is on screen, the device does not fall asleep.
    
*   For iOS devices, verify that auto-lock is off. In **Settings**, navigate to **General** > **Auto-Lock** and select **Never**.
    

You need a list of serial numbers for each Android device and UUIDs or device name for each iOS device. To retrieve a list:

*   For Android devices, use the adb devices command to output a list of all connected devices with their serial numbers in the terminal.
    
*   For iOS devices, use the Xcode Organizer and click on each individual device to get the **Identifier**.
    

Rather than using a device, you can use the Android emulator and iOS simulator, which can be launched by the build server. Remember to register them with Appcelerator Test.

### Setup the Test Composition

For each device in your test farm, you need to create a test composition that runs on that device. Note that to select a device for a composition it needs to be connected to Appcelerator Test.

Before creating a test composition, you need to create a test clip for each device type, that is, Android, iPhone, and iPad. For information on creating a test composition, see Test.

Remember the name of the test composition and the device used to run the test composition. You need this information for the build script.

### Setup Jenkins to Use Appcelerator Test

#### Titanium Prerequisites

To build the application, the user account that builds the application needs permission to:

*   Run Titanium CLI commands
    
*   Access the Titanium SDK and third-party SDK tools (Xcode and Android SDK)
    
*   Access the keychain with an Apple Development Certificate and Profile to build for an iOS device
    

Log in to the user account and verify you can build an Android and iOS application for a device with the Titanium CLI.

For easier troubleshooting, set the CLI log level to trace to output more debug information: titanium config logLevel trace

To see this information, click **Console Output** when viewing a specific Jenkins build.

#### Install and Configure the SOASTA Plugin

1.  From the Jenkins start page, click **Manage Jenkins.**
    
2.  Click **Manage Plugin** **s**.
    
3.  Click the **Available** tab.
    
4.  Search for **SOASTA CloudTest Plugin** and enable it for installation.
    
5.  Click **Install without Restart**.
    
6.  After the plugin has been installed, from the Jenkins start page, click **Manage Jenkins.**
    
7.  Click **Configure System.**
    
8.  Under the **CloudTest Servers** section, in the **CloudTest URL** textbox, enter "http://appctest-2.appcelerator.com/concerto/".
    
9.  In the **User Name** and **Password** text boxes, enter your Appcelerator Test credentials.
    
10.  Click the **Test Connect** button to verify that the connection to Appcelerator Test works.
    

If the test connection passes, you are done with this section. If not, reenter your Appcelerator Test credential and retest the connection.

If you do not see the SOASTA CloudTest Plugin in the list of available plugins:

1.  Login to the [AMPLIFY Platform](https://platform.axway.com/).
    
2.  On the Dashboard tile, select **Go to Dashboard**.
    
3.  Download the Jenkins plugin from [http://appctest-2.appcelerator.com/concerto/downloads/jenkinsplugin/cloudtest.hpi](http://appctest-2.appcelerator.com/concerto/downloads/jenkinsplugin/cloudtest.hpi).
    
4.  In the Jenkins Manage Plugin page, under the **Update Plugin** section, click **Choose File**. A dialog appears.
    
5.  In the dialog, navigate to and select the **cloudtest.hpi** file and click **OK.**
    
6.  Click the **Upload** button to start the installation process.
    

After the installation successfully completes, continue the directions above at step #6.

#### Install the iOS App Installer Utility

To install your application to iOS devices, you need to install the iOS App Installer utility to the node that has your iOS devices connected to it.

1.  Login to the [AMPLIFY Platform](https://platform.axway.com/).
    
2.  On the Dashboard tile, select **Go to Dashboard**.
    
3.  Download the iOS App Installer utility from [http://appctest-2.appcelerator.com/concerto/downloads/mobile/iOSAppInstaller.zip](http://appctest-2.appcelerator.com/concerto/downloads/mobile/iOSAppInstaller.zip).
    
4.  Unzip and copy the contents of the archive where it can be accessed by a user to install the application to the device, for example, /opt/share.
    

Run the command with the user account that is going to install the application to the device to verify it works. Make a note of the installation path. You need this information for the build script.

#### Install the scommand Utility

The scommand utility contacts Appcelerator Test to start the test composition or run other test commands.

1.  Login to the [AMPLIFY Platform](https://platform.axway.com/).
    
2.  On the Dashboard tile, select **Go to Dashboard**.
    
3.  Download the utility from [http://appctest-2.appcelerator.com/concerto/downloads/scommand/scommand.zip](http://appctest-2.appcelerator.com/concerto/downloads/scommand/scommand.zip).
    
4.  Unzip and copy the contents of the archive where it can be accessed by a user to initiate the test, for example, /opt/share.
    

Run the command with the user account that is going to initiate the test to verify it works. Make a note of the installation path. You need this information for the build script.

### Setup the Continuous Integration Job

Finally, create a CI job that calls a script to run your test composition after it has been successfully built and installed to the device. The sample scripts below shows how to build the application, install it to an Android or iOS device, then call Appcelerator Test to execute the test composition. The script creates an XML file with the results of the command. This script assumes that the application is built and installed to the device on the same node.

1.  From the Jenkins start page, click **New Job**.
    
2.  Enter a name for your job in the **Job name** textbox.
    
3.  Select **Build a free-style software project** from the list of job options.
    
4.  Click **OK.**
    
5.  Enter a description for your job and configure the **Source Code Management** and **Build Trigger** sections for your setup and tools.
    
6.  Under the **Build** section, click the **Add build step** drop-down and select **Execute shell**.
    
7.  In the **Command** text field, copy and paste one of the example scripts below, then modify it for your setup.
    
8.  Under **Post-build Actions** section, click the **Add post-build action** drop-down and select **Publish JUnit test result report**.
    
9.  In the **Test report XMLs** textbox, enter the path to the result files. For the example scripts, enter "testresults/\*.xml".
    
10.  Enable **Include links to SOASTA CloudTest dashboards**. The **CloudTest URL** textbox appears below.
    
11.  In the **CloudTest URL** textbox, enter "http://appctest-2.appcelerator.com/concerto/".
    
12.  Click **Save**.
    

Manually start a build to test the CI job. If the test passes, you have successfully integrated Appcelerator Test with Jenkins. If not, review the console logs to troubleshoot the issue and run a build again.

#### Example iOS Device Shell Script

`## Clean the previous build`

`/usr/local/bin/titanium clean --project-dir $WORKSPACE`

`## Build` `for` `an iOS device (mininum command-line options specified)`

`/usr/local/bin/titanium build --platform ios --target device --developer-name` `'Joe User (AAA00AA0AA)'` `--pp-uuid` `'<UUID>'` `--project-dir $WORKSPACE`

`## Install to Device using the iOS App Installer`

`## By` `default``,` `this` `command deploys to all connected devices`

`## Specify --udid <device_id> or --device <device_name> to deploy to a specific device`

`/opt/share/iOSAppInstaller/bin/ios_app_installer --ipa $WORKSPACE/build/iphone/build/Debug-iphoneos/TestSoasta.ipa`

`mkdir -p testresults`

`## Run the Test Composition called /DataTest/TestiOSDevice`

`/opt/share/scommand/bin/scommand cmd=play url=http:``//appctest-2.appcelerator.com/concerto username=juser@appcelerator.com password=<password> type=composition name='/DataTest/TestiOSDevice' wait format=junitxml > testresults/$BUILD_NUMBER.xml`

#### Example iOS Simulator Shell Script

`## Clean the previous build`

`/usr/local/bin/titanium clean --project-dir $WORKSPACE`

`## Build`

`/usr/local/bin/titanium build --platform ios --project-dir $WORKSPACE --build-only`

`## Install to Simulator using the xcrun simctl part of Xcode command-line tools`

`## Use the` `'xcrun simctrl list'` `command to get the simulator ID`

`xcrun simctl boot <SIMULATOR_ID>`

`xcrun simctl install booted $WORKSPACE/build/iphone/build/Debug-iphonesimulator/TestSoasta.app`

`xcrun simctl shutdown <SIMULATOR_ID>`

`## Launch the Simulator`

`open -a` `"iOS Simulator"` `--args -CurrentDeviceUDID <SIMULATOR_ID>`

`mkdir -p testresults`

`## Run the Test Composition called /DataTest/TestiOSEmulator`

`/opt/share/scommand/bin/scommand cmd=play url=http:``//appctest-2.appcelerator.com/concerto username=juser@appcelerator.com password=<password> type=composition name='/DataTest/TestiOSEmulator' wait format=junitxml > testresults/$BUILD_NUMBER.xml`

#### Example Android Device Shell Script

`## Clean the previous build`

`/usr/local/bin/titanium clean --project-dir $WORKSPACE`

`## Build` `for` `an Android device (mininum command-line options specified)`

`/usr/local/bin/titanium build --platform android --target device --project-dir $WORKSPACE --build-only`

`## Install to Device using the Android Debug Bridge`

`/opt/share/android-sdk-macosx/platform-tools/adb -s <device_serial_number> install -r $WORKSPACE/build/android/bin/app.apk`

`mkdir -p testresults`

`## Run the Test Composition called /DataTest/TestAndroidDevice`

`/opt/share/scommand/bin/scommand cmd=play url=http:``//appctest-2.appcelerator.com/concerto username=juser@appcelerator.com password=<password> type=composition name='/DataTest/TestAndroidDevice' wait format=junitxml > testresults/$BUILD_NUMBER.xml`

#### Example Android Emulator Shell Script

`## Launch the Android emulator`

`/opt/share/android-sdk-macosx/tools/emulator -avd <emulator_name> &`

`## Clean the previous build`

`/usr/local/bin/titanium clean --project-dir $WORKSPACE`

`## Build` `for` `Android emulator`

`/usr/local/bin/titanium build --platform android --project-dir $WORKSPACE --build-only`

`## Install to Emulator using the Android Debug Bridge`

`/opt/share/android-sdk-macosx/platform-tools/adb -s emulator-``5554` `install -r build/android/bin/app.apk`

`mkdir -p testresults`

`## Run the Test Composition called /DataTest/TestAndroidEmulator`

`/opt/share/scommand/bin/scommand cmd=play url=http:``//appctest-2.appcelerator.com/concerto username=juser@appcelerator.com password=<password> type=composition name='/DataTest/TestAndroidEmulator' wait format=junitxml > testresults/$BUILD_NUMBER.xml`

### View Test Results

After a build, you can view the test results and report.

1.  When viewing a specific Jenkins build, click **Test Result**.
    
2.  In the **All Test** table, click on **(root)** and drill down to the name of the test composition. For example, if your test composition is called **/DataTest/TestAndroidDevice**, you would need to click **(root)**, then **DataTest** and finally **TestAndroidDevice** to get to the results page.
    
3.  The test results display a status title, such as "Passed", "Fixed, "Regression" or "Failed".
    
4.  Below the status, click the **Click here to see the SOASTA CloudTest dashboard for this test** link to show a frame that contains the report of the test. You may be prompted to log in before viewing the report.
    

## References

[SOASTA Appcelerator TouchTest Jenkins Tutorial](http://cdn.soasta.com/productresource/download/SOASTA_TouchTest_Jenkins_Tutorial.pdf)