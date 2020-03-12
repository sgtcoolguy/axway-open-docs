{"title":"Mobile Backend Services 1.6.0.sp3 Release Note","weight":"30"} 

## Mobile Backend Services 1.6.0.sp3 - 26 February 2018

This release of Mobile Backend Services 1.6.0.sp3 includes the following fixed issues.

## Fixed issues

*   Previously, application scaling up or application scaling down caused all the application containers to be recreated. Now, applications can scale up or down without causing the application container to be recreated.
    
*   Previously, the Dashboard was unavailable in an on-premise cluster because the Dashboard backend was not generated in the haproxy.cfg file in the on-premise cluster. Now, the Dashboard backend is generated in the haproxy.cfg file in the on-premise cluster.
    
*   Previously, the VPC deployment cluster name could not contain any uppercase characters. Now, the VPC deployment cluster name can be a mix of upper and lower case characters.