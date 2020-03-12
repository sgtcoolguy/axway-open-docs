{"title":"Contributing API Documentation","weight":"10"} 

# Contributing API Documentation

**Contents**

*   [Overview](#Overview)
    
*   [Editing API Documentation](#EditingAPIDocumentation)
    
*   [Generating the HTML API Docs](#GeneratingtheHTMLAPIDocs)
    
*   [Validating API Doc Modifications](#ValidatingAPIDocModifications)
    
    *   [Validating on Windows](#ValidatingonWindows)
        
*   [Submitting Contributions](#SubmittingContributions)
    

## Overview

This guide describes how to submit changes to the Titanium SDK API documentation.

The process for getting the SDK source and submitting a pull request is identical to the process for code contributions, described in the [Pull Request Guide](/docs/appc/Titanium_SDK/Titanium_SDK_Guide/Contributing_to_Titanium/Platform_Development/Pull_Request_Guide/).

As with code contributions, you must electronically sign the [Contributors License Agreement (CLA)](http://developer.appcelerator.com/cla) before you can contribute documentation or any other materials to the project.

## Editing API Documentation

The API documentation is stored in the apidoc folder inside the [titanium\_mobile](https://github.com/appcelerator/titanium_mobile) repository.

The documentation is written in the Titanium Doc format, TDoc, which is documented in the [TDoc Specification](/docs/appc/Titanium_SDK/Titanium_SDK_Guide/Contributing_to_Titanium/Platform_Development/Specs/TDoc_Specification/).

API doc contributions should comply with the [Titanium API Doc Style Guide](/docs/appc/Titanium_SDK/Titanium_SDK_Guide/Contributing_to_Titanium/Documentation/Titanium_API_Doc_Style_Guide/).

## Generating the HTML API Docs

Python and some of its libraries must be installed to build the Titanium's API Docs. Refer to the [Installing Python](/docs/appc/Titanium_SDK/Titanium_SDK_Getting_Started/Installation_and_Configuration/Installing_Titanium_Advanced_Tools/Installing_Python/) and [Installing Required Python Packages](/docs/appc/Titanium_SDK/Titanium_SDK_Getting_Started/Installation_and_Configuration/Installing_Titanium_Advanced_Tools/Installing_Required_Python_Packages/) guides.

You can build the basic HTML version of the Titanium docs using the docgen.py script, as follows:

`cd /path/to/titanium_mobile/apidoc`

`python ./docgen.py`

The HTML files are then output to the /path/to/titanium\_mobile/dist/apidoc directory, with the index page at dist/apidoc/index.html.

## Validating API Doc Modifications

After changes have been made to the API Doc source, it's important to verify that the code is free from errors using the validate.py script:

`cd /path/to/titanium_mobile/apidoc`

`python ./validate.py`

### Validating on Windows

On Windows, as Command Line program cannot handle the UTF-8 characters of the validation report, the following error may be displayed:

`UnicodeEncodeError:` `'charmap'` `codec can``'t encode character u'``\u2713' in position` `1``: character maps to <undefined>`

A workaround for this is to only display a simple report, using the following command:

`cd /path/to/titanium_mobile/apidoc`

`python validate.py --errors-only --style=simple`

## Submitting Contributions

The process for contributing API Docs is the same as contributing code. Please refer to [Pull Request Guide](/docs/appc/Titanium_SDK/Titanium_SDK_Guide/Contributing_to_Titanium/Platform_Development/Pull_Request_Guide/) for guidance.