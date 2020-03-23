{"title":"Manage Flows","weight":"30"}

{{% alert title="❗️ Warning" color="danger" %}}*API Builder 3.x is deprecated*

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.{{% /alert %}}

* [Add API endpoints](#add-api-endpoints)

* [View flows](#view-flows)

* [Create flows](#create-flows)

* [Edit flows](#edit-flows)

* [Delete flows](#delete-flows)

Flows are acyclic directed graphs of operational flow-nodes which are composed of inputs, logic, and outputs. They are used by endpoints, which require them for their runtime functionality of taking inputs and turning them into responses when an endpoint is hit. For reference information on flow orchestration, refer to [Flow Orchestration](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Flow_Orchestration/).

## Add API endpoints

To import and add API endpoints and flows, refer to [Manage Endpoints](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Endpoints/).

## View flows

To view a flow using the API Builder GUI:

1. Select the **API Doc & Test** tab.

2. Select an API Endpoint to view the API List of endpoints. The API Lists page is displayed. Endpoints that are flow-based have a **Flow** icon displayed. Endpoints that are programmatically-based do not have a **Flow** icon display. Additionally, the method, path, nickname, description, and status of each endpoint is provided on the APIs List page.

3. Select the **Flow** icon for the endpoint flow you want to view. The selected flow is displayed in the flow editor panel on the API Orchestration user interface.

4. To exit the API Orchestration user interface and return to the API Lists page, select **Cancel**.

## Create flows

To create a flow using the API Builder GUI:

1. Import an API endpoint per the **Add endpoints** instructions in [Manage Endpoints](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Endpoints/). Once the API endpoints are imported and the server is restarted, the imported API endpoints are displayed on the APIs List page. The imported API endpoints are disabled and each endpoint has **Create Flow** and **Delete** icons. Additionally, the method, path, nickname, description, and status of each imported endpoint is provided on the APIs List page.

2. Click the **Create Flow** icon for an endpoint. The API Orchestration user interface is displayed and a Start flow-node is presented in the flow editor panel.

3. Add flow-nodes to the flow. Refer to the **Add flow-node** instructions in [Manage Nodes](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Nodes/).

4. Configure the flow-nodes added to the flow. Refer to the **Configure flow-node** instructions in [Manage Nodes](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Nodes/).

5. Connect the flow-nodes in the flow. Refer to the **Connect flow-nodes** instructions in [Manage Flows](#undefined).

6. When the flow is complete, click the **Save** button. The Flow save caution window is displayed.

    {{% alert title="⚠️ Warning" color="primary" %}}Only valid flows can be saved.{{% /alert %}}

    ![save_caution](/Images/appc/download/attachments/51252040/save_caution.png)

7. Select **Proceed** to save the flow. Select **Cancel** to return to the API Orchestration user interface. If **Proceed** is selected, the server is restarted and the flow is saved. Once the server restart is completed, the APIs List page is displayed and the flow is enabled. For flow creation examples, refer to [Flow Examples](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Flows/Flow_Examples/).

## Edit flows

To edit a flow using the API Builder GUI:

1. Select the **API Doc & Test** tab.

2. Select an API Endpoint to view the API List of endpoints. The API Lists page is displayed.

3. Select the **Flow** icon for the API endpoint flow to edit. The selected flow is displayed in the flow editor panel on the API Orchestration user interface.

4. Make the required edits to the flow. For instructions on adding, configuring, and connecting flow-nodes or disconnecting and deleting flow-nodes, refer to [Manage Nodes](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Nodes/).

5. Once the flow edits are completed, click the **Save** button. The Flow save caution window is displayed.

    ![save_caution](/Images/appc/download/attachments/51252040/save_caution.png)
6. Select **Proceed** to save the flow. Select **Cancel** to return to the API Orchestration user interface. If **Proceed** is selected, the server is restarted and the flow is saved. Once the server restart is completed, the APIs List page is displayed.

## Delete flows

To delete a flow using the API Builder GUI:

1. Select the **API Doc & Test** tab.

2. Select an API Endpoint to view the API List of endpoints. The API Lists page is displayed.

3. Select the **Delete** icon for the API endpoint to delete. The Endpoint delete caution window is displayed.

    ![endpoint_del_caution](/Images/appc/download/attachments/51252040/endpoint_del_caution.png)
4. Select **Proceed** to the delete the selected API endpoint. Select Cancel to return to the APIs List page. If **Proceed** is selected, the endpoint and any associated flow are deleted and the server is restarted. Once the server restart is completed, the APIs List page is displayed.
