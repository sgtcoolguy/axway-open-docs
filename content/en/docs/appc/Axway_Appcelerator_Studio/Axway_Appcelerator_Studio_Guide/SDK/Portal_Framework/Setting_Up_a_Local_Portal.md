{"title":"Setting Up a Local Portal","weight":"50"}

* [Description](#description)

* [Importing the Portal sample from Github](#importing-the-portal-sample-from-github)

* [Pointing to the local Portal](#pointing-to-the-local-portal)

## Description

Follow the instructions on this page to import the portal samples from Github, and point the Studio to load the local portal.

## Importing the Portal sample from Github

Import the portal samples project from the [studio3-sdk](https://github.com/aptana/studio3-sdk) repository to your machine.

## Pointing to the local Portal

* open the TitaniumStudio.ini file (or AptanaStrudio.ini), which exists next to the Studio executable.

* edit the **\-vmargs** part by adding:

    ```
    -Dtitanium.dashboardUrl=file:///C:/studio3-sdk/portal/sample/dashboard.html
    ```

* re-launch Studio.

The loaded portal will now be the local one.
