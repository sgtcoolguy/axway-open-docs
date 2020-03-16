{"title":"API Builder","weight":"10"}

API Builder 3.x is deprecated

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.

* [Overview](#overview)

    * [Connectors](#connectors)

    * [Models](#models)

    * [APIs](#apis)

    * [Blocks](#blocks)

    * [Webs](#webs)

    * [Flows](#flows)

* [Topics](#topics)

With the release of version 1.10.0, **Arrow Builder** will now be known as **API Builder**. The following pages reference many concepts and original features from Arrow Builder but there also several new features and workflows that are uniquely part of API Builder.

## Overview

API Builder lets you build and deploy a project that is comprised of API endpoints that can be consumed by any client application. An API Builder project is a Node.js application that runs in the AMPLIFY Runtime Services and is comprised of several components. You can either define the components using JavaScript files placed in specific directories, which are automatically loaded when creating an API Builder instance or programmatically create components after initializing an API Builder instance. For information about the components, see the diagram and sections below.

To get started, see the [API Builder Getting Started Guide](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Getting_Started_Guide/).

![API_Builder_Application](/Images/appc/download/attachments/49153253/API_Builder_Application.png)

### Connectors

**[API Builder Connectors](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Connectors/)** are adaptors that allow you to read and write data to and from an external data source, such as [Mobile Backend Services](/docs/appc/Mobile_Backend_Services/) , MySQL, Salesforce, and MongoDB, or in server memory. You can either add an existing connector to your application or create one to interface with your custom data source.

### Models

**[Models](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Project/Artifacts/Models/)** provide a standardized interface for an application which allows client applications to access data. Models are either provided by a connector, reduced from an [existing model](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Project/Artifacts/Models/), or composed of several models ([composite models](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Project/Artifacts/Models/)) using a left or an inner join operation.

### APIs

**[API Builder APIs](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_APIs/)** are custom endpoints that allow you to programmatically access and execute custom operations on model data. You can create an API if you want to execute an operation not exposed by the standardized interface.

### Blocks

**[API Builder Blocks](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_How-tos/API_Builder_Blocks/)** are filters that allow you to pre- or post-process data. Blocks are optional and can be used by either APIs or Models.

### Webs

**[API Builder Web](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Web/)** is a framework to create endpoints that render HTML for client applications. An API Builder Web is composed of a router (API endpoint), renderer engine (generates HTML by applying data to a view), view (template file) and static assets, such as JavaScript files, images, CSS, and so forth.

### Flows

**[API Builder Flows](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/)** are acyclic directed graphs of operational flow-nodes which are composed of inputs, logic, and outputs. They are used by endpoints, which require them for their runtime functionality of taking inputs and turning them into responses when an endpoint is hit.

## Topics

* [API Builder Getting Started Guide](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Getting_Started_Guide/)

* [API Builder Developer Guide](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/)

* [API Builder How-tos](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_How-tos/)

* [API Builder Release Notes](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Release_Notes/)

* [API Builder FAQ](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_FAQ/)
