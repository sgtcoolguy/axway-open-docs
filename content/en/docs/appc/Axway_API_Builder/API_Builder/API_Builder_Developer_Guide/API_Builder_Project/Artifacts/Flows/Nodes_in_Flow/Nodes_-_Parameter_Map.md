{"title":"Nodes - Parameter Map","weight":"10"} 

API Builder 3.x is deprecated

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.

This document describes a parametermap flow-node and provides a parametermap flow-node example.

Name

Description

parametermap

Non-functional flow-node which returns all parameters passed in as a response. Allows setting arbitrary values directly into the flow context.

## Example

This is an example of the parametermap flow-node. It takes model.id as the parameter data, and the static value 201 as the parameter status. These are then echoed back. data is set in the context as locaton and status is set as status.

`"response.success"``: {`

`"type"``:` `"parametermap"``,`

`"config"``: {},`

`"parameters"``: [`

`{`

`"name"``:` `"data"``,`

`"value"``:` `"$.model.id"`

`},`

`{`

`"name"``:` `"status"``,`

`"default"``: 201`

`}`

`],`

`"response"``: {`

`"context"``: {`

`"$.data"``:` `"location"``,`

`"$.status"``:` `"status"`

`},`

`"routes"``: [`

`{`

`"next"``:` `null`

`}`

`]`

`}`

`}`