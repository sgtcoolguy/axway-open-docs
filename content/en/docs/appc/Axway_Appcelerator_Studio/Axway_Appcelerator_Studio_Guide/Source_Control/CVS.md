{"title":"CVS","weight":"10"} 

# CVS

*   [CVS Support](#CVSSupport)
    
*   [Installation](#Installation)
    
    *   [Eclipse CVS Functionality](#EclipseCVSFunctionality)
        
*   [Import or Checkout an CVS Respository](#ImportorCheckoutanCVSRespository)
    
    *   [Utilize the CVS Perspective](#UtilizetheCVSPerspective)
        
    *   [Additional CVS Questions](#AdditionalCVSQuestions)
        

## CVS Support

The Studio uses the [Eclipse CVS](http://www.eclipse.org/eclipse/platform-cvs/) to provide CVS support.

When updating or adding Eclipse plugins or software, the software repository varies with the version of Studio:

Appcelerator/Titanium Studio Version

Eclipse Repository Name

Eclipse Version

2.1.x

Helios

3.6

3.0.x - 3.1.3

Indigo

3.7

3.1.4 - 3.4.x

Kepler

4.3

4.0.0 - latest

Luna

4.4

**Please ask your Confluence administrator to update the license for the [MultiExcerpt Plugin for Confluence 4+](https://plugins.atlassian.com/plugins/biz.artemissoftware.confluence.multiexcerpt.MultiExcerptMacro) .**  
**Admin Info: The error is: license VERSION\_MISMATCH**

## Installation

In case you installed the Studio as a plugin to eclipse distribution, CVS is already bundled and ready to be used. In any other case, follow these instructions to install the CVS support.

*   Open the Studio's preferences and locate the 'Available Software Sites' page.
    
*   Make sure that the main Eclipse update site is checked 'on'. In this example, the update site is the Eclipse 'Helios' site. Click 'OK' to commit any changes made to this page and exit.
    
    ![update_sites](/Images/appc/download/attachments/30083196/update_sites.jpg)
    
*   Click **Help** -> **Install New Software**and select the Eclipse update site. It may take a couple of minutes to populate the plugin options.
    
    ![cvs_install](/Images/appc/download/attachments/30083196/cvs_install.jpg)
    
*   Select the CVS plugin and follow the wizard's 'Next' or 'Finish' to complete the installation.
    

### Eclipse CVS Functionality

*   Browser remote repository
    
*   Share project to the repository and checkout projects from the repository
    
*   Synchronize project to see incoming and outgoing changes
    
*   Commit, update and reverse changes
    
*   See resource change history
    
*   Merge changes
    

## Import or Checkout an CVS Respository

1.  Go to **File**\->**Import**
    
2.  Expand **CVS**
    
3.  Select Checkout Projects from CVS.
    
4.  Complete Wizard with your CVS repository details.
    

### Utilize the CVS Perspective

1.  Go to **Window** -> **Open Perspective...** -> **Other**.
    
2.  Select **CVS Respository Exploring**
    

### Additional CVS Questions

For advanced questions, we recommend checking out the [CVS FAQ](http://wiki.eclipse.org/index.php/CVS_FAQ)