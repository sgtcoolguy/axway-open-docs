{"title":"Graphical Asset Specifications","weight":"90"} 

# Graphical Asset Specifications

*   [Overview](#Overview)
    
*   [Splash Screen](#SplashScreen)
    
*   [About Image - about.gif](#AboutImage-about.gif)
    
*   [Mac OSX DMG Background](#MacOSXDMGBackground)
    
*   [Windows Installer](#WindowsInstaller)
    
    *   [Left panel](#Leftpanel)
        
    *   [Top Panel](#TopPanel)
        
    *   [Bottom Panel](#BottomPanel)
        
    *   [Installer Splash](#InstallerSplash)
        
    *   [Background Color](#BackgroundColor)
        
*   [In-Product Imagery](#In-ProductImagery)
    
    *   [General Icons](#GeneralIcons)
        
    *   [Wizard Banners](#WizardBanners)
        

## Overview

A collection of all of the various assets required when developing Aptana And Titanium Studio branding.

## Splash Screen

![splash](/Images/appc/download/attachments/33031056/splash.bmp)

Filename

splash.bmp

Dimension

590 x 405 pixels

Notes

The space to the right of the Appcelerator logo should be left blank for the login user interface

Usage:

Splash screen

![Screen_Shot_2012-10-30_at_Oct_30%2C2.39.56_PM](/Images/appc/download/attachments/33031056/Screen_Shot_2012-10-30_at_Oct_30%2C2.39.56_PM.png)

## About Image - about.gif

![about](/Images/appc/download/attachments/33031056/about.gif)

Filename

about.gif

Dimension

131 x 222 pixels

Usage:

About Dialog

![Screen_Shot_2012-10-30_at_Oct_30%2C2.50.17_PM](/Images/appc/download/attachments/33031056/Screen_Shot_2012-10-30_at_Oct_30%2C2.50.17_PM.png)

## Mac OSX DMG Background

![background](/Images/appc/download/attachments/33031056/background.gif)

Filename

com.appcelerator.titanium.mac.installer/dmgbuilder/background.png

Dimensions

600 x 600 pixels

Notes

*   Ensure the top-left label background accommodates the width/height of a wrapped product name
    
*   Copyright should be updated appropriately
    

Usage:

DMG installer

![Screen_Shot_2012-10-30_at_Oct_30%2C2.56.44_PM](/Images/appc/download/attachments/33031056/Screen_Shot_2012-10-30_at_Oct_30%2C2.56.44_PM.png)

## Windows Installer

The installer uses three images that are butted up against each other to compose window: Left panel, the top panel and the bottom panel  
![Screen_Shot_2012-10-30_at_Oct_30%2C3.01.25_PM](/Images/appc/download/attachments/33031056/Screen_Shot_2012-10-30_at_Oct_30%2C3.01.25_PM.png)

### Left panel

![LeftBranding](/Images/appc/download/attachments/33031056/LeftBranding.bmp)

Filename

com.appcelerator.win.installer/windows-nsis/Tools/unicode\_nsis/Contrib/ExperienceUI/Skins/Appcelerator/LeftBranding.bmp

Dimensions

240 x 349 pixels

Notes

Ensure the color of the right most edge matches the color set in the installer. The color in the installer can be modified

### Top Panel

![Header](/Images/appc/download/attachments/33031056/Header.bmp)

Filename

com.appcelerator.win.installer/windows-nsis/Tools/unicode\_nsis/Contrib/ExperienceUI/Skins/Appcelerator/Header.bmp

Dimensions

1 x 57 pixels

Notes

The one pixel strip is repeated across the header. The strip should include the border between the title and the main content

### Bottom Panel

![Bottom](/Images/appc/download/attachments/33031056/Bottom.bmp)

Filename

com.appcelerator.win.installer/windows-nsis/Tools/unicode\_nsis/Contrib/ExperienceUI/Skins/Appcelerator/Bottom.bmp

Dimensions

693 x 70 pixels

### Installer Splash

(Same images as the splash.bmp)

Filename

com.appcelerator.win.installer/windows-nsis/Bitmaps/splash.bmp

Dimension

590 x 405 pixels

Notes

Same as splash.bmp

### Background Color

The background color can be updated in the following files:

File: builders/com.appcelerator.win.installer/windows-nsis/Tools/unicode\_nsis/Contrib/ExperienceUI/Skins/Appcelerator.xpuiskin

Property: XPUI\_TEXT\_BGCOLOR

Files: builders/com.appcelerator.win.installer/windows-nsis/JREDyna\_Inetc.nsh, builders/com.appcelerator.win.installer/windows-nsis/Titanium Studio.nsi

Property: setCtlColors

## In-Product Imagery

### General Icons

Icons should be 16 x 16 pixel PNG files. While 16px is the maximum width and height, it is preferred if the actual icon is a pixel or two smaller than that. See the [Eclipse Guidelines](http://wiki.eclipse.org/User_Interface_Guidelines#Icon_Size_.26_Placement) for further hints on icons.

When possible, attempt to keep the color scheme and overall feel similar to existing icons. A selection of icons from the product is included below:

![shield_on](/Images/appc/download/attachments/33031056/shield_on.png) ![dev_toolbox](/Images/appc/download/attachments/33031056/dev_toolbox.png) ![event](/Images/appc/download/attachments/33031056/event.gif) ![html](/Images/appc/download/attachments/33031056/html.png) ![loglevel](/Images/appc/download/attachments/33031056/loglevel.png) ![mobileweb](/Images/appc/download/attachments/33031056/mobileweb.png) ![web_project_small_16x16](/Images/appc/download/attachments/33031056/web_project_small_16x16.png) ![ruby_rails_project_small_16x16](/Images/appc/download/attachments/33031056/ruby_rails_project_small_16x16.png)

Note the icons are colorful and shaded, with a generally "dimensional" feel.

![web](/Images/appc/download/attachments/33031056/web.png)

Filename

web.png

Dimensions

16 x 16 pixels

### Wizard Banners

Wizard banner graphics are designed to fit within a specified screen space of 75 x 66 pixels on the right side of the wizard banner, with a main overlay image of around 67 x 50 pixels in size. Center the image vertically, and off-center to the left horizontally.

Use the file below as the background of the image and save as a PNG with transparency

![wizard_background](/Images/appc/download/attachments/33031056/wizard_background.png)

Filename

wizard\_background.png

Dimensions

75 x 66 pixels