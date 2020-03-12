{"title":"Arrow Cloud 1.3.0 - 17 September 2015","weight":"40"} 

This release of Arrow Cloud includes version 1.0.27 of the CLI and 1.3.0 of the server and includes behavior changes.

**Behavior Changes**

*   The scripts specified by the scripts.preinstall and scripts.postinstall fields in the package.json file no longer support installing custom binaries outside the project directory. Instead, create a script called install.sh located at the root level of the project folder to install the custom binaries. You can still use the scripts.preinstall and scripts.postinstall scripts to install binaries inside the project folder.
    

**New Features and Improvements**

*   **Build logs**: To view the application build logs, pass the \--build\_log flag to the [loglist command](/docs/appc/Axway_API_Builder/AMPLIFY_Runtime_Services/AMPLIFY_Runtime_Services_Guide/AMPLIFY_Runtime_Services_Command-Line_Interface_Reference/).
    
*   **Install custom binaries**: To install custom binaries, create a script called install.sh located at the root level of the project to install the custom binaries. See [API Builder Project](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Project/).
    
*   **Restart command**: To restart a server, pass the \--restart <SERVER\_ID> option to the [server command](/docs/appc/Axway_API_Builder/AMPLIFY_Runtime_Services/AMPLIFY_Runtime_Services_Guide/AMPLIFY_Runtime_Services_Command-Line_Interface_Reference/#server). You may want to restart the server if the memory or CPU usage becomes too high. To get the server ID the application is running on, use the list command.
    
*   **Timestamps**: The loglist and logcat commands now display a timestamp next to the log output.