{"title":"Alloy Concepts","weight":"10"} 

# Alloy Concepts

*   [Overview](#Overview)
    
*   [Model-View-Controller](#Model-View-Controller)
    
    *   [Alloy: MVC with Backbone](#Alloy:MVCwithBackbone)
        
*   [Alloy and the Titanium SDK](#AlloyandtheTitaniumSDK)
    
*   [Convention over configuration](#Conventionoverconfiguration)
    
    *   [Platform-specific resources](#Platform-specificresources)
        
*   [Widgets](#Widgets)
    
*   [Builtins](#Builtins)
    
*   [Compilation process](#Compilationprocess)
    
    *   [Cleanup](#Cleanup)
        
    *   [Build configuration](#Buildconfiguration)
        
    *   [Alloy Framework, assets, and lib](#AlloyFramework,assets,andlib)
        
    *   [Model-View-Controller and widget generation](#Model-View-Controllerandwidgetgeneration)
        
    *   [Main application](#Mainapplication)
        
    *   [Code optimization](#Codeoptimization)
        

## Overview

This guide covers the important concepts related to the Alloy framework, including the model-view-controller framework, convention-over-configuration design, widgets, and built-in support from Backbone.js and Underscore.js.

## Model-View-Controller

Alloy utilizes the model-view-controller (MVC) pattern, which separates the application into three different components:

*   **Models** provide the business logic, containing the rules, data and state of the application
    
*   **Views** provide the GUI components to the user, either presenting data or allowing the user to interact with the model data
    
*   **Controllers** provide the glue between the model and view components in the form of application logic
    

For example, in a calendar application, the models include events, reminders, invitations, and contacts. The views present the calendar data and reminders to the user or allow the user to add events. For reminders, the controller checks the model data and launches a 'reminder' view to the user. For adding events, the controller opens an 'add event' view, then adds the event into the model data once the user entered the data.

An advantage of MVC is the ability to reuse code by separating the functionality. For example, you can have specific views for different devices, while keeping the controller code relatively the same and the model data unchanged.

### Alloy: MVC with Backbone

Backbone.js is a lightweight MVC framework, originally designed for web applications. Alloy models are built on top of Backbone.js, taking advantage of Backbone's rich Model and Collection APIs. You define models using a Javascript file that exports a special JSON object, which uses Backbone's extend functionality to customize models and collections. See [Alloy Models](/docs/appc/Alloy_Framework/Alloy_Guide/Alloy_Models/) for more information on creating model objects and [http://backbonejs.org/](http://backbonejs.org/) for more information on Backbone.js.

Alloy views are built from Titanium UI components. You define views using XML markup and style them using Alloy _Titanium Style Sheets (.tss)_, which abstracts the creation of these components without using Titanium API calls. Alloy generates the code to create your views. See [Alloy Views](/docs/appc/Alloy_Framework/Alloy_Guide/Alloy_Views/) for more information on creating views.

Alloy controllers generally have a one-to-one relationship with Alloy views. Controllers directly use the Titanium SDK API without an abstraction layer. The controller has access to all of the view components. See [Alloy Controllers](/docs/appc/Alloy_Framework/Alloy_Guide/Alloy_Controllers/) for more information on creating controllers.

Additionally, Alloy provides built-in support for Underscore.js, which provides a set of utility functions, such as array and iterative helpers. Refer to [http://underscorejs.org/](http://underscorejs.org/) for more information.

## Alloy and the Titanium SDK

Alloy uses Titanium SDK to abstracts the creation of UI components through the use of XML markup and style sheets. If Alloy has not implemented a feature of the Titanium SDK or if the feature is not UI related, you can always use the Titanium SDK API in the Alloy controller code or create a CommonJS module to implement a feature. The table below lists what Alloy directly abstracts from the Titanium SDK.

For assets, such as images, any references to the Resources folder in the Titanium SDK documentation should be replaced with the app/assets folder to use it for Alloy. For example, the [Icons and Splash Screens](/docs/appc/Titanium_SDK/Titanium_SDK_How-tos/User_Interface_Fundamentals/Icons_and_Splash_Screens/) guide tells you to place files in either the Resources/android or Resources/iphone folder. For Alloy, the files should be placed in either the app/assets/android or app/assets/iphone folder.

Titanium SDK Component

Alloy Component

Titanium.UI.\* Objects  
Titanium.Android.Menu  
Titanium.Facebook.LoginButton  
Titanium.Map  
Titanium.Media.VideoPlayer

`Titanium.UI.createButton();`

*   XML element. Remove the namespace. For some elements, you may need to assign the ns attribute. For more information, refer to [Alloy XML Markup: Namespace](/docs/appc/Alloy_Framework/Alloy_Guide/Alloy_Views/Alloy_XML_Markup/#Namespace).
    
    `<!-- Creates a button -->`
    
    `<Button />`
    
*   TSS element. Remove the namespace. If the object belongs to another namespace besides Titanium.UI and is not implicitly assigned a namespace by Alloy, you cannot create a style based on the element name. Instead, create a style based on a selector (XML class attribute) or id (XML id attribute). For a list of objects that Alloy implicitly assigns a namespace, refer to [Alloy XML Markup: Namespace](/docs/appc/Alloy_Framework/Alloy_Guide/Alloy_Views/Alloy_XML_Markup/#Namespace).
    
    `// Does not create a button. Used to style all Button objects in the associated view.`
    
    `"Button"``:{`
    
    `// Button attributes`
    
    `}`
    

Titanium Object properties

`Titanium.UI.createButton({`

`text:` `"Foobar"``,`

`top:` `0``,`

`width: Ti.UI.SIZE`

`});`

*   XML attribute if the property can be expressed as a string, number or Titanium SDK constant. Some properties that take Titanium objects can be expressed inline using XML tags. For more information, refer to [Alloy XML Markup: Property Mapping](/docs/appc/Alloy_Framework/Alloy_Guide/Alloy_Views/Alloy_XML_Markup/#Propertymapping).
    
    `<Button title=``"Foobar"` `top=``"0"` `width=``"Ti.UI.SIZE"``/>`
    
*   TSS attribute if the property can be directly expressed as a string, number, Titanium SDK constant, dictionary or array. Indirectly, you can assign a method or value to the Alloy Globals or CFG namespace and reference it in the TSS file. For more information, refer to [Alloy Styles and Themes](/docs/appc/Alloy_Framework/Alloy_Guide/Alloy_Views/Alloy_Styles_and_Themes/).
    
    `"Button"``:{`
    
    `title:` `"Foobar"``,`
    
    `top:` `0``,`
    
    `width: Ti.UI.SIZE`
    
    `}`
    

Titanium Object methods

`var button = Titanium.UI.createButton();`

`button.setTitle(``'Push Me!'``);`

Use in the controller code. You need to define the id attribute of the object in the XML markup, so the object can be referenced in the controller.

`// Need to give the object an ID, for example, <Button id="button" />`

`$.button.setTitle(``'Push Me!'``);`

Titanium Object events

`var button = Titanium.UI.createButton();`

`button.addEventListener(``'click'``, doClick);`

XML attribute to bind a callback in the associated controller. Capitalize the first character of the event name and append 'on' to the beginning of the name.

`<!-- doClick needs to be declared in the associated controller -->`

`<Button onClick=``"doClick"``/>`

## Convention over configuration

To simplify development, Alloy uses a directory structure and naming conventions to organize the application rather than configuration files. Alloy expects to find files in specific locations. Any folder or file not adhering to the below naming conventions is ignored by Alloy. For example, at generation time, Alloy will look for the mandatory files app/views/index.xml and app/controllers/index.js, then the optional corresponding file app/styles/index.tss. Alloy requires these files to create the initial view-controller Resources/<platform>/alloy/controllers/index.js.

The following is a list of directories and files that can be found in an Alloy project:

app

Contains the models, views, controllers and assets of the application. All work should be done here. See folder descriptions below.

app/alloy.jmk

Build configuration file.  
See [Build Configuration File (alloy.jmk)](/docs/appc/Alloy_Framework/Alloy_How-tos/Alloy_Reference_Guides/Build_Configuration_File_(alloy.jmk)/).

app/alloy.js

Initializer file used to preconfigure components or override Alloy methods before the main controller is executed.  
See [Initializer File (alloy.js)](/docs/appc/Alloy_Framework/Alloy_Guide/Alloy_Controllers/#Initializerfile(alloy.js)) for more information.

app/config.json

Project configuration file.  
See [Project Configuration File (config.json)](/docs/appc/Alloy_Framework/Alloy_How-tos/Alloy_Reference_Guides/Project_Configuration_File_(config.json)/).

app/assets

Contains image assets and other files that need to be copied into the Resources directory.  
Reference these files in the code without the 'app/assets' path and without the platform-specific folder if it is inside one.

app/controllers

Contains controllers in the format filename.js to a corresponding view file app/views/filename.xml.  
See [Alloy Controllers](/docs/appc/Alloy_Framework/Alloy_Guide/Alloy_Controllers/) for more information.

app/i18n

Since Alloy 1.8.0 and Titanium 5.2.0 [Language Strings](/docs/appc/Titanium_SDK/Titanium_SDK_How-tos/Cross-Platform_Mobile_Development_In_Titanium/Internationalization/#Languagestrings) are sourced from app/i18n and Alloy will generate the i18n folder in the project root.

app/lib

Contains application-specific library code, typically in the CommonJS format.  
See [Library code and CommonJS modules](/docs/appc/Alloy_Framework/Alloy_Guide/Alloy_Controllers/#LibrarycodeandCommonJSmodules) for more information.

app/migrations

Contains database migration files in the format <DATETIME>\_filename.js.  
See [Migrations](/docs/appc/Alloy_Framework/Alloy_Guide/Alloy_Models/Alloy_Sync_Adapters_and_Migrations/#Migrations) for more information.

[Alloy Sync Adapters and Migrations:Migrations](/docs/appc/Alloy_Framework/Alloy_Guide/Alloy_Models/Alloy_Sync_Adapters_and_Migrations/#Migrations)

app/models

Contains model files in the format filename.js.  
See [Alloy Models](/docs/appc/Alloy_Framework/Alloy_Guide/Alloy_Models/) for more information.

app/platform

Since Alloy 1.8.0 platform resources are sourced from app/platform and Alloy will generate the platform folder in the project root.

app/specs

Like the app/lib folder except it is only used if the deploy type is **not** production (since **Alloy 1.2.0**).  
See [Library Code](/docs/appc/Alloy_Framework/Alloy_Guide/Alloy_Controllers/#LibrarycodeandCommonJSModules) for more information.

app/styles

Contains view styling in the format filename.tss, which is applied to a corresponding view file app/views/filename.xml.  
See [Titanium Style Sheets](/docs/appc/Alloy_Framework/Alloy_Guide/Alloy_Views/Alloy_Styles_and_Themes/#TitaniumStyleSheets) for more information.

app/themes

Contains themes to customize the assets and styles of the entire GUI.  
See [Themes](/docs/appc/Alloy_Framework/Alloy_Guide/Alloy_Views/Alloy_Styles_and_Themes/#Themes) for more information.

app/views

Contains views in the format filename.xml with the optional corresponding files app/controllers/filename.js and app/styles/filename.tss.  
See [Alloy XML Markup](/docs/appc/Alloy_Framework/Alloy_Guide/Alloy_Views/Alloy_XML_Markup/) for more information.

app/widgets

Contains widget files. Each widget will have its own app\-like directory structure.  
See [Widgets](#Widgets) for more information.

i18n

Since Alloy 1.8.0 and Titanium 5.2.0 [Language Strings](/docs/appc/Titanium_SDK/Titanium_SDK_How-tos/Cross-Platform_Mobile_Development_In_Titanium/Internationalization/#Languagestrings) are sourced from app/i18n and Alloy will generate the i18n folder in the project root. Before Alloy 1.8.0 and Titanium 5.2.0 you were expected to manage the i18n folder in the project root, just like you do without Alloy.

Resources

Contains the Titanium files generated by the Alloy interface from the app directory. All files will be overwritten each time the application is built.  
Since Alloy 1.3.0, Alloy creates a separate Titanium project for each platform you build for in the Resources/<platform> folder.  
See [Compilation process](#Compilationprocess) for more information.

**Notes:** the lib, migrations, themes and widgets folders are not automatically generated when creating a new project. The migrations and widgets folder will be generated by the Alloy command-line interface if any of those components are generated. The lib and themes folders will need to be manually created.

The alloy.jmk file is not automatically generated when creating a new project. Use the command-line interface to generate this file.

### Platform-specific resources

Controllers, views and styles can have platform-specific resources. Just add a folder named android, ios, mobileweb or windows under the component folder and add your platform-specific files for Android, iOS, Mobile Web or Windows Phone into the folder, respectively. Note: Support for Windows 8.1 and Windows Phone SDKs has been deprecated as of SDK 6.3.0.GA and has be removed in SDK 7.0.0.GA.

For example, an iOS-specific view and an Android-specific controller would be look like this:

*   app
    
    *   controllers
        
        *   android
            
            *   index.js
                
        *   index.js
            
    *   views
        
        *   ios
            
            *   index.xml
                
        *   index.xml
            

Alternatively, you can use special conditional code and attributes inside the controllers, views and styles to apply platform-specific code and components. Refer to [Controller Conditional Code](/docs/appc/Alloy_Framework/Alloy_Guide/Alloy_Controllers/#Conditionalcode) and [Conditional Code](/docs/appc/Alloy_Framework/Alloy_Guide/Alloy_Views/Alloy_XML_Markup/#Conditionalcode) for more details.

Additionally, the assets folder is laid out the same way as the Resources folder in a Titanium project for platform-specific files and density-specific images. Refer to [Platform-Specific Resources](/docs/appc/Titanium_SDK/Titanium_SDK_How-tos/Cross-Platform_Mobile_Development_In_Titanium/Supporting_Multiple_Platforms_in_a_Single_Codebase/#Platform-specificresources) for more information.

## Widgets

Widgets are self-contained components that can be easily dropped into Alloy-powered Titanium projects. They were conceived as a way to reuse code in multiple applications or to be used multiple times in the same application. Widgets have their own models, views, controllers, styles and assets and are laid out the same as the app directory in the Alloy project.

*   For information on using widgets in a project, see [Importing Widgets](/docs/appc/Alloy_Framework/Alloy_Guide/Alloy_Views/Alloy_XML_Markup/#Importingwidgets).
    
*   For information on creating widgets, see [Creating Widgets](/docs/appc/Alloy_Framework/Alloy_Guide/Alloy_Widgets/#Creatingwidgets).
    
*   To search publicly available widgets, visit [gitTio](http://gitt.io/) .
    

## Builtins

Alloy comes with additional utilities used to simplify certain functions, such as animations, string manipulation, and display unit conversion. These utilities are referred to as 'builtins.' To use these utilities, the controller needs to call require with 'alloy' as the root directory. For example, to use an animation function to shake the current view by pressing the 'shake' button, add this code to a controller:

`var animation = require(``'alloy/animation'``);`

`$.shake.addEventListener(``'click'``, function(e) {`

`animation.shake($.view);`

`});`

See [Alloy builtins API documentation](#!/api/Alloy.builtins) for the functionality and usage of builtins.

## Compilation process

This section provides a brief overview of how the Alloy command-line interface converts the files in the app folder to a Titanium project in the Resources/<platform> folder for each platform you build your project for. Before Alloy 1.3.0, Alloy creates only one Titanium project in the Resources folder.

### Cleanup

The Resources folder is cleaned of any previous built files.

### Build configuration

If the build configuration file, alloy.jmk, exists, it is loaded. The 'pre:load' task executes at this point if it is defined.

### Alloy Framework, assets, and lib

Alloy framework files, which include the Backbone.js and Underscore.js libraries, sync adapters and base controller class, are copied to the Resources/<platform>/alloy folder. The Alloy base library, alloy.js, is copied to the Resources folder. These files are necessary to run any Alloy project.

The project configuration file, config.json, is processed and copied to Resources/<platform>/alloy/CFG.js.

The files in the assets and lib folders, as well as the files in the theme's assets folder, are copied to the Resources folder.

The 'pre:compile' task executes at this point if it is defined.

### Model-View-Controller and widget generation

The model files are processed. The compiler creates a JavaScript file per model and copies them to the Resources/<platform>/alloy/models folder.

The widget files are processed. The compiler creates a folder per widget that contains JavaScript files per view-controller and copies them to the Resources/<platform>/alloy/widgets folder.

The style, view, and controller files, as well as the files in the theme's style folder and the app.tss global style file, are processed. The compiler creates a JavaScript file per view-controller and copies them to the Resources/<platform>/alloy/controllers folder.

### Main application

Alloy creates a skeleton app.js file from a template. The contents of this file require some Alloy modules and calls the main view-controller index.js. If an initializer file, alloy.js, exists, the entire contents of the file are copied into the app.js file right before the call to initiate the main view-controller.

Before the file is written to the Resources directory, the 'compile:app.js' task executes if one is defined in the build configuration file.

### Code optimization

The generated code is processed through UglifyJS to optimize the code for speed and compactness. The code is optionally beautified.

If the code is compiled for a specific platform, all conditional code that should not be executed for that platform is removed. For example, if the application contains code sections specifically for iOS but the application is compiled for an Android platform, all of the iOS conditional code is removed.

Required Alloy builtin libraries are copied to the Resources/<platform>/alloy folder and optimized in the same process as described before.

Then, the 'post:compile' task executes if one is defined in the build configuration file.