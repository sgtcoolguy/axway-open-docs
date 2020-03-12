{"title":"AMPLIFY CLI Commands","weight":"20"} 

# AMPLIFY CLI Commands

*   [Command options](#Commandoptions)
    
*   [auth](#auth)
    
    *   [auth list options](#authlistoptions)
        
    *   [auth login options](#authloginoptions)
        
    *   [auth logout options](#authlogoutoptions)
        
    *   [auth switch options](#authswitchoptions)
        
*   [config](#config)
    
*   [pm](#pm)
    
    *   [amplify pm install](#amplifypminstall)
        
    *   [amplify pm list](#amplifypmlist)
        
    *   [amplify pm purge](#amplifypmpurge)
        
    *   [amplify pm search](#amplifypmsearch)
        
    *   [amplify pm uninstall](#amplifypmuninstall)
        
    *   [amplify pm update](#amplifypmupdate)
        
    *   [amplify pm use](#amplifypmuse)
        
    *   [amplify pm view](#amplifypmview)
        

There are three basic commands for using AMPLIFY CLI (ACLI):

*   auth: Authenticate machines with the Axway AMPLIFY platform
    
*   config: get and set config options
    
*   pm: Package manager for Axway products
    

## Command options

If you need to specify a particular environment, use this option: **\--env=<name>**

Outputting accounts as JSON is a common option between all ACLI commands. To use this option, use the **\--json** flag.

## auth

amplify auth <command> \[options\] command will authenticate you machine with the Axway AMPLIFY platform

*   list: lists all authenticated accounts
    
*   login: log in to the Axway AMPLIFY platform
    
*   logout: log out all or specific accounts from the AMPLIFY platform
    
*   switch: select default account and organization
    

### auth list options

**amplify auth list \[options\]** command lists all authenticated accounts.

**Auth options**

*   **\--env=<name>**: the environment to use
    

There are no other extra options other than the ones mentioned above in [Command options](#Commandoptions).

### auth login options

amplify auth login \[options\] command logs one into the Axway AMPLIFY platform.

*   **\-c,--client-secret=<key>**: a secret key used to authenticate
    
*   \--force: re-authenticate even if the account is already authenticated
    
*   \--no-launch-browser: display the authentication URL instead of opening it in the default web browser
    
*   **\--org=<id|name>**: the organization to use
    
*   **\-p,--password=<pass>**: password to authenticate with
    
*   **\-s,--secret-file=<path>**: path to the PEM key used to authenticate
    
*   **\-u,--username=<user>**: username to authenticate with
    

Also, the extra options mentioned in [Command options](#Commandoptions) can be used here.

There are several ways one can use the ACLI auth command to login:

1.  Interactive browser: amplify auth login
    
2.  Client secret: amplify auth login --secret <key>
    
3.  Signed JWT: amplify auth login --secret-file <path\_to\_pem\_file>
    
4.  Username and password: amplify auth login --username <user> --password <pass>
    

### auth logout options

**amplify auth logout \[options\] \[<accounts...>\]** command logs the user out all or specific accounts from the AMPLIFY platform.

*   **\-a,--all**: revoke all credentials; supersedes list of accounts
    

Also, the extra options mentioned in [Command options](#Commandoptions) can be used here.

### auth switch options

amplify auth switch \[options\] command selects a default account and organization.

*   **\--account=<name>**: account to switch to
    
*   **\--org=<id|name>**: organization to switch to
    

Also, the extra options mentioned in [Command options](#Commandoptions) can be used here.

## config

**amplify config \[options\] <action> \[<key>\] \[<value>\]** command will get and set config options.

Config arguments:

*   action
    
*   key
    
*   value
    

Config options only includes the \--json flag as mentioned in [Command options](#Commandoptions).

## pm

**amplify pm <command> \[options\]** command is the package manager for Axway products.

*   install: installs the specified package
    
*   list: lists all installed packages
    
*   purge: purges all unused packages
    
*   search: searches registry for packages
    
*   uninstall: uninstalls the specified package
    
*   update: download updates for installed packages
    
*   use: activates a specific package version
    
*   **view**: displays info for a specific package
    

Also, the extra options mentioned in [Command options](#Commandoptions) can be used here.

For examples on how to use amplify pm command, see [Using the package manager](https://wiki.appcelerator.org/display/DB/AMPLIFY+CLI+Package+Manager#AMPLIFYCLIPackageManager-Usingthepackagemanager) section of [AMPLIFY CLI Package Manager](https://wiki.appcelerator.org/display/DB/AMPLIFY+CLI+Package+Manager).

### amplify pm install

amplify pm install \[options\] <package> command installs a specified package.

*   **<package>**: the package name and version to install
    

**Install options**

*   \--auth=<account>: the authorization account to use
    

Also, the extra options mentioned in [Command options](#Commandoptions) can be used here.

### amplify pm list

**amplify pm list \[options\]** command lists all installed packages.

Also, the extra options mentioned in [Command options](#Commandoptions) can be used here.

### amplify pm purge

amplify pm purge \[options\] \[<package>\] command will purge all unused packages.

*   **<package>**: name of the package for purging old versions
    

Also, the extra options mentioned in [Command options](#Commandoptions) can be used here.

### amplify pm search

**amplify pm search \[options\] \[<search>\]** command will search registry for packages

*   <search>: the package name or keywords
    

**Search options**

*   \--auth=<account>: the authorization account to use
    
*   **\--repository=<repository>**: repository to search
    
*   **\--type=<type>**: type of component to search
    

Also, the extra options mentioned in [Command options](#Commandoptions) can be used here.

If you get the following error, execute this command to set an environment: amplify config set env staging

`404` `-` `"<!DOCTYPE html>\n<html lang=\"en\">\n<head>\n<meta charset=\"utf-8\">\n<title>Error</title>\n</head>\n<body>\n<pre>Cannot GET /api/packages/v1/-/search</pre>\n</body>\n</html>\n"`

### amplify pm uninstall

**amplify pm uninstall \[options\] <package>** command will uninstall a specified package.

*   **<package>**: the package name and version to uninstall
    

Also, the extra options mentioned in [Command options](#Commandoptions) can be used here.

### amplify pm update

amplify pm update \[options\] \[<package>\] command will download updates for installed packages.

*   **<package>**: the package name to update
    

**Update options**

*   \--auth=<account>: the authorization account to use
    

Also, the extra options mentioned in [Command options](#Commandoptions) can be used here.

### amplify pm use

amplify pm use \[options\] <package> command will activate a specific package version.

*   <package>: the package version or latest to activate
    

Also, the extra options mentioned in [Command options](#Commandoptions) can be used here.

### amplify pm view

**amplify pm view \[options\] <package> \[<filter>\]** command will display info for a specific package.

*   <package>: the package name and version to install
    
*   <filter>: display specific package fields
    

**View options**

*   \--type=<name>: the package type
    

Also, the extra options mentioned in [Command options](#Commandoptions) can be used here.