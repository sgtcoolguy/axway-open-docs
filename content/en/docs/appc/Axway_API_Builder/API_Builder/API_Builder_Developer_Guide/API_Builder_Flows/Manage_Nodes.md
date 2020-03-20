{"title":"Manage Nodes","weight":"40"}

*API Builder 3.x is deprecated*

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.

* [Add flow-nodes](#add-flow-nodes)

* [Configure flow-nodes](#configure-flow-nodes)

    * [Selector and output auto-complete](#selector-and-output-auto-complete)

* [Connect flow-nodes](#connect-flow-nodes)

* [Delete flow-node connectors](#delete-flow-node-connectors)

* [Delete flow-nodes](#delete-flow-nodes)

This topic describes how to manage the API endpoint flow-nodes and the connections between flow-nodes on the API Orchestration user interface. The API Orchestration user interface is divided into the following panels:

* Flow-node list (left side of the API Orchestration user interface) - Provides a graphical listing of the Model and Core flow-nodes. The default Core flow-node types are Custom, Codeblock, Compose, Condition, Delay, HTTP, JSON, and Set Context. A model flow-node is displayed for each configured model and an endpoint flow-node is displayed for each imported endpoint.

* Flow editor (center of the API Orchestration user interface) - Provides a graphical space to view, edit, and create flows.

* Flow-node configuration (right side of the API Orchestration user interface) - Provides the functionality to configure the Name, Method, Parameters, and Outputs of flow-nodes.

API Orchestration user interface example:

![api_orchestration](/Images/appc/download/attachments/51252726/api_orchestration.png)

The procedures in this topic appear in the most probable configuration order. To manage API endpoints, refer to [Manage Endpoints](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Endpoints/). To manage API endpoint flows, refer to [Manage Flows](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Flows/).

## Add flow-nodes

To add flow-nodes to a flow:

1. Select the flow-node to add to the flow from the listed flow-nodes from the panel on the left.

2. Drag the selected flow-node into the flow editor panel in the center of the API Orchestration user interface. The flow-node will automatically align with any additional flow-nodes in the flow. A warning message may be displayed and the flow-node may be highlighted until it is configured.

## Configure flow-nodes

To configure flow-nodes in a flow:

1. Select a flow-node on the flow editor panel to configure its properties.

2. If necessary, select and change the default flow-node name. Flow-node naming should reflect the function of the flow-node.

3. Select a **Method** from the Method drop-down menu. For additional information on the Model and General flow-node Method selections, refer to [Flow Orchestration](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Flow_Orchestration/).

4. Select **Parameters** and complete or edit the parameter configuration entries. If **selector** is selected from the _selector_ drop-down menu, as you begin typing in the **parameter** field, a drop-down menu of valid or previously used selector options is displayed. You may optionally choose a selector from the list, or continue typing to manually configure the parameter. For additional selector auto-complete information, refer to [Selector and output auto-complete](#Selectorautocomplete). Note that the parameter entries are dependent on the selected flow-node method. For additional information on the Model flow-node and General flow-node configuration parameters, refer to [Flow Orchestration](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Flow_Orchestration/).

5. Select **Outputs** and complete or edit the output configuration entries. As you begin typing in the **output** field, a drop-down menu of valid or previously used output options is displayed. You may optionally choose an output from the list, or continue typing to manually configure the parameter. For additional information on the Model and General flow-node output configuration for each method, refer to [Flow Orchestration](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Flow_Orchestration/). Once the flow-node is properly configured, the warning message is longer displayed and the flow-node is longer highlighted.

### Selector and output auto-complete

When you edit a selector or an output parameter. any previously used or valid selectors or outputs are displayed in a context-assisted drop-down menu that shows the selectors or outputs that match the input text. You may optionally choose a selector or output from the list, or continue typing to manually configure the parameter.

## Connect flow-nodes

All API endpoint flows begin with a default Start flow-node.

Start flow-nodes can only be connected to one other flow-node in the flow. To connect the output of the Start flow-node to the input of another flow-node:

1. Click on the Start flow-node.

2. While leaving the Start flow-node selected, move your pointer off the Start flow-node. The output connection on Start flow-node and the input connections on the additional flow-nodes in the flow will be displayed. The connector from the Start flow-node will follow the movement of the cross-hair of your pointer.

3. Pull the connector towards the next flow-node to include in the flow. The connector will snap to the input of the next flow-node to include in the flow when you hover over it.

4. To finish the connection, drop the connector on the input of the next flow-node in the flow. The flow is automatically rearranged according to the existing connectors and flow-nodes.

To connect the output or outputs of a flow-node to the input of another flow-node:

1. Click on the output of a flow-node to connect to the input of another flow-node.

2. While leaving the output of flow-node selected, move your pointer off the output of the flow-node. The output connection and the input connections on the additional flow-nodes in the flow that can be connected with will be displayed. The connector from the output of the flow-node will follow the movement of the cross-hair of your pointer.

3. Pull the connector towards the next flow-node to include in the flow. The connector will snap to the input of the next flow-node to include in the flow when you hover over it.

4. To finish the connection, drop the connector on the input of the next flow-node in the flow. The flow is automatically rearranged according to the existing connectors and flow-nodes.

## Delete flow-node connectors

To delete a flow-node connector:

1. Select the flow-node connector to delete.

2. Click the keyboard **Del** key or **Backspace** key. The selected connector is deleted and the flow is automatically rearranged according to the existing connectors and flow-nodes.

## Delete flow-nodes

To delete flow-nodes in a flow:

1. Select the flow-node to delete.

2. Click the keyboard **Del** key or **Backspace** key. The flow-node delete caution screen is displayed.

    ![delete_caution](/Images/appc/download/attachments/51252726/delete_caution.png)
3. Click **Proceed** to complete the deletion of the selected flow-node and return to the flow. Select **Cancel** to cancel the deletion of the selected flow-node and return to the flow.
