{"title":"Manage Endpoints","weight":"10"}

API Builder 3.x is deprecated

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.

* [Import endpoints](#import-endpoints)

* [Generate endpoints](#generate-endpoints)

* [Export endpoints](#export-endpoints)

* [Delete endpoints](#delete-endpoints)

An API endpoint provides a way for a client to access your application, such as GET <SERVER\_ADDRESS>/api/users/query and access the application's models and/or custom code blocks to return data back to the client application. To create API endpoints, see the Arrow.API API reference or follow the Generate endpoints instructions. For reference information on flow orchestration, refer to [Flow Orchestration](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Flow_Orchestration/).

## Import endpoints

A Swagger API endpoint definition file (swagger.json) can only be imported once. If you attempt to import a Swagger file for the same API endpoint definition, you will receive a server error message.

To import API endpoints using the API Builder GUI:

1. Select the **API Doc & Test** tab.

2. Click the **\+ API** button on the right side. The Import API Definition page is displayed.

    ![import_API](/Images/appc/download/attachments/51252022/import_API.png)
3. Select a file from your local filesystem or enter a URL. A file can be selected by browsing or dragging and dropping it. The selected file must be a Swagger formatted JSON file. To export an API endpoint as a swagger.json file, refer to the [Export endpoints](#Export) section. Once a file is selected or a URL entered, the API summary review page is displayed.

    ![API_sum_review](/Images/appc/download/attachments/51252022/API_sum_review.png)
4. Click the **Save** button on the right to import and save the selected API endpoint. Click the **Save and mock** button to save and mock the selected API endpoint. You can mock imported APIs to get early feedback from your API consumers and reduce your overall time-to-market. Click the **Cancel** button to cancel the import of the selected API endpoint. When the **Save** button or the **Save and mock** button is clicked, the server will restart. Once the server restart is completed, the imported API endpoints will be displayed on the APIs List page. The imported API endpoints will be disabled and each will have a **Create Flow** and **Delete** icons. To create the API endpoint flows, refer to the Create flows instructions in [Manage Flows](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Flows/).

## Generate endpoints

API Builder may auto-generate APIs for certain models. These APIs are hard-coded and cannot be used with flows or the orchestration flow editor.

To generate endpoints that have flows that can be edited within the flow editor using the API Builder GUI:

1. Select the **Models** tab.

2. Click the **Tool** icon.

3. Select **Generate endpoints**. The Endpoint generate caution window is displayed.

    ![endpoint_gen_caution](/Images/appc/download/attachments/51252022/endpoint_gen_caution.png)
4. Select **Proceed** to generate the model endpoint flows. Select **Cancel endpoint generation** to return to the Models tab.

5. If Proceed is selected, the new endpoints will be generated and the server will be restarted. Once the endpoints are generated, the Endpoint generate success window is displayed

    ![endpoint_gen_success](/Images/appc/download/attachments/51252022/endpoint_gen_success.png)
6. To view and manage the Endpoints, select **Go to API details**. The method, path, nickname, description, and status (enabled, disabled, or error) of each generated endpoint is provided on the APIs List page. Additionally, **Flow** and Delete icons are provided for each Endpoint.

## Export endpoints

To export an API endpoint as a Swagger formatted JSON file using the API Builder GUI:

1. Select the **API Doc & Test** tab.

2. Select the API endpoint to export from the API Endpoints list. Selecting the API endpoint to export will open the APIs List page.

3. Click the **Download Swagger** button to download the selected API endpoint as a Swagger formatted JSON file.

4. Select the file download location on your filesystem.

5. Confirm the file download.

## Delete endpoints

To delete endpoints using the API Builder GUI:

1. Select the **API Doc & Test** tab.

2. Select the API endpoint to manage from the API Endpoints list. Selecting the API endpoint to manage will open the APIs List page.

3. Select the **Delete** icon for the endpoint to delete. The Endpoint delete caution window is displayed.

    ![endpoint_del_caution](/Images/appc/download/attachments/51252022/endpoint_del_caution.png)
4. Select **Proceed** to the delete the selected endpoint. Select **Cancel** to return to the _API List_ page. If **Proceed** is selected, the endpoint and any associated flow are deleted and the server is restarted. Once the server restart is completed, the APIs List page is displayed.
