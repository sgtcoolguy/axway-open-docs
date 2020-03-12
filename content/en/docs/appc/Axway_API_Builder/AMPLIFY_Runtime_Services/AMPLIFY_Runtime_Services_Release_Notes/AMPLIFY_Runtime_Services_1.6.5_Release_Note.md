{"title":"AMPLIFY Runtime Services 1.6.5 Release Note","weight":"10"} 

## AMPLIFY Runtime Services 1.6.5 - 18 October 2019

AMPLIFY Runtime Services 1.6.5 is a minor release, which includes improvements and several bug fixes.

## Improvement

*   Previously, the go-client (Arrow Cluster) configuration was read from the config/env\_vars.json file into a binary. This was to simplify the distribution and usage of the tool. Now, to allow configuration flexibility, the Arrow Cluster configuration is read from the working disk directory. If the Arrow Cluster configuration can't be read from the working disk directory, it is read from the built-in config/env\_vars.json configuration file.
    

## Additional improvements

*   Previously, AMPLIFY Runtime Services could not be deployed to run in an on-premise Azure container service. Now, AMPLIFY Runtime Services can be deployed and ran in an on-premise Azure container service.
    
*   Previously, the Amazon Web Services credentials were coded into the user.json input configuration file. Now, the Amazon Web Services credential is obtained from the environment and is no longer coded into the user.json input file.
    
*   Previously, the Amazon Web Services (AWS) credentials and region were coded into the user.json input configuration file.
    
    `{`
    
    `"platform"` `: {`
    
    `"infrastructure"` `:` `"aws"``,`
    
    `"aws"``: {`
    
    `"aws_access_key_id"``: AKIA``"xxxxx"``,`
    
    `"aws_secret_access_key"``:` `"xxxxxx"``,`
    
    `"aws_region"``:` `"us-west-1"`
    
    `}`
    
    `},`
    
    `...`
    
    Now, the AWS section has been removed from the user.json input configuration file.
    
    `{`
    
    `"platform"` `: {`
    
    `"infrastructure"` `:` `"aws"`
    
    `},`
    
    `...`
    
    And the AWS credentials are configured as environmental variables in the CLI using the **arrowcluster-vpc** command.
    
    `Usage: arrowcluster-vpc COMMAND [``command``-specific-options]`
    
    `Deploy and manage an ArrowCloud cluster` `in` `an AWS VPC environment. Type` `"arrowcluster-vpc COMMAND -h"`  `for`  `more` `details:`
    
    `Environment:`
    
    `AWS_REGION AWS region`
    
    `AWS_ACCESS_KEY_ID AWS access key` `id`
    
    `AWS_SECRET_ACCESS_KEY AWS secret access key`
    
    `AWS_SESSION_TOKEN [Optional] AWS session token (temporary security credentials)`
    
    `Commands:`
    
    `deploy deploy a new arrowcloud arrowcloud cluster` `in` `AWS VPC environment`
    
    `teardown teardown an existing arrowcloud AWS VPC cluster`
    
    `verify perform optional sanity checks after cluster installation`
    
    `upgrade upgrade an arrowcloud cluster to a new version`
    
    `downgrade downgrade an arrowcloud cluster to an old version`
    
    `add-host add new hosts to cluster`
    
    `info show arrowcloud VPCs and other resources`
    
    `Options:`
    
    `-h, --help output usage information`
    
    `-``v``, --version output the version of the cli`
    

## Fixed issues

*   Previously, events were not being reported on the preproduction server. Now, events are being properly reported on the preproduction server.
    
*   Previously, the fluentd-aggregator build process would error and stop working. Now, the fluentd-aggregator build process completes successfully.
    
*   Previously, the Apple Push Notification service (APNs) would error once per day. Now, the issue has been resolved, and the Apple Push Notification service no longer errors.
    
*   Previously, the size of /log and /data was wrong in the VAC deployment. Additionally, the mapping of the mount order was incorrect. Now, the issues in VAC deployment have been resolved.
    
*   Previously, deploying AMPLIFY Runtime Services using ACS CLI would error on startup due to missing modules. Now, deploying AMPLIFY Runtime Services using ACS CLI is successful, and there are no errors on startup.