{"title":"In-place App Upgrading","weight":"30"} 

# In-place App Upgrading

As of AMPLIFY Runtime Services (API Runtime Services) 1.6.0, the in-place app will no longer be supported. We recommend a rolling upgrade (via appc acs publish) and utilizing more than one server to avoid app downtime.

## Overview

Currently, we ensure that there is no downtime when an app is upgraded (re-published) or when the environment variables have changed. Implementation happens by launching the same number of Docker containers for a new publish as for existing containers. New and existing containers run in parallel for a while before the new containers go online, and the previously existing containers are destroyed. This process is safe and will provide smooth upgrades for apps.

However, it may not be desired in some cases since the process needs twice as many resources (containers) when upgrading. This issue becomes significant when an app uses many containers. For example, if an app runs 100 containers, and upgrade would require an additional 100 containers. Even though the old 100 containers will be destroyed after the upgrade is complete, this process may not be affordable.

As an alternative to this expensive process, we provide support for in-place upgrading. This process will not require any additional containers, but it will cause some downtime.

## Zero-downtime upgrade property

A new property has been added to manage "zero-downtime upgrading" (enabled by default).

![image2015-12-18_11-37-54](/Images/appc/download/attachments/46245227/image2015-12-18_11-37-54.png)

As illustrated in the image above, Zero-downtime upgrading is set to true. A true setting will perform the app upgrade by the normal means (create new containers and destroy the old ones). If this property is set to false, no new containers will be created (in-place), and you can expect downtime.

From the command line, you can use the \--nodowntime flag to set this property:

`appc acs config --nodowntime` `false`

`appc acs config --nodowntime` `true`

## One-time In-place Upgrade

As noted above, when Zero-downtime upgrading is set to true, the upgrade will use additional containers. However, you can disable this with an option when publishing:

`appc acs publish --force --inplace`

The inplace flag makes upgrading happen in-place for this one time.

Similarly:

`appc acs config --set key=value --inplace`

This makes environment variable change happen in-place for this one time.