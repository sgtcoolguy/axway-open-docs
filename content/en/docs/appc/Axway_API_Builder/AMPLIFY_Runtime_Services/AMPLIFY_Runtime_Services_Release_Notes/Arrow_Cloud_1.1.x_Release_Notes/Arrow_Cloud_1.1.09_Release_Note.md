{"title":"Arrow Cloud 1.1.9 - 05 March 2015","weight":"50"} 

This release of Arrow Cloud includes version 1.0.22 of the CLI and version 1.1.9 of the server.

## CLI 1.0.22

**Notice of Feature and Behavior Changes**

*   The appc cloud cname command has been deprecated in favor of the appc cloud domain command, which can bind an application to an A record in addition to a CNAME record.
    
*   The appc cloud config \--autoscale and \--setsize command options have been removed. To enable auto-scaling, use the \--autoscaleup and \--autoscaledown options. You can no longer set the current number of cloud servers to use with the \--setsize option. Instead, you can set the minimum number with the \--minsize option.
    

**New Features and Improvements**

*   New appc cloud domain command to bind either a CNAME or A record to an application. This command deprecates the appc cloud cname command, which can only bind a CNAME record to an application.
    
*   New appc cloud config \--minsize command option to set the minimum number of cloud servers the application can use.
    

## Server 1.1.9

**New Features and Improvements**

*   Support for wildcard subdomain routing.
    
*   Support for binding the application to an A record in addition to a CNAME record.
    
*   Add support for body-parser middleware, which makes the body of an HTTP request available as req.body in the controller of an MVC application. To enable the body-parser middleware, add the following line to the package.json file:
    
    `"bodyParser"``:` `true`
    

For legacy releases, see [http://docs.appcelerator.com/cloud/latest/#!/guide/node\_releasenotes](/arrowdb/latest/#!/guide/node_releasenotes).