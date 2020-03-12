{"title":"Installing the Android NDK","weight":"50"} 

# Installing the Android NDK

## Contents

*   [Compatibility and Download](#CompatibilityandDownload)
    
*   [Installation](#Installation)
    

## Compatibility and Download

The Android NDK is required to build native modules for Android, or to build the Titanium SDK from source.

The NDK is **not** required to build, run, or distribute apps using the Titanium SDK.

Titanium supports NDK Revision 12.

Download the appropriate NDK archive from the following site:

![download_05](/Images/appc/download/attachments/29004836/download_05.png)

[Download the Android NDK on developer.android.com](http://developer.android.com/sdk/ndk/index.html)

## Installation

To install the Android NDK, simply expand the archive in the folder where you want to install it.

The path to the NDK must not contain spaces or special characters, such as a dollar sign, ampersand, etc.

After installing the NDK, define an environment variable identifying the path to the NDK. For example,  
on OS X, you might add the following to your .bash\_profile:

`export ANDROID_NDK=~/android-ndk-r9d` `//path to your NDK`