{"title":"Basic Concepts","weight":"10"}

In an Eclipse-based IDE, the **Workbench** is a desktop environment where you create and manage projects. The workbench consists of **Editors** and **Views** organized into **Perspectives**. The workbench consists of several different components, as described below. The screenshot below displays the workbench in the Studio Default perspective.

![WorkbenchAnnotated](/Images/appc/download/attachments/30083295/WorkbenchAnnotated.png)

## Workspace

A workspace is a folder where new projects are created and where Studio stores your preferences. On the first launch of Studio, you are prompted to choose your workspace. You should group similar projects in the same workspace. To switch workspaces, see [Switching your Workspace](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Basic_Concepts/Switching_your_Workspace/).

## Editor

An editor lets you modify the contents of a file. You can associate files with either a Studio editor or an external editor. By default, Studio opens files based on the file associations. For example, by default, XML files (files with an .xml extension) are opened in Alloy XML editor except for the tiapp.xml file which is opened in the TiApp editor.

If you do not want to open the file in its default editor, in the **Project Explorer** view, right-click the file, select **Open With...**, then choose an Editor to open the file or **Other...** to select from a list of Editors. You can also [change your file association preferences](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Basic_Concepts/Editors/Changing_your_file_association_preferences/) to make the changes permanent.

For more information about Editors, see [Editors](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Basic_Concepts/Editors/).

## View

A view displays information about your project or provides a way to navigate through the resources in your project. For example, the [Project Explorer view](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Basic_Concepts/Views/Project_Explorer_View/) helps you navigate through the files in your project, the [Outline view](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Basic_Concepts/Views/Outline_View/) presents a hierarchy of XML elements, functions or variables depending on the file opened in the Editor, and the [Console view](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Web_Development/JavaScript_Development/Debugging_JavaScript/Using_the_Console_View/) displays logs about the application build process.

For more information about Views, see [Views](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Basic_Concepts/Views/).

## Perspective

A perspective is a collection of views and editors configured for a specific task. For example, use the Studio Default Perspective for coding your project and the [Debug Perspective](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Web_Development/JavaScript_Development/Debugging_JavaScript/About_the_Debug_perspective/) to test and debug your application. To change perspectives, see [Changing the Workbench Perspective](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Basic_Concepts/Changing_the_Workbench_Perspective/).

## Toolbar

The workbench toolbar provides shortcuts to common Studio commands.

## Status Bar

The status bar displays extra information for the active view or editor. For example, when a file is selected in the Project Explorer view, the status bar displays the path to the file, and when the Editor is selected, the status bar displays the column and row numbers as well as the write and insertion modes.

## Chapters

* [Editors](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Basic_Concepts/Editors/)

    * [Navigating Open Files with Next Editor or Previous Editor](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Basic_Concepts/Editors/Navigating_Open_Files_with_Next_Editor_or_Previous_Editor/)

    * [Modifying Editor Colors](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Basic_Concepts/Editors/Modifying_Editor_Colors/)

    * [Changing your file association preferences](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Basic_Concepts/Editors/Changing_your_file_association_preferences/)

* [Views](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Basic_Concepts/Views/)

    * [Bookmarks View](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Basic_Concepts/Views/Bookmarks_View/)

    * [Outline View](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Basic_Concepts/Views/Outline_View/)

    * [Problems View](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Basic_Concepts/Views/Problems_View/)

        * [Adding custom error message filters to the Problems View](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Basic_Concepts/Views/Problems_View/Adding_custom_error_message_filters_to_the_Problems_View/)

        * [Enabling and disabling validation](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Basic_Concepts/Views/Problems_View/Enabling_and_disabling_validation/)

    * [Project Explorer View](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Basic_Concepts/Views/Project_Explorer_View/)

    * [Properties View](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Basic_Concepts/Views/Properties_View/)

    * [Tasks View](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Basic_Concepts/Views/Tasks_View/)

* [Working with Projects](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Basic_Concepts/Working_with_Projects/)

    * [Importing an Existing Project](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Basic_Concepts/Working_with_Projects/Importing_an_Existing_Project/)

    * [Comparing Different Versions of a File](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Basic_Concepts/Working_with_Projects/Comparing_Different_Versions_of_a_File/)

    * [Creating a New Project File](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Basic_Concepts/Working_with_Projects/Creating_a_New_Project_File/)

    * [Setting the Encoding of Your Text Files](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Basic_Concepts/Working_with_Projects/Setting_the_Encoding_of_Your_Text_Files/)

    * [Recovering a Deleted File with Local History](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Basic_Concepts/Working_with_Projects/Recovering_a_Deleted_File_with_Local_History/)

    * [Displaying Dot Files and Folders](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Basic_Concepts/Working_with_Projects/Displaying_Dot_Files_and_Folders/)

    * [Rolling Back a File Version](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Basic_Concepts/Working_with_Projects/Rolling_Back_a_File_Version/)

    * [Changing Your Project Type](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Basic_Concepts/Working_with_Projects/Changing_Your_Project_Type/)

    * [Using Open Declaration to jump to another location in your code](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Basic_Concepts/Working_with_Projects/Using_Open_Declaration_to_jump_to_another_location_in_your_code/)

* [Content Assist](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Basic_Concepts/Content_Assist/)

    * [About Content Assist](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Basic_Concepts/Content_Assist/About_Content_Assist/)

    * [Displaying Content Assist](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Basic_Concepts/Content_Assist/Displaying_Content_Assist/)

* [Changing the Workbench Perspective](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Basic_Concepts/Changing_the_Workbench_Perspective/)

* [Switching your Workspace](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Basic_Concepts/Switching_your_Workspace/)
