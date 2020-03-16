{"title":"iOS Module Project","weight":"30"}

* [Introduction](#introduction)

* [Prerequisite](#prerequisite)

* [Project structure](#project-structure)

    * [Titanium .xcconfig file](#titanium-.xcconfig-file)

    * [Module .xcconfig file](#module-.xcconfig-file)

    * [Manifest file](#manifest-file)

* [CLI tasks](#cli-tasks)

    * [Create a new module project](#create-a-new-module-project)

    * [Build and package the module](#build-and-package-the-module)

* [Studio tasks](#studio-tasks)

    * [Create a new module project](#create-a-new-module-project)

    * [Build and package the module](#build-and-package-the-module)

* [Test the module](#test-the-module)

    * [Link the test application and the module projects](#link-the-test-application-and-the-module-projects)

* [Add a third-party framework](#add-a-third-party-framework)

* [Bundle module assets](#bundle-module-assets)

* [Format / Lint source-code](#format-/-lint-source-code)

* [Distribute your module through the Appcelerator Marketplace](#distribute-your-module-through-the-appcelerator-marketplace)

## Introduction

This guide covers how to manage your module project as well as how to add third-party frameworks and bundle assets with your module.

## Prerequisite

In order to develop iOS modules, you need to have your environment setup to build iOS applications with the Titanium SDK.

* To setup Titanium, see [Setting up Studio](/docs/appc/Titanium_SDK/Titanium_SDK_Getting_Started/Installation_and_Configuration/Setting_up_Studio/).

* To setup your environment for iOS, see [Installing the iOS SDK](/docs/appc/Titanium_SDK/Titanium_SDK_Getting_Started/Installation_and_Configuration/Installing_Platform_SDKs/Installing_the_iOS_SDK/).

## Project structure

When you create a new project, it generates the following directories and files. Titanium expects to find files in certain directories with a specific naming convention.

<table class="confluenceTable"><thead class=""></thead><tfoot class=""></tfoot><tbody><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><strong>Filename / Directory</strong></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p><strong>Description / Purpose</strong></p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt>.gitignore</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>A special <tt>.gitignore</tt> file used by the revision control system git to instruct it to ignore certain temporary files and directories. This file is not distributed with your module. This file can be safely ignored if you are not using git.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt>README</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>The file that gives a short explanation of the module project. This file is not distributed with your module.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt>assets</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>The directory where you should place module assets, such as images.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt>documentation</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>The directory where you should place your module documentation for end-users. The file <tt class="">index.md</tt> is a Markdown-formatted template file that you should use when writing your module documentation. You may also write your documentation using the <a class="document-link" href="#!/guide/TDoc_Specification">TDoc Specification</a>. This is only required for module distributed in the Appcelerator Marketplace. You can safely ignore this directory if you do not intend to distribute your module.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt>example</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>The directory where your module example(s) should go. The file <tt>app.js</tt> will be generated to include a sample loading of your module in a test window. This file can be used for quickly testing your module as well as give an example to end-users on how to use your module. This directory is distributed with your module.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt>ios/Classes</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>The directory where you Objective-C headers and implementation classes should go, used by the Xcode compiler. By default, when you create a new project, you are given a boiler plate module class (<tt class="">ModuleIdModule.h</tt> and <tt class="">ModuleIdModule.m</tt>) and the auto-generated module assets class (<tt class="">ModuleIdModuleAssets.h</tt> and <tt class="">ModuleIdModuleAssets.m</tt>). These files are not distributed with your module. For information about these files, see <a class="document-link" href="#!/guide/iOS_Module_Architecture">iOS Module Architecture</a>.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt>ios/&lt;MODULE_ID&gt;_Prefix.pch</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>The pre-compiled header file used by the Xcode compiler. This file is not distributed with your module.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><del class=""><tt>ios/build.py</tt></del></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p><del class="">This file is a script that will compile and package your module for usage and distribution.</del> Usage of this script has been replaced with <tt>appc run -p ios --build-only</tt>.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt>ios/manifest</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>A special file that describes metadata about your module and used by the Titanium compiler. This file is required and is distributed with your module.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt>ios/module.xcconfig</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>A special file used by Xcode when your module is compiled in an end-user Titanium application which references your module.<br>This file is a Xcode configuration file which can setup special compiler and linker directives that are specific to your module. This file is distributed with your module.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt>ios/platform</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Directory to place native frameworks and (static) libraries in. Examples are <tt class="">.framework</tt> and <tt>.a</tt> files.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt>ios/Resources</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Directory for platform-specific assets. This is analogous to the <tt class="">app/platform</tt> directory in a standard Titanium application project, and contains platform-specific assets that are not processed by Titanium but copied over to the module's package. For example, place any third-party frameworks or bundles you want to use with the module in this folder. <i>Note</i>: This directory will only be recognized in Titanium Mobile 5.2.0.GA and later.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt>ios/test.xcodeproj</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>The directory which contains your Xcode project. Open this directory to launch your module project in Xcode. This directory is not distributed with your module.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt>ios/timodule.xml</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Titanium module configuration file. The format is described in <a class="document-link" href="#!/guide/tiapp.xml_and_timodule.xml_Reference">tiapp.xml and timodule.xml Reference</a>. This file is not currently supported by iOS modules.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt>ios/titanium.xcconfig</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>A special file used by Xcode when your module is compiled when building your module. This file is a Xcode configuration file which can setup special compiler and linker directives that are specific to your module. This file is not distributed with your module and only used during module development.</p></td></tr></tbody></table>

The CLI generates a module project containing multiple platforms. The module contains platform-dependent folders, for example, ios , that contain platform-specific resources and common folders for assets, documentation and examples.

### Titanium .xcconfig file

The titanium.xcconfig file is used when compiling your module for packaging. It defines the following environment variables:

* TITANIUM\_SDK\_VERSION: Version of the Titanium SDK to build the module library.

* TITANIUM\_SDK: Path to the Titanium SDK.

* TITANIUM\_BASE\_SDK: Path to the Titanium SDK iOS header files. Do not modify.

* TITANIUM\_BASE\_SDK2: Path to the Titanium SDK iOS TiCore header files. Do not modify.

* TITANIUM\_BASE\_SDK3: Path to the Titanium SDK iOS JavaScriptCore header files. Do not modify.

* HEADER\_SEARCH\_PATHS: Path to the Titanium SDK header files. Do not modify.

Normally, you do not need to edit this file once it is created. If you delete the Titanium SDK referenced by the file, you need to update the TITANIUM\_SDK\_VERSION and TITANIUM\_SDK variables to use another Titanium SDK to build the module.

### Module .xcconfig file

If your module needs a special Framework, other system library or special compiler directives, you can use the module's xcconfig file to define them. The module.xcconfig is used by the application compiler when the application is built and your module is referenced. This allows you to control the compiler directives used during this process.

For a list of variables you can add to this file, see [Xcode Build Setting Reference.](https://developer.apple.com/legacy/library/documentation/DeveloperTools/Reference/XcodeBuildSettingRef/1-Build_Setting_Reference/build_setting_ref.html#//apple_ref/doc/uid/TP40003931-CH3-SW105)

For example, if you include the iOS 11 CoreML framework with your module, you need to modify the OTHER\_LDFLAGS variable to include the framework. To not overwrite the Titanium application's OTHER\_LDFLAGS variable, add $(inherited).

`OTHER_LDFLAGS=$(inherited) -framework CoreML`

### Manifest file

Titanium module metadata is described in a special text file named manifest. This file is a simple key/value property format.

Before you distribute your module, you must edit this manifest and change a few values. Some of the values are pre-generated and should not be edited. These are noted with the comment before them. In the manifest file, any line starting with a hash character (#) is ignored. The following are the descriptions of each entry in the manifest:

<table class="confluenceTable"><thead class=""></thead><tfoot class=""></tfoot><tbody><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><strong>Key</strong></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p><strong>Description/Purpose</strong></p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p>version</p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>This is the version of your module. You should change this value each time you make major changes and distribute them. Version should be in the dotted notation (X.Y.Z) and must not contain any spaces or non-number characters.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p>apiversion</p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>The internal module API version of the SDK that is required to build this module. Currently this is at version 2 for iOS modules which is supported by all recent versions of the Titanium SDK. By default, this will be automatically set to the module API version of the SDK that was used when creating your module.</p><p>You only need to ever change this if a new SDK has internal breaking changes to the module API. In the rare event that the module API did change, you need to migrate the module to the new module API and then update this property to match the API version of the SDK you are trying to build with.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p>architectures</p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>The binary architectures the module supports as a delimited list. Example: armv7 arm64 i386 x86_64</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p>description</p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>This is a human-readable description of your module. It should be short and suitable for display next to your module name.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p>author</p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>This is a human-readable author name you want to display next to your module. It can simply be your personal name, such as "Jon Doe" or an organizational name such as "Axway Appcelerator".</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p>license</p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>This is a human-readable name of your license. You should use a short description such as "Apache Public License", "MIT" or "Commercial".</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p>copyright</p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>This is a human-readable copyright string for your module. For example, "Copyright (c) 2010-Present by Axway Appcelerator, Inc."</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p>name</p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>This is a read-only name of your module that is generated when you created your project. You must not edit this value.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p>moduleid</p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>This is a read-only module id of your module that is generated when you created your project. You should not edit this value. NOTE: you must generate a unique id. We recommend using your reverse-DNS company name + module_name as a pattern to guarantee uniqueness. The Titanium Marketplace will only allow unique module ids when distributing modules. If you must edit this value, you must also edit the value in your module implementation file.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p>guid</p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>This is a read-only unique module id for your module that is generated when you created your project. You must not edit this value.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p>platform</p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>This is a read-only platform target of your module that is generated when you created your project. You must not edit this value.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p>minsdk</p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Indicates the minimum version of the SDK your module is compatible with. Users of your module will need to build their app with the specified SDK version (or later versions). This will be set to the Titanium SDK version that was used when creating your module by default. Adjust this if you change your module later on and use features that were introduced in new versions of the Titanium SDK or you know that your module is compatible with older versions of Titanium SDK as well.</p></td></tr></tbody></table>

## CLI tasks

### Create a new module project

To create a new module project, run the following Titanium CLI command:

`appc new -d` `/PATH/TO/WORKSPACE` `-n <MODULE_NAME> --``id` `<MODULE_ID>`

`### when prompted for the project type, select "Titanium Module"`

`### Example`

`$ appc new -p ios -n` `test` `--``id` `com.example.``test`

`Appcelerator Command-Line Interface, version 7.0.2`

`Copyright (c) 2014-2018, Appcelerator, Inc. All Rights Reserved.`

`? What` `type` `of project are you creating?`

`Native App`

`Arrow App`

`❯ Titanium Module`

`Apple Watch App`

If you omit any of the options, the CLI will prompt you to enter them.

### Build and package the module

To build and package a module, run the appc run -p ios --build-only command inside the ios directory.

`cd` `/<PATH_TO_MODULE_PROJECT>/<MODULE_NAME>``/ios`

`ti build -p ios --build-only`

After the build completes, you should have a ZIP file in the iphone directory and see the following message in the console:

`** BUILD SUCCEEDED **`

With the ZIP file, you can either:

* Uncompress it in the Titanium SDK home path to install the module globally for all your Titanium applications

* Uncompress it in a Titanium project's parent directory to install the module locally for that one Titanium application

* Distribute the ZIP file

## Studio tasks

### Create a new module project

1. From the menu, select **File** > **New** > **Mobile Module Project** to open the **New Mobile Module Project** dialog.

2. In the **Project name** field, enter a name for the module.

3. In the **Module Id** field, enter a module ID for the module.

4. In **Deployment Targets**, select **iOS**.

5. Click **Next.**

6. In the **Module Manifest File** page, enter information about your module, such as the license information, version number, etc. You can also edit this information in the manifest file later.

7. Click **Finish**.

### Build and package the module

1. Select your module folder in the **Project Explorer** view.

2. Verify **Package** and **iOS Module** are displayed in **Launch Mode** and **Launch Target**, respectively.

3. Click the Package icon to open the **Package iOS Module** dialog.

4. In **Output Location**, select either

    1. **Titanium SDK** to install the module in the Titanium SDK home path to be accessed by any Titanium application

    2. **Mobile App Project** and choose an application to install the module locally that can be accessed by one that Titanium application

    3. **Location** and enter a path to copy the ZIP file to for distribution

5. Click **Finish**.

## Test the module

To test a module:

1. Create a new Titanium Classic or Alloy project.

2. Install the module to either the Titanium SDK home directory or in the project.

3. Add the module as a dependency to the project.

4. Load the module and make module API calls.

### Link the test application and the module projects

To make it easier to debug your module, you can link the module to the test application. Then you can run the test application, which will rebuild the module project. You need to build the test application and module project at least once before proceeding.

1. Close the module project if it is open in Xcode.

2. Open the test application's Xcode project (PROJECT\_NAME/build/iphone/PROJECT\_NAME.xcodeproj).

3. Expand the **Frameworks** folder, right-click the module library (lib<MODULE\_ID>.a) and select **Delete.**

4. Click **Remove Reference**.

5. Right-click the project name and select **Add Files to <PROJECT\_NAME>...**

6. In the dialog:

    1. Locate your module's Xcode project and select it.

    2. Uncheck **Copy item if needed** if it is checked.

    3. Select all targets under **Add to targets**.

    4. Click **Add**.

7. In the project's **Build Phases**:

    1. Under **Target Dependencies**, click the **Add** button, then select the module and click **Add.**

    2. Under **Link Binaries with Libraries**, click the **Add** button, then select the module library (lib<MODULE\_ID>.a) and click **Add**.

8. From the menu bar, select **Product** > **Clean**.

After you are done, the module Xcode project should be under the test application Xcode project. Expand the module Xcode project. You can edit and work on your module project, then build the test application project to test the module.

If the module project appears under the test application project, but you cannot expand the module project, the module project was opened when you linked the two projects together. Exit Xcode, then reopen the test application Xcode project.

## Add a third-party framework

Since release 6.2.0, Titanium supports both static and dynamic framworks. Frameworks written in Swift are also supported if they expose an Objective-C interface header in combination with the [Swift framework hook](https://github.com/appcelerator-modules/hook-swift-frameworks). Please refer to the individual framework to see if it meets this requirement to be used with Titanium and if it requires additional configuration.

To use a third-party framework in your module, add the framework to the module's platform directory, so it can be copied over during the module's build process and linked when building the application. Add and setup the framework in Xcode then code and build your project to verify the project compiles correctly. If you are targeting Titanium 6.2.0 and above, these setup steps is all you have to complete as the frameworks will be integrated automatically. In older versions, you need to take additional steps to modify the module's module.xcconfig file to include the path to the framework when it is installed in a local project or globally in the Titanium SDK home directory, and modify the linker flags to include the framework when building the application.

1. **Copy the framework** to the module project's ios/platform directory.

2. Open the module project in **Xcode** and open ios/<PROJECT\_NAME>.xcodeproj.

3. **Add the framework** to the project: Right-click the project name and select **Add File to <PROJECT\_NAME>...**

4. Follow any additional directions to incorporate the framework, such as adding additional linker flags.

5. Verify that the framework is included in the project. In **Build Phases**, check that static frameworks are listed in the **Link Binary With Libraries** section. Dynamic frameworks need to be added to the **Embedded Binaries** section, which will also generate the entry in the **Link Binary With Libraries** section.

6. In your **header and source files**, add the framework's header files and add the third-party APIs.

7. Optional: this step is only required if your module needs to be compatible with in Titanium 6.2.0 and earlier: Open the module project's ios/module.xcconfig file and set the:

    1. FRAMEWORK\_SEARCH\_PATHS variable to the path(s) to the module's platform directory once it is installed. The example below specifies the local install location and global install locations.

    2. OTHER\_LDFLAGS variable to the \-framework <FRAMEWORK\_NAME> for each framework you are adding. Add the $(inherited) variable to the beginning to not overwrite the variable for the application build command.

        `FRAMEWORK_SEARCH_PATHS=$(SRCROOT)/../..``/modules/iphone/``<MODULE_ID>/<MODULE_VERSION>``/platform`

        `/Library/Application``\ Support``/Titanium/modules/iphone/``<MODULE_ID>/<MODULE_VERSION>``/platform`

        `~``/Library/Application``\ Support``/Titanium/modules/iphone/``<MODULE_ID>/<MODULE_VERSION>``/platform`

        `OTHER_LDFLAGS=$(inherited) -framework <FRAMEWORK_NAME>`

8. **Set any other build settings** the framework might require via the module's ios/module.xconfig to make sure they get applied when building the application.

9. **Build your project** in Xcode to verify it will compile and link correctly.

Stripping unused architectures from dynamic frameworks

For a proper app store submission, all used dynamic frameowrks in the final app need to be stripped of unused architechtures. To do so, our SDK will automatically integrate Realm's popular [strip-frameworks.sh](https://github.com/realm/realm-cocoa/blob/master/scripts/strip-frameworks.sh) script into the Xcode project. If any of the frameworks used in your module needs additional handling or scripts, you can instruct your users to create a custom script under platform/ios/strip-frameworks.sh inside the app project. If this file is present, the pre-bundled script from Realm will be ignored and the script inside the project will be used instead.

## Bundle module assets

To distribute module assets with your module distribution, you must place them in the assets directory of your project. Any assets within this folder (with the exception of JavaScript files) will be distributed and copied into the folder pattern "module/<moduleid>" in the application bundle. You can then load them using this relative path from your Objective-C code. For example, assuming you had a module image named "foo.png". You could load that using the following example:

`NSString *path = [NSString stringWithFormat:@``"modules/%@/foo.png"``,[self moduleId]];`

`NSURL *url = [TiUtils toURL:path proxy:self];`

`UIImage *image = [TiUtils image:url proxy:self];`

## Format / Lint source-code

The Titanium SDK uses clang-format to have a unified code-style in its source-code (clang-format for iOS and Android, ESLint for the CLI). You can do the same by following the following few steps:

1. Copy the .clang-format file from [here](https://github.com/appcelerator/titanium_mobile/blob/master/iphone/.clang-format) to the "ios/" directory of your module project, e.g. <module-root>/ios/.clang-format

2. Install the [clang-format CLI](https://clang.llvm.org/docs/ClangFormat.html): npm install -g clang-format

3. Optional: Ensure that you have your module project in Git to be able to restore the old files in case you do not like the predefined format

4. Format your source with: clang-format -style=file -i Classes/\*

5. Thats it! All native files have been formatted.

Now that you have a format, you can also extend your .clang-format with more formatting rules or adjust existing ones to match your own code style.

## Distribute your module through the Appcelerator Marketplace

To distribute your module through the Titanium+Plus Marketplace, you'll first need to package normally. Once you have tested your module locally and are ready to distribute it, you can then submit it to the marketplace for distribution. There are several prerequisites you'll need before you can distribute:

* You must have a valid Titanium developer account.

* You must have fully completed filling your manifest values.

* You must have a valid license text in the LICENSE file in your project.

* You must have a valid documentation file in the index.md file in your documentation directory of your project.

* You must specify some additional metadata upon upload such as the price (which can be free).

* If you are charging for your module, you must establish a payment setup with Appcelerator so we can pay you.

* You must accept the Titanium+Plus Marketplace terms of service agreement.

Once you have upload your module and completed the necessary submission steps, your module will be queued for submission and availability in the marketplace directory.
