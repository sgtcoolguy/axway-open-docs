{"title":"Installing Required Python Packages","weight":"30"}

* [Overview](#Overview)

* [Compatibility and download](#Compatibilityanddownload)

* [Installation](#Installation)

  * [OS X](#OSX)

  * [Windows](#Windows)

* [Using EasyInstall to install packages](#UsingEasyInstalltoinstallpackages)

  * [PyCrypto](#PyCrypto)

  * [pyOpenSSL](#pyOpenSSL)

  * [PyYAML](#PyYAML)

  * [Pygments](#Pygments)

  * [Markdown](#Markdown)


## Overview

Python's setuptools is a third-party library that enhances the default Python distribution utilities (distutil). One of its components is the [EasyInstall](http://en.wikipedia.org/wiki/EasyInstall) (easy\_install) package manager, which is used to install a number of prerequisite libraries for compiling Titanium's SDK and API Docs.

## Compatibility and download

Python's setuptools can be installed from the following locations:

![download_05](/Images/appc/download/attachments/29004836/download_05.png)

Operating System

Package Version

Package Architecture Version

Download Location

OS X

Latest version compatible with installed Python version

32-bit and 64-bit

Installed on OS by default

Windows

Latest version compatible with installed Python version

32-bit **only**

[Official setuptools Website](http://pypi.python.org/pypi/setuptools#downloads)

Ubuntu

Latest version compatible with installed Python version

32-bit and 64-bit

Default Repositories

## Installation

Before attempting to install _setuptools_, ensure that you have followed the [Installing Python](/docs/appc/Titanium_SDK/Titanium_SDK_Getting_Started/Installation_and_Configuration/Installing_Titanium_Advanced_Tools/Installing_Python/) guide.

### OS X

Note that the typical file system location of this software can be found in the [mac OS Software Locations](/docs/appc/Titanium_SDK/Titanium_SDK_Getting_Started/Installation_and_Configuration/Software_Locations_and_Environment_Variables/#macOSSoftwareLocations) section of these guides.

OS X ships with _setuptools_ installed by default. Hence, simply follow the steps in the [Using EasyInstall to install packages](#UsingEasyInstalltoinstallpackages) section

### Windows

Note that the typical file system location of this software can be found in the [Windows Software Locations](/docs/appc/Titanium_SDK/Titanium_SDK_Getting_Started/Installation_and_Configuration/Software_Locations_and_Environment_Variables/#WindowsSoftwareLocations) section of these guides.

To install _setuptools_:

* Follow the official [Installation Instructions](http://pypi.python.org/pypi/setuptools).

* Verify that path/to/easy\_install is in the system PATH, by following the [Software Locations and Environment Variables](/docs/appc/Titanium_SDK/Titanium_SDK_Getting_Started/Installation_and_Configuration/Software_Locations_and_Environment_Variables/) guide.

* Follow the steps in the [Using EasyInstall to Install Packages](#UsingEasyInstalltoInstallPackages) section.


## Using EasyInstall to install packages

The following Python libraries are necessary for compiling Titanium's SDK and API Docs. Install them using the supplied commands. On Mac OS X, prefix the commands with sudo.

### PyCrypto

`easy_install pycrypto`

### pyOpenSSL

`easy_install pyopenssl`

### PyYAML

`easy_install pyyaml`

### Pygments

`easy_install Pygments`

### Markdown

Markdown is required for building module documentation when packaging a Titanium module.

`easy_install markdown`
