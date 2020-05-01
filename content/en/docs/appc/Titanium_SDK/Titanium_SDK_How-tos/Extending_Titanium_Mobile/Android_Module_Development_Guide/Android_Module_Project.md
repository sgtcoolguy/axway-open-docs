{"title":"Android Module Project","weight":"30"}

* [Introduction](#introduction)

* [Prerequisites](#prerequisites)

* [Project Structure](#project-structure)

    * [Build properties file](#build-properties-file)

    * [Manifest file](#manifest-file)

* [CLI tasks](#cli-tasks)

    * [Create a new module project](#create-a-new-module-project)

    * [Build and package the module](#build-and-package-the-module)

    * [Clean the project](#clean-the-project)

* [Studio tasks](#studio-tasks)

    * [Create a new module project](#create-a-new-module-project)

    * [Build and package the module](#build-and-package-the-module)

        * [Studio Toolbar](#studio-toolbar)

* [Test the module](#test-the-module)

* [Debug the module](#debug-the-module)

* [Adding 3rd party libraries](#adding-3rd-party-libraries)

    * [Gradle Dependencies](#gradle-dependencies)

    * [Local Dependencies](#local-dependencies)

    * [Adding Android Libraries to Studio](#adding-android-libraries-to-studio)

* [Bundling files](#bundling-files)

    * [Module "assets" folder](#module-"assets"-folder)

    * [Module "platform/android/res" folder](#module-"platform/android/res"-folder)

* [Format / Lint source-code](#format-/-lint-source-code)

* [Distribute your module through the Axway Marketplace](#distribute-your-module-through-the-axway-marketplace)

* [Troubleshooting](#troubleshooting)

    * [Conflicting JAR files / Google Play Services](#conflicting-jar-files-/-google-play-services)

    * [Android NDK build fails](#android-ndk-build-fails)

## Introduction

This guide covers how to manage your module project as well as how to add third-party frameworks and bundle assets with your module. You can use Studio, Eclipse or the Appc-CLI to build Android modules.

## Prerequisites

To develop an Android-based Module, you need to install the following tools and setup a few additional environment variables:

* Titanium SDK

* Android SDK API 26+

* Studio or the Appcelerator Command-Line Interface (CLI) for creating modules, and building and running test applications

* [Android NDK](/docs/appc/Titanium_SDK/Titanium_SDK_Getting_Started/Installation_and_Configuration/Installing_Titanium_Advanced_Tools/Installing_the_Android_NDK/) and add an ANDROID\_NDK environment variable pointing to the NDK directory. See [Installing the Android NDK](/docs/appc/Titanium_SDK/Titanium_SDK_Getting_Started/Installation_and_Configuration/Installing_Titanium_Advanced_Tools/Installing_the_Android_NDK/).

* [gperf](/docs/appc/Titanium_SDK/Titanium_SDK_Getting_Started/Installation_and_Configuration/Installing_Titanium_Advanced_Tools/Installing_gperf/) must be installed and in your system PATH. See [Installing gperf](/docs/appc/Titanium_SDK/Titanium_SDK_Getting_Started/Installation_and_Configuration/Installing_Titanium_Advanced_Tools/Installing_gperf/).

* Python, Python setuptools and the markdown module, and Python in your system PATH. See [Installing Python](/docs/appc/Titanium_SDK/Titanium_SDK_Getting_Started/Installation_and_Configuration/Installing_Titanium_Advanced_Tools/Installing_Python/) and [Installing Required Python Packages](/docs/appc/Titanium_SDK/Titanium_SDK_Getting_Started/Installation_and_Configuration/Installing_Titanium_Advanced_Tools/Installing_Required_Python_Packages/).

If you want to use Studio, install:

* [Eclipse Java Development Tools plugin](https://eclipse.org/jdt/). See [Installing the Java Development Tools](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Getting_Started/Installing_the_Java_Development_Tools/).

* [Android Development Tools plugin](http://developer.android.com/tools/sdk/eclipse-adt.html). See [Installing the Android Development Tools](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Getting_Started/Installing_the_Android_Development_Tools/).

## Project Structure

A number of files and directories work together to define our module and what it does. Let's take a quick look at each of them:

<table class="confluenceTable"><thead class=" "></thead><tfoot class=" "></tfoot><tbody class=" "><tr><td class="highlight-grey confluenceTd" rowspan="1" colspan="1"><p>File/Directory</p></td><td class="highlight-grey confluenceTd" rowspan="1" colspan="1"><p>Description</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p>LICENSE</p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>The module's full license text; this will be distributed with the module to let other developers know how they can use and redistribute it.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">assets/</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>The directory where you can place module assets such as images. The files in this directory are added as JAR resources which you can be fetch in Java via the <a class="external-link external-link" href="https://developer.android.com/reference/java/lang/ClassLoader#getResourceAsStream(java.lang.String)" target="_blank">ClassLoader.getResourceAsStream()</a> method. They're also copied to the APK's "assets" folder.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">documentation/</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>The directory where you should place your module documentation for end-users. The file <tt class=" ">index.md</tt> is a Markdown-formatted template file that you should use when writing your module documentation. You may also write your documentation using the <a class="document-link " href="#!/guide/TDoc_Specification">TDoc Specification</a>. This is only required for module distributed in the Appcelerator Marketplace. You can safely ignore this directory if you do not intend to distribute your module.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">example/</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>The directory where your module example(s) should go. The file app.js will be generated to include a sample loading of your module in a test window. This file can be used for quickly testing your module as well as give an example to end-users on how to use your module. This directory is distributed with your module.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">Resources/</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Supported as of Titanium 9.0.0. Files placed in this directory will be copied to the Android app's root "Resources" directory when built, making them accessible to the Titanium app's JavaScript files. These files are also accessible in Java via the <tt class=" ">AssetManager</tt> class.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">android/build.gradle</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>As of Titanium 9.0.0, this optional gradle file allows a module to define its dependencies.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">android/lib/</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Place any third-party JAR dependencies here and they will be bundled up as a part of your module automatically.</p><p>As of Titanium 9.0.0, it is highly recommended to reference dependencies via "build.gradle" instead to avoid dependency collision with other modules.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">android/manifest</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>A special file that describes metadata about your module and used by the Titanium compiler. This file is required and is distributed with your module.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">android/platform/android/AndroidManifest.xml</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>As of Titanium 9.0.0, you can optionally specify the module's custom <tt class=" ">AndroidManfiest.xml</tt> here. Alternatively, you can do the same within the <tt class=" ">timodule.xml</tt> as documented below.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">android/platform/android/aidl/</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>As of Titanium 9.0.0, you can add Java code generation templates here, as defined by the <a class="external-link external-link" href="https://developer.android.com/guide/components/aidl" target="_blank">Android Developer: AIDL</a> guide.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">android/platform/android/assets/</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>As of Titanium 9.0.0, you can optionally provide files that will be copied to the APK's root "assets" folder here.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">android/platform/android/jniLibs/</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>As of Titanium 9.0.0, you can add C/C++ <tt class=" ">*.so</tt> libraries to be bundled with the module. These libraries must placed under subdirectories named after their respective architecture such as <tt class=" ">armeabi-v7a</tt>, <tt class=" ">arm64-v8a</tt>, <tt class=" ">x86</tt>, and <tt class=" ">x86_64</tt>.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">android/platform/android/rs/</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>As of Titanium 9.0.0, you can add RenderScript files here as defined by the <a class="external-link external-link" href="https://developer.android.com/guide/topics/renderscript/compute" target="_blank">Android Developer: RenderScript</a> guide.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">android/platform/android/res/</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Optional folder where you can add Android resource files such as drawables, layouts, mipmaps, values, etc. as defined in the <a class="external-link external-link" href="http://developer.android.com/guide/topics/resources/providing-resources.html" target="_blank">Android Developer: Providing Resources</a> guide.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">android/src/</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Folder containing your Java source files for the module. Can contain Kotlin source files as of Titanium 9.0.0. This directory is not distributed with your module.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">android/timodule.xml</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>A place to put custom activities and general XML that will end up in the AndroidManifest.xml of apps. Read more about this file in the <a class="document-link " href="#!/guide/tiapp.xml_and_timodule.xml_Reference">tiapp.xml and timodule.xml reference</a>.</p></td></tr></tbody></table>

The CLI creates a module project that contains multiple platforms. Each platform contains its own folder with platform-specific resources and common folders for assets, documentation, example, and Resources.

### Build properties file

This was deprecated since 5.0.0.

The build.properties file contains build variables used by the Ant CLI. Using the build.properties is deprecated in favor of the unified build-command appc ti build -p android --build-only.

| Variable | Description | Example |
| --- | --- | --- |
| titanium.platform | Path to the Titanium SDK android folder | /Users/<USERNAME>/Library/Application Support/Titanium/mobilesdk/osx/<VERSION>/android |
| android.platform | Path to the Android SDK platforms folder | /Users/<USERNAME>/ opts /android- sdk /platforms/android-25 |
| google.apis | Path to the Google APIs add-ons folder | /Users/<USERNAME>/ opts /android- sdk /add-ons/addon-google\_apis-google-25 |
| android.ndk | Path to the Android NDK (if needed) | /Users/<USERNAME>/ opts /android-ndk |

### Manifest file

Titanium module metadata is described in a special text file named manifest. This file is a simple key/value property format.

Before you distribute your module, you must edit this manifest and change a few values. Some of the values are pre-generated and should not be edited. These are noted with the comment before them. In the manifest file, any line starting with a hash character (#) is ignored. The following are the descriptions of each entry in the manifest:

<table class="confluenceTable"><thead class=" "></thead><tfoot class=" "></tfoot><tbody class=" "><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><strong class=" ">Key</strong></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p><strong class=" ">Description/Purpose</strong></p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p>version</p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>This is the version of your module. You should change this value each time you make major changes and distribute them. Version should be in the dotted notation (X.Y.Z) and must not con-tain any spaces or non-number characters.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p>architectures</p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>The binary architectures the module supports as a delimited list. Example: x86 arm64-v8a</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p>description</p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>This is a human-readable description of your module. It should be short and suitable for display next to your module name.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p>author</p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>This is a human-readable author name you want to display next to your module. It can simply be your personal name, such as "Jon Doe" or an organizational name such as "Axway Appcelerator".</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p>license</p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>This is a human-readable name of your license. You should use a short description such as "Apache Public License", "MIT" or "Commercial".</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p>copyright</p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>This is a human-readable copyright string for your module. For example, "Copyright (c) 2020 by Axway Appcelerator, Inc."</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p>name</p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>This is a read-only name of your module that is generated when you created your project. You must not edit this value.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p>moduleid</p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>This is a read-only module id of your module that is generated when you created your project. You should not edit this value. NOTE: you must generate a unique id. We recommend using your reverse-DNS company name + module_name as a pattern to guarantee uniqueness. The Titanium Marketplace will only allow unique module ids when distributing modules. If you must edit this value, you must also edit the value in your module implementation file.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p>guid</p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>This is a read-only unique module id for your module that is generated when you created your project. You must not edit this value.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p>platform</p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>This is a read-only platform target of your module that is generated when you created your project. You must not edit this value.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p>minsdk</p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>The is a generated value for the minimum Titanium SDK version that was used when creating your module. The current minimum version for new Android modules is 7.0.0.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p>respackage</p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>This setting only applies to Titanium versions older than 9.0.0.</p><p>This is specific package name to generate a R.java. If you got exception like <i class=" "><tt class=" ">java.lang.NoClassDefFoundError: com.example.mypackage.R$layout</tt> </i>then add the following entry to the your module manifest file: <i class=" ">respackage: <tt class=" ">com.example.mypackage</tt> </i>. This will generate a corresponding java R file <tt class=" ">com.example.mypackage.R.java</tt></p></td></tr></tbody></table>

## CLI tasks

### Create a new module project

To create a new module project, run the following Appcelerator CLI command:

```bash
appc new -d /PATH/TO/WORKSPACE -n <MODULE NAME> --id <MODULE ID>

$ appc new -n <MODULE NAME> --id <MODULE ID>
Appcelerator Command-Line Interface, version 7.1.2
Copyright (c) 2014-2018, Appcelerator, Inc.  All Rights Reserved.
? What type of project are you creating?
  Native App
  Arrow App
❯ Titanium Module (timodule)
  Apple Watch App
```

If you omit any of the options, the CLI will prompt you to enter them.

### Build and package the module

To build and package a module, run ti build in the android directory.

```bash
cd /<PATH_TO_MODULE_PROJECT>/<MODULE_NAME>/android
appc run -p android --build-only
```

After the build completes, you should have a ZIP file in the android/dist directory and see the following message in the console:

```
** BUILD SUCCEEDED **
```

With the ZIP file, you can either:

* Uncompress it in the Titanium SDK home path to install the module globally for all your Titanium applications

* Uncompress it in a Titanium project's parent directory to install the module locally for that one Titanium application

* Distribute the ZIP file

### Clean the project

Earlier, you could clean your module with ant clean. These days, using the Appc-CLI, the build will be cleaned automatically before a new build is made.

## Studio tasks

### Create a new module project

1. From the menu, select **File** > **New** > **Mobile Module Project** to open the **New Mobile Module Project** dialog.

2. In the **Project name** field, enter a name for the module.

3. In the **Module ID** field, enter a module ID for the module.

4. In **Deployment Targets**, select **Android**.

5. Click **Next.**

6. In the **Module Manifest File** page, enter information about your module, such as the license information, version number, etc. You can also edit this information in the manifest file later.

7. Click **Finish**.

### Build and package the module

You can either use Studio's launch toolbar or use Ant from the right-click context menu.

#### Studio Toolbar

1. Select your module folder in the **Project Explorer** view.

2. Verify **Package** and **Android Module** are displayed in **Launch Mode** and **Launch Target**, respectively.

3. Click the Package icon to open the **Package Android Module** dialog.

4. In **Output Location**, select either

    1. **Titanium SDK** to install the module in the Titanium SDK home path to be accessed by any Titanium application

    2. **Mobile App Project** and choose an application to install the module locally that can be accessed by one that Titanium application

    3. **Location** and enter a path to copy the ZIP file to for distribution

5. Click **Finish**.

In the **Console** view, you will see the build log output. After the build completes, the package (ZIP file) will be in the module's android/dist folder.

## Test the module

To test a module:

1. Create a new Titanium Classic or Alloy project.

2. Install the module to either the Titanium SDK home directory or in the project.

3. Add the module as a dependency to the project.

4. Load the module and make module API calls.

## Debug the module

The best way to debug your Android modules right now is a bit old fashioned. When there is a problem or unexpected behavior in your module, use log statements to trace through your code's execution. The Java [Log](http://builds.appcelerator.com.s3.amazonaws.com/module-apidoc/2.0.0/android/org/appcelerator/kroll/common/Log.html) class offers several static methods for writing to the log. It is considered a best practice to define a LCAT or TAG variable at the top of your class, and to use that as the first parameter to all calls to Log.

```
private static final String TAG = "FooProxy";

@Kroll.method
public void fooFunction(String arg)
{
    Log.i(TAG, "fooFunction received: " + arg);
}
```

## Adding 3rd party libraries

As of Titanium 9.0.0, you can no longer use Google's deprecated Support libraries. You must use the AndroidX libraries instead.

### Gradle Dependencies

As of Titanium 9.0.0, you can reference libraries via gradle by adding a build.gradle file to the module's root android directory. This is the preferred way of adding libraries because the gradle build system will automatically include a dependency's dependencies and resolve version conflicts.

An example can be found here: [ti.map/android/build.gradle](https://github.com/appcelerator-modules/ti.map/blob/master/android/build.gradle)

The below is an example build.gradle file which provides access to the Google "Material Components" library.

```
dependencies {
    implementation 'com.google.android.material:material:1.1.0'
}
```

### Local Dependencies

To use a third-party JAR in your module, add the JAR file to the module's lib directory (not the libs directory), so it can be copied over during the module's build process and linked when building the application. If you are using Studio, you need to add the JAR as a dependency to the module project before importing the package and making API calls.

To add a JAR as a dependency in Studio:

1. Right-click the module project (root folder) and select **Properties** to open the project's properties dialog.

2. In the left pane, select **Java Build Path**.

3. In the right pane, click the **Libraries** tab.

4. Click the **Add External JARs...** button to open the **JAR Selection** dialog.

5. Navigate to the module's android/lib folder and select the JAR to add.

6. Click **Open**. The JAR should be added to the JARs list.

7. Click **OK** to dismiss the dialog.

With Titanium 6.1.1 - 8.3.1, you can also copy AAR (Android Archive) library files to the module's lib directory. However, this is not supported as of Titanium 9.0.0, which requires you to reference these AAR libraries via a build.gradle file instead.

*Where do i get .aar files?*

Most third-party libraries can be downloaded from either GitHub or from one of the popular repositories like [jCenter](https://bintray.com/bintray/jcenter) or [Maven Central](http://maven central/). Copies of the Android Support Libraries can be found inside your Android SDK directory under <andriod-sdk>/extras/android/m2repository/com/android

### Adding Android Libraries to Studio

To properly resolve any imports of your used Android Libraries in Studio, you need to add the JARs they are contained in to Studio's Java build path. Before you add any import statements to your code, build the project at least once. This is required to process the AAR files and extract the JAR files they contain. After that, add the required JARs to Studio just as described in the [Add a Third-Party JAR](#AddaThird-PartyJAR) section of this guide. The extracted JAR files can be found under build/android/intermediates/exploded-aar. There you'll find a directory for each AAR file. Inside each of those directories, add the classes.jar and any additional JAR files under the lib directory.

## Bundling files

For Android modules, you can either add assets in the module's assets folder or android/platform folder.

### Module "assets" folder

Files in the module's assets folder are added as JAR resources. To access these files, use the Android Class's getResource()method to retrieve a URL object or [getResourceAsStream()](http://developer.android.com/reference/java/lang/Class.html#getResourceAsStream(java.lang.String)) method to retrieve an InputStream object.

```
// original file was in assets/image.png
URL url = getClass().getClassLoader().getResource('assets/image.png');
Log.i('GETFILE', url.toString());
```

The README file and JavaScript files (any file with a .js extension) in the assets folder are not added to the JAR library.

### Module "platform/android/res" folder

Add any of the resource directories defined in [Android Developer: Providing Resources](http://developer.android.com/guide/topics/resources/providing-resources.html) to add drawables, layouts, values, etc. to the built app. To access these files, you can use the Titanium SDK TiRHelperhelper class.

```
// original file was in android/platform/android/res/drawable/image.png
int result = 0;
try {
    result = TiRHelper.getApplicationResource('drawable.image');
    Log.i("GOODSTUFF", new Integer(result).toString());
} catch (ResourceNotFoundException e) {
    Log.e('BADSTUFF', '[ERROR] EXCEPTION -- RESOURCE NOT FOUND');
}
```

## Format / Lint source-code

The Titanium SDK uses clang-format to have a unified code-style in its source-code (clang-format for iOS and Android, ESLint for the CLI). You can do the same by following the following few steps:

1. Copy the .clang-format file from [here](https://github.com/appcelerator/titanium_mobile/blob/master/android/.clang-format) to the "android/" directory of your module project, e.g. <module-root>/ios/.clang-format

2. Install the [clang-format CLI](https://clang.llvm.org/docs/ClangFormat.html): npm install -g clang-format

3. Optional: Ensure that you have your module project in Git to be able to restore the old files in case you do not like the predefined format

4. Format your source with: clang-format -style=file -i src/<yourmodule>/\*.java

5. Thats it! All \*.java files have been formatted.

Now that you have a format, you can also extend your .clang-format with more formatting rules or adjust existing ones to match your own code style.

## Distribute your module through the Axway Marketplace

To distribute your module through the [Axway Marketplace](https://marketplace.axway.com/home), you'll first need to package normally. Once you have tested your module locally and are ready to distribute it, you can then submit it to the marketplace for distribution. There are several prerequisites you'll need before you can distribute:

* You must have a valid Titanium developer account.

* You must have fully completed filling our your manifest values.

* You must have a valid license text in the LICENSE file in your project.

* You must have a valid documentation file in the index.md [file in your documentation directory of your project.](http://index.md/)

* You must specify some additional metadata upon upload such as the price (which can be free).

* If you are charging for your module, you must establish a payment setup with Axway so we can pay you.

* You must accept the Axway Marketplace terms of service agreement.

Once you have upload your module and completed the necessary submission steps, your module will be queued for submission and availability in the marketplace directory.

## Troubleshooting

### Conflicting JAR files / Google Play Services

When building an application that includes two or more modules that contains the same library, in particular, the google-play-services.jar, the JAR files may conflict indicating that each module is using a different version of the library.

*Error Log*

```
[ERROR] Application Installer abnormal process termination. Process exit value was 1
[ERROR] :  Conflicting jar files detected:
[ERROR] :
[ERROR] :  The following modules have different "google-play-services.jar" files
[ERROR] :     mymodule   (version 3.0.3) (hash=8b95ece0c3ae132fb898ec8beef1cb2d)
[ERROR] :     ti.map     (version 2.2.3) (hash=a9b753b4c63719e24d0022e341c57b2e)
[ERROR] :
[ERROR] :  You can either select a version of these modules where the conflicting jar file is the same or you
[ERROR] :  can try copying the jar file from one module's "lib" folder to the other module's "lib" folder.
```

Prior to Titanium SDK 7.0.0, to resolve this issue, you can either delete one of the JAR files from one of the modules or copy the JAR file from one module's lib folder to the other's to make both versions the same. This solution only works on a per-application basis and is not a global solution. In Titanium 7.0.0 and later, use the t[i.playservices](https://github.com/appcelerator-modules/ti.playservices) module to handle play services dependencies centralized. Simply add it to your timodule.xml and users will be notified if they do not include the module in their project.

### Android NDK build fails

If the Android NDK build fails, it can be because of various reasons:

* Your module has compile errors. Usually the build on the "javac" compile step already, but in case it does not, scroll up in the logs to see the actual error)

* Your NDK version is outdated (Check for the latest version [here](https://developer.android.com/ndk/index.html))

* Your project path contains spaces, which is not recommended for projects in general but especially causes build failures like /android-ndk/build/core/build-local.mk:158: \*\*\* Android NDK: Aborting, which is an Android NDK error for spaces in projects OR invalid directories for the Android NDK. Please note that spaces in a sub-directory can also cause this.

In any case, ensure to run your Titanium module build with log-level "trace" (e.g. appc run -p android -build-only -l trace) to see the whole build command. If you find issues that are not listed here, feel free to let us know via [JIRA](http://jira.appcelerator.org) or [TiSlack](http://tislack.org).
