{"title":"Titanium SDK 5.3.0.Beta - 21 April 2016","weight":"120"} 

## Contents

*   [About This Release](#AboutThisRelease)
    
    *   [Windows 8.1 and Windows 10](#Windows8.1andWindows10)
        
*   [New Features](#NewFeatures)
    
    *   [Windows Platform](#WindowsPlatform)
        
*   [Community Credits](#CommunityCredits)
    
*   [Fixed Issues](#FixedIssues)
    
*   [Improvements](#Improvements)
    
*   [API Changes](#APIChanges)
    

## About This Release

Titanium SDK 5.3.0.Beta is a minor release of the SDK, addressing high-priority issues from previous releases.

As of this release, Titanium SDK 5.2.x will not be supported six months from 5.3.0.GA's release date. See [Axway Appcelerator Deprecation Policy](/docs/appc/AMPLIFY_Appcelerator_Services_Overview/Axway_Appcelerator_Deprecation_Policy/) and [Nominal Lifetimes](/docs/appc/AMPLIFY_Appcelerator_Services_Overview/Axway_Appcelerator_Product_Lifecycle/#NominalLifetimes) documents for details.

### Windows 8.1 and Windows 10

With the release of SDK 5.3.0, we put some focus on supporting Windows 10 and Windows 10 mobile features ([TIMOB-19816](https://jira.appcelerator.org/browse/TIMOB-19816)).

We updated the way you can specify capabilities of your app in the tiapp.xml to account for namespace and naming differences between Windows 8.1 and 10 apps ( [TIMOB-20231](https://jira.appcelerator.org/browse/TIMOB-20231)). Previously, you would have to include capabilities in the xml namespace on the tag. You had to know what namespace prefix to use based on what capability your app for each platform and version. See [Handling differing capabilities between Windows 8.1 and 10](/docs/appc/Titanium_SDK/Titanium_SDK_Guide/Appendices/tiapp.xml_and_timodule.xml_Reference/#HandlingdifferingcapabilitiesbetweenWindows8.1and10) for some examples on for Windows 8.1 and Windows 10 capabilities.

This release also includes support of localization ([TIMOB-20315](https://jira.appcelerator.org/browse/TIMOB-20315)) that includes localization of application name and properties for the Ti.Locale module:

`currentCountry`

`currentLanguage`

`currentLocale`

`getCurrencyCode`

`getCurrencySymbol`

`getLocaleCurrencySymbol`

On the SDK and tooling side, we added support for Windows 10 detection and tooling without requiring the user to also have Windows 8.1 SDK/tooling ([TIMOB-20198](https://jira.appcelerator.org/browse/TIMOB-20198)). Listing of emulators was improved when no specific Windows SDK version is specified to include all available emulators ([TIMOB-20571](https://jira.appcelerator.org/browse/TIMOB-20571) and [TISTUD-8447](https://jira.appcelerator.org/browse/TISTUD-8447)). The SDK no longer requires explicit setting of t he --wp-sdk option for SDK version when the version of the SDK can be determined by the chosen emulator (i.e. If a user chooses to build for a Windows 10 emulator, they no longer _also_ have to provide the \--wp-sdk 10.0 flag). Updated CLI and tooling to support deploying to Windows 10 mobile devices and emulators ([TIMOB-20096](https://jira.appcelerator.org/browse/TIMOB-20096)). And, to support Windows 10 policy changes for signing apps, we now support generating private keys to sign for Windows 10 mobile apps. FA temporary key is generated for development if the user has no certificate or private key ([TIMOB-20145](https://jira.appcelerator.org/browse/TIMOB-20145)).

Finally, we updated Ti.Media.AudioPlayer’s use of background audio APIs due to changes in Windows 10 API ([TIMOB-20080](https://jira.appcelerator.org/browse/TIMOB-20080)) and added support for handling window size under the Windows 10 Store desktop apps ([TIMOB-20187](https://jira.appcelerator.org/browse/TIMOB-20187)).

## New Features

### Windows Platform

*   [TIMOB-17917](https://jira.appcelerator.org/browse/TIMOB-17917) - Windows: Implement Ti.Media.AudioRecorder
    
    *   Implemented the [Ti.Media.AudioRecoder](#!/api/Titanium.Media.AudioRecorder) API
        
*   [TIMOB-20163](https://jira.appcelerator.org/browse/TIMOB-20163) - Windows: Add Contact group functionality for Windows 10
    
    *   Added support for [Ti.Contacts](#!/api/Titanium.Contacts), [Ti.Contacts.Group](#!/api/Titanium.Contacts.Group), and [Ti.Contacts.Person](#!/api/Titanium.Contacts.Person) for Windows 10
        
*   [TIMOB-20257](https://jira.appcelerator.org/browse/TIMOB-20257) - Windows: Support Ti.Blob.imageAs\* methods
    
    *   Implemented image manipulation for Windows Phone
        
    *   Please note that Ti.Blob.imageAsThumbnail doesn't support/ignores the borderSize and cornerRadius arguments.
        

## Community Credits

*   [Andrey Tkachenko](https://github.com/falkolab) for several exceptional issues including those affecting ScrollableView ([TIMOB-20116](https://jira.appcelerator.org/browse/TIMOB-20116) and [TIMOB-23134](https://jira.appcelerator.org/browse/TIMOB-23134))
    
*   [Michael Gangolf](https://github.com/m1ga) for several exceptional issues that among others includes his contributions to android video, android padding, and tint button features
    
*   [Jason Kneen](https://github.com/jasonkneen) for numerous updates one of which includes updating [iOS.yml](https://github.com/appcelerator/titanium_mobile/pull/7926)
    
*   [Manuel Lehner](https://github.com/manumaticx) for contributing to [TIMOB-15424](https://jira.appcelerator.org/browse/TIMOB-15424) fixes default color and updates doc
    
*   Sergey Volkov for contributing to (Android) Use getExternalCacheDir() for temp ([TIMOB-20470](https://jira.appcelerator.org/browse/TIMOB-20470))
    
*   [Timan Rebel](https://github.com/timanrebel) for his contribution on support remote debugging / inspecting of Android webviews ([TIMOB-18066](https://jira.appcelerator.org/browse/TIMOB-18066))
    
*   [Alex Montgomery](mailto:alex@appwapp.com) for contributing to add session identifiers to urlSession events
    

## Fixed Issues

*   [CLI-978](https://jira.appcelerator.org/browse/CLI-978) - Appc config get <key> always returns null
    
*   [CLI-987](https://jira.appcelerator.org/browse/CLI-987) - Appcelerator Login not triggered when login is required on production build
    
*   [TIMOB-19673](https://jira.appcelerator.org/browse/TIMOB-19673) - windowslib: visualstudio.detect failed for VS 2015
    
*   [TIMOB-19937](https://jira.appcelerator.org/browse/TIMOB-19937) - Windows: Titanium.UI.ImageView animation events
    
*   [TIMOB-19954](https://jira.appcelerator.org/browse/TIMOB-19954) - Windows: Implement ImageView properties
    
*   [TIMOB-19958](https://jira.appcelerator.org/browse/TIMOB-19958) - Windows: Missing events in ScrollableView
    
*   [TIMOB-19959](https://jira.appcelerator.org/browse/TIMOB-19959) - Windows: Missing events in ScrollView
    
*   [TIMOB-19960](https://jira.appcelerator.org/browse/TIMOB-19960) - Windows: background color/image for Ti.UI.Tab and TabGroup
    
*   [TIMOB-19964](https://jira.appcelerator.org/browse/TIMOB-19964) - Windows: attributedString for Label
    
*   [TIMOB-20035](https://jira.appcelerator.org/browse/TIMOB-20035) - Windows:Ti.Media.AudioPlayer => allowBackground has no effect
    
*   [TIMOB-20095](https://jira.appcelerator.org/browse/TIMOB-20095) - Windows: Cannot deploy app to Win 10 Mobile emulator
    
*   [TIMOB-20097](https://jira.appcelerator.org/browse/TIMOB-20097) - Windows: Windows 10 Mobile requires pfx
    
*   [TIMOB-20143](https://jira.appcelerator.org/browse/TIMOB-20143) - Windows: Titanium.UI.WebView don't load local html page
    
*   [TIMOB-20155](https://jira.appcelerator.org/browse/TIMOB-20155) - Windows: Ti.Codec.encodeNumber hangs on Windows 10
    
*   [TIMOB-20166](https://jira.appcelerator.org/browse/TIMOB-20166) - Windows: Window.fullscreen on Windows 10 doesn't work
    
*   [TIMOB-20167](https://jira.appcelerator.org/browse/TIMOB-20167) - Windows: Platform.version on Windows 10
    
*   [TIMOB-20172](https://jira.appcelerator.org/browse/TIMOB-20172) - Windows 10: Cannot package for the phonestore or winstore
    
*   [TIMOB-20173](https://jira.appcelerator.org/browse/TIMOB-20173) - Windows: Ti.Platform.username on Windows 10
    
*   [TIMOB-20190](https://jira.appcelerator.org/browse/TIMOB-20190) - Titanium.Database.ResultSet.fieldName(\[index\]) is not returning the correct value
    
*   [TIMOB-20191](https://jira.appcelerator.org/browse/TIMOB-20191) - The e.source of a table click event is supposed to return the table row but instead it returns the table view
    
*   [TIMOB-20192](https://jira.appcelerator.org/browse/TIMOB-20192) - \[Windows Phone 8.1\] Certification reject - This API is not supported for this application type - Api=OutputDebugStringA. Module=api-ms-win-core-debug-l1-1-1.dll
    
*   [TIMOB-20195](https://jira.appcelerator.org/browse/TIMOB-20195) - Windows: The textAlign and verticalAlign property of the label is not working on windows phone
    
*   [TIMOB-20222](https://jira.appcelerator.org/browse/TIMOB-20222) - Windows: Error while createcollection on Windows Phone
    
*   [TIMOB-20236](https://jira.appcelerator.org/browse/TIMOB-20236) - Windows: Downloaded image not show in ImageView
    
*   [TIMOB-20246](https://jira.appcelerator.org/browse/TIMOB-20246) - Windows: generate\_project.js does not set MSBuild version
    
*   [TIMOB-20282](https://jira.appcelerator.org/browse/TIMOB-20282) - Windows: ProgressBar default layout should be SIZE, not FILL
    
*   [TIMOB-20288](https://jira.appcelerator.org/browse/TIMOB-20288) - Windows: File.write can't handle UTF-8 string
    
*   [TIMOB-20370](https://jira.appcelerator.org/browse/TIMOB-20370) - Windows: Running desktop app doesn't show logs in console
    
*   [TIMOB-20372](https://jira.appcelerator.org/browse/TIMOB-20372) - Windows: Ti.App.fireEvent and listener doesnt work in static javascript/html page loaded in webview
    
*   [TIMOB-20382](https://jira.appcelerator.org/browse/TIMOB-20382) - Windows: Custom iconic fonts do not render properly.
    
*   [TIMOB-20385](https://jira.appcelerator.org/browse/TIMOB-20385) - Windows: ScrollView does not respect \`top\` property on views
    
*   [TIMOB-20386](https://jira.appcelerator.org/browse/TIMOB-20386) - Windows: View based click event are not working consistently
    
*   [TIMOB-20440](https://jira.appcelerator.org/browse/TIMOB-20440) - Android 6.0: writing to applicationDataDirectory fails without External storage permissions
    
*   [TIMOB-20478](https://jira.appcelerator.org/browse/TIMOB-20478) - Windows: Implement missing Ti.Locale properties
    
*   [TIMOB-20480](https://jira.appcelerator.org/browse/TIMOB-20480) - Windows: Implement missing Ti.Locale functions
    
*   [TIMOB-20481](https://jira.appcelerator.org/browse/TIMOB-20481) - Windows: Support l10n application name
    
*   [TIMOB-20566](https://jira.appcelerator.org/browse/TIMOB-20566) - Windows: Building to a Windows 10 mobile device errors with 'Failed to conect to emulator'
    
*   [TIMOB-20569](https://jira.appcelerator.org/browse/TIMOB-20569) - Windows: View visible property doesn't seem to work on Windows phone
    
*   [TIMOB-20572](https://jira.appcelerator.org/browse/TIMOB-20572) - Windows: Windows 10 Mobile device is listed as available to build to when not connected by USB
    
*   [TIMOB-20581](https://jira.appcelerator.org/browse/TIMOB-20581) - Windows: Ti App Properties Crashes while storing large data
    
*   [TIMOB-20598](https://jira.appcelerator.org/browse/TIMOB-20598) - Windows: views not animating correctly
    
*   [TIMOB-20600](https://jira.appcelerator.org/browse/TIMOB-20600) - Windows: close window throws unknown exception
    
*   [TIMOB-20601](https://jira.appcelerator.org/browse/TIMOB-20601) - Windows: Support bindId property on ListView
    
*   [TIMOB-20605](https://jira.appcelerator.org/browse/TIMOB-20605) - Windows: view.center not working
    
*   [TIMOB-20609](https://jira.appcelerator.org/browse/TIMOB-20609) - Windows: ImageView.image doesn't handle Windows-style path
    
*   [TIMOB-20612](https://jira.appcelerator.org/browse/TIMOB-20612) - Windows: postlayout events not firing
    
*   [TIMOB-20613](https://jira.appcelerator.org/browse/TIMOB-20613) - Android native modules build is getting failed with Android NDK r11
    
*   [TIMOB-20625](https://jira.appcelerator.org/browse/TIMOB-20625) - SplashScreen is used for "Ti.App.forceSplashAsSnapshot" instead of LaunchScreen
    
*   [TIMOB-20627](https://jira.appcelerator.org/browse/TIMOB-20627) - iOS: App rejected by Apple due to use of the nativeObject API
    
*   [TIMOB-23127](https://jira.appcelerator.org/browse/TIMOB-23127) - Windows: Ti.Network.HTTPClient.setRequestHeader is crashing
    
*   [TIMOB-23146](https://jira.appcelerator.org/browse/TIMOB-23146) - iOS/WatchOS: Installing to Simulators hangs since Xcode 7.3
    
*   [TIMOB-23170](https://jira.appcelerator.org/browse/TIMOB-23170) - If you launch the default Alloy app on Windows 8.1 emulator, "\[ERROR\] \[object CallbackObject\]" appears in the console
    
*   [TIMOB-23171](https://jira.appcelerator.org/browse/TIMOB-23171) - Cannot package Alloy app for dist-winstore
    
*   [TIMOB-23172](https://jira.appcelerator.org/browse/TIMOB-23172) - Default min-ios-ver and default enable-launch-screen-storyboard combination rejected by Apple
    
*   [TIMOB-23181](https://jira.appcelerator.org/browse/TIMOB-23181) - Windows: Install of app to Windows 10 Mobile device fails on second build of application
    
*   [TIMOB-23192](https://jira.appcelerator.org/browse/TIMOB-23192) - Windows: Prompt for selecting wp-sdk option contains unsupported 8.0
    
*   [TIMOB-23208](https://jira.appcelerator.org/browse/TIMOB-23208) - CLI: Error when building for Windows Phone
    
*   [TIMOB-23214](https://jira.appcelerator.org/browse/TIMOB-23214) - Windows: raulriera/XHR doesn't work with HTTPClient implementation
    
*   [TIMOB-23217](https://jira.appcelerator.org/browse/TIMOB-23217) - Windows: Packaging for dist-winstore with 8.1 SDK fails
    
*   [TIMOB-23223](https://jira.appcelerator.org/browse/TIMOB-23223) \- Windows: No splash screen when deploying alloy app to windows 10 mobile
    
*   [TIMOB-23235](https://jira.appcelerator.org/browse/TIMOB-23235) \- Windows: Splash screen on Win 10 mobile doesn't look right
    
*   [TIMOB-23237](https://jira.appcelerator.org/browse/TIMOB-23237) - Windows: Inconsistencies in Ti.API.log
    

## Improvements

*   [CLI-963](https://jira.appcelerator.org/browse/CLI-963) - CLI: enable template options when creating Alloy project
    
    *   Added feature that allows for creating two\_tabbed Alloy project from CL
        
*   [TIMOB-18066](https://jira.appcelerator.org/browse/TIMOB-18066) - Support remote debugging / inspecting of Android webviews
    
    *   Support remote debugging and inspecting of Android webviews
        
*   [TIMOB-18531](https://jira.appcelerator.org/browse/TIMOB-18531) - Windows: Use default publisher-guid when none is given on build
    
    *   Ti CLI now uses a default publisher GUID for non-production builds (00000000-0000-1000-8000-000000000000) and will prompt developers to enter a guid only when building for dist-phonestore or dist-winstore with no value for windows.publisherId configured
        
*   [TIMOB-18707](https://jira.appcelerator.org/browse/TIMOB-18707) - Windows: Support Ti.UI.View border\* properties
    
    *   Added support for Ti.UI.View border properties (borderColor, borderRadius, and borderWidth)
        
*   [TIMOB-19946](https://jira.appcelerator.org/browse/TIMOB-19946) - Windows: Implement Titanium.UI.AlertDialog.hide
    
    *   Added Titanium.UI.AlertDialog.hide for Windows
        
*   [TIMOB-20085](https://jira.appcelerator.org/browse/TIMOB-20085) - Windows: ti clean should cleanup VS temporary build directory
    
    *   The ti clean command cleans up the temporary build directory
        
*   [TIMOB-20241](https://jira.appcelerator.org/browse/TIMOB-20241) - Windows: Implement Ti.UI.View.convertPointToView( point, destinationView )
    
    *   Implemented the [Ti.UI.View.convertPointToView](#!/api/Titanium.UI.View-method-convertPointToView) method
        
*   [TIMOB-20281](https://jira.appcelerator.org/browse/TIMOB-20281) - Windows: Implement enabled property for View
    
    *   Implemented the Ti.UI.View.enabled property. This is currently not in our docs, but Android (and now Windows) has it. This makes it so that the backgroundDisabledColor and backgroundDisabledImage would be shown when enabled is set to false (otherwise, I’m not sure when those values would ever be used). Other than that, I don’t think it “disables” all the controls on the view from being clickable/editable/etc for us. Since this wasn’t really defined ind acs, I’m guessing we may need to revisit and make sure we’re in parity with Android.
        

## API Changes

The following APIs are deprecated in Release 5.3.0.Beta.

API

Type

Notes

Titanium.UI.Picker.getUseSpinner

method

This property is deprecated. Please use the default native "dropdown" style.

Titanium.UI.Picker.setUseSpinner

method

This property is deprecated. Please use the default native "dropdown" style.

Titanium.UI.Picker.useSpinner

property

This property is deprecated. Please use the default native "dropdown" style.