{"title":"Mobile Backend Services 1.6.0.sp1 - 27 July 2017","weight":"50"}

This release of Mobile Backend Services (MBS) includes version 2.0.5 of the CLI and 1.6.0.sp1 of the server and includes behavior changes, new features and improvements, and several bug fixes.

MBS 1.6.0.sp1 introduces mandatory dedication of three (3) swarm manager VMs in the production cluster. If you have a production deployment using 1.6.0 on-premise cluster, you will need to add these additional swarm manager hosts by following these steps:

1. Prepare three additional hosts according to the requirements when setting up the cluster initially. There should be three swarm managers running, and services running on the manager nodes will be moved to the three new hosts.

2. Use the arrowcluster add-host command to provision the three new hosts.

3. Use ssh to connect to one of the manager nodes. Then use docker node ls -f role=manager to find all the swarm managers.

4. Execute docker node update <node-id> --availability=drain for each manager node.

5. Wait about two minutes and execute arrowcluster verify postinstall command to verify all services are working well.


Note: Users should use ArrowCluster 1.6.1.

## Requirements

For this release, existing clusters are required to upgrade Docker to version 17.06 and install NTP.

## New features and improvements

* Introduced **has\_internet\_access** (boolean (true/false)) in the user\_input.json file

  * There are situations when MBS cannot accurately determine if a target cluster in an on-premise environment has Internet access. To remedy this issue, you can set has\_internet\_access to true if the cluster has full Internet access so that the installer can retrieve and install required software such as Docker. Otherwise, the cluster should be pre-installed with the following required software:

    * nfs-utils

    * docker 17.06

    * nc (for port check)

    * lsof (for port check)

* Introduced **swarm\_manager\_hosts** in the user\_input.json file

  * For production deployment, we recommend at least three dedicated swarm manager hosts to ensure the high availability of the cluster. The number of swarm managers should be an odd number equal to or less than three.

  * Note: if you don't set swarm\_manager\_hosts or it contains less than three hosts, you will receive a warning message to the effect of this:

    `WARN[``2017``-``07``-``14`  `14``:``39``:``22``] You did not specify dedicated swarm manager hosts. For production environment, there should be at least` `3` `dedicated swarm managers. You should maintain an odd number of managers in the swarm to support manager node failures.`

    `Enter` `'y'``/``'yes'` `to` `continue` `OR` `'n'``/``'no'` `to exit, then hit enter:`

    `If your cluster is non production, enter yes to` `continue``.`

  * Usage: swarm\_manager\_hosts:\["ip1", "ip2",...\]


## Bug fix

* Fixed a bug that prevented scaled up apps from accepting more requests
