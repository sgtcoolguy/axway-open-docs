{"title":"Android Module Upgrade Guide","weight":"40"} 

# Android Module Upgrade Guide

*   [Summary](#Summary)
    
*   [Migration to SDK 7.0.0](#MigrationtoSDK7.0.0)
    
*   [Manifest file](#Manifestfile)
    
    *   [apiversion](#apiversion)
        
    *   [minsdk](#minsdk)
        
    *   [architecture](#architecture)
        
    *   [Version](#Version)
        
*   [API updates](#APIupdates)
    

## Summary

With major releases of the Titanium SDK, you may need to update older modules. This document will provide you with the information to upgrade your Android modules as necessary.Titanium SDK 7.0.0 and later will require modules to be updated for the latest V8 version 6.x. This is done by changing the "manifest" file in the module project and recompiling them afterwards.

## Migration to SDK 7.0.0

When using Titanium SDK 7.0.0 and later, you can simply switch to your Android module project (e.g. cd ti.map/android) and use appc run -p android --build-only. The command will prompt you to confirm the migration and update your manifest file for you. The details of the migration are described below.

The following components of the Android manifest file need to be updated:

*   **architecture**: Add the "arm64-v8a" architecture to support 64 Bit on Android
    
*   **apiversion**: Update the value to "4"
    
*   **minsdk**: Update the value to "7.0.0" to indicate that developers should use Titanium SDK 7.0.0 and later
    
*   version: Update the value to the next major version (read more about semantic versioning [here](https://semver.org/)). If your module version is "1.2.0" right now, it should be revised to "2.0.0"
    

![Bildschirmfoto_2017-11-29_um_16.51.08](/Images/appc/download/attachments/52298697/Bildschirmfoto_2017-11-29_um_16.51.08.png)

That's it! After the migration, you can include your module inside a Titanium 7.0.0 project and benefit from the new V8 changes like [Chrome-debugging](https://developers.google.com/web/tools/chrome-devtools/remote-debugging/) and 64-bit compatibility.  
See an example of the exact changes being made:

![Bildschirmfoto_2017-11-29_um_16.51.32](/Images/appc/download/attachments/52298697/Bildschirmfoto_2017-11-29_um_16.51.32.png)

## Manifest file

The following tables provide an overview of the relations between different properties inside a native Android module project.

### apiversion

SDK

required apiversion

7.x

4

6.x

3

5.x

2

### minsdk

SDK

required apiversion

7.x

7.0.0.GA

6.x

6.0.0.GA

5.x

5.0.0.GA

### architecture

SDK

Architecture

7.x

arm64-v8a armeabi-v7a x86

6.x

armeabi-v7a x86

5.x

armeabi armeabi-v7a x86

### Version

Update the module version to the major version number.

## API updates

Please note any API changes. Refer to [Titanium SDK Release Notes](https://wiki.appcelerator.org/display/DB/Titanium+SDK+Release+Notes) for the latest info on changes to the API and/or the [API documentation](#!/api).