{"title":"API Builder Flows","weight":"70"}

*API Builder 3.x is deprecated*

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.

## Introduction

Beginning with API Builder V3.0.0 (Included in CLI 7.0.0), you can manage endpoints and their associated flows using the API Builder Console. You can also create and edit flows and configure their associated flow-nodes using the API Orchestration user interface.

## Manage endpoints

An API endpoint provides a way for a client to access your application, such as GET <SERVER\_ADDRESS>/api/users/query and access the application's models and/or custom code blocks to return data back to the client application. You can use the API Builder Console to import, generate, export, and delete endpoints. For additional information, refer to [Manage Endpoints](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Endpoints/).

## Flow orchestration

Flows can be viewed and edited on the API Orchestration user interface. Additionally, you can manage flow-node configuration and connections on the API Orchestration user interface. For additional information on the API Orchestration user interface and for flow-node configuration reference information, refer to [Flow Orchestration](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Flow_Orchestration/).

## Manage flows

Flows are acyclic directed graphs of operational flow-nodes which are composed of inputs, logic, and outputs. They are used by endpoints, which require them for their runtime functionality of taking inputs and turning them into responses when an endpoint is hit. You can **use** the API Builder Console and the associated API Orchestration user interface to view, create and edit flows. For additional information, refer to [Manage Flows](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Flows/).

## Manage nodes

Flow-nodes represent an individual portion of functionality in a flow. You can use the API Orchestration user interface to add, configure, and delete flow-nodes. You can also connect and disconnect flow-nodes in a flow. For additional information, refer to [Manage Nodes](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Nodes/).

## Axway Flow SDK

The Axway Flow SDK (axway-flow-sdk) is a standalone utility that enables the creation of custom flow-nodes for API Builder flows. For additional information, refer to [Axway Flow SDK](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Axway_Flow_SDK/).
