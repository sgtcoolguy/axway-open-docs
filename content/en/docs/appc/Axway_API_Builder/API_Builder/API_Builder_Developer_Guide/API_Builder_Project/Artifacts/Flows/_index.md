{"title":"Flows","weight":"20"} 

API Builder 3.x is deprecated

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.

## Flows

Flows are acyclic directed graphs of operational flow-nodes which are composed of inputs, logic, and outputs. They are used by Endpoints, which require them for their runtime functionality of taking inputs and turning them into responses when an Endpoint is hit. Flows are written as .json files and located within the /flows directory of your app. Flows have a runtime context which can be written to and read from by individual flow-nodes. This is how data is passed around in the flow. When running a flow via an endpoint, the data passed to the endpoint will propagate to the flow.

Beginning with API Builder Tools 3.0, flows can be created and configured using the API Orchestration flow editor. For additional information, see [API Builder Flows](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/).

## Flow context

The **Flow context** is where data is temporarily stored at runtime while a Flow is being executed. This allows flow-nodes to share information, by reading data from the context before execution using their parameters and writing data to the context after execution using [JSONPath](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Project/Artifacts/Flows/JSONPath/) selectors. If a flow is used by an endpoint which has certain parameters defined, these will also be accessible to flow-nodes from the flow context.

## Flow input

If a flow is executed from an endpoint, any parameters defined by the endpoint and correctly passed to the endpoint upon execution will be accessible from the flow context from the JSONPath selector: $.params

For example, a header parameter called enabled would be accessible from $.params.enabled. If a request is made with a parameter which is not defined in the endpoint’s swagger, it will not be accessible from the flow.