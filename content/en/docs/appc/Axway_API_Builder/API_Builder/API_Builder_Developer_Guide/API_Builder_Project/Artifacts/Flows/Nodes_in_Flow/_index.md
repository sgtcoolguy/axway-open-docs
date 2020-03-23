{"title":"Nodes in Flow","weight":"20"}

{{% alert title="❗️ Warning" color="danger" %}}*API Builder 3.x is deprecated*

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.{{% /alert %}}

Flow-nodes represent an individual portion of functionality in a flow. Flow-nodes are available for flows which are built to perform certain actions. These can be configured individually and pass parameters from the flow context as part of the flow definition.

Flow-node configuration is handled on server initialization, whereas parameter handling happens at flow execution time.

As of API Builder Tools 2.0, the following flow-nodes are available for use:

* [Codeblock](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Project/Artifacts/Flows/Nodes_in_Flow/Nodes_-_Codeblock/)

* [Model Count](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Project/Artifacts/Flows/Nodes_in_Flow/Nodes_-_Model_Count/)

* [Model Create](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Project/Artifacts/Flows/Nodes_in_Flow/Nodes_-_Model_Create/)

* [Model Delete](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Project/Artifacts/Flows/Nodes_in_Flow/Nodes_-_Model_Delete/)

* [Model Delete All](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Project/Artifacts/Flows/Nodes_in_Flow/Nodes_-_Model_Delete_All/)

* [Model Distinct](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Project/Artifacts/Flows/Nodes_in_Flow/Nodes_-_Model_Distinct/)

* [Model Find All](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Project/Artifacts/Flows/Nodes_in_Flow/Nodes_-_Model_Find_All/)

* [Model Find and Modify](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Project/Artifacts/Flows/Nodes_in_Flow/Nodes_-_Model_Find_and_Modify/)

* [Model Find by ID](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Project/Artifacts/Flows/Nodes_in_Flow/Nodes_-_Model_Find_by_ID/)

* [Model Query](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Project/Artifacts/Flows/Nodes_in_Flow/Nodes_-_Model_Query/)

* [Model Update](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Project/Artifacts/Flows/Nodes_in_Flow/Nodes_-_Model_Update/)

* [Model Upsert](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Project/Artifacts/Flows/Nodes_in_Flow/Nodes_-_Model_Upsert/)

* [Parameter Map](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Project/Artifacts/Flows/Nodes_in_Flow/Nodes_-_Parameter_Map/)

Beginning with API Builder Tools 3.0, flow-nodes can be configured by selecting a method and the defining the parameters and outputs in the API Orchestration flow editor. The default Model flow-node methods are: count, create, delete, deleteAll, distinct, findAll, findAndModify, findByID, query, update, and upsert. The default Core flow-node types are: Custom, Codeblock, Compose, Condition, Delay, HTTP, JSON, and Set Context. For additional information, see [API Builder Flows](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/).
