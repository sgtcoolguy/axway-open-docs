{"title":"Nodes - Model Query","weight":"110"} 

API Builder 3.x is deprecated

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.

This document describes the model query and provides instance configuration and parameters information.

Name

Description

ModelQuery

A Model specific flow-node. Invokes the Query API on a specified model and returns the response.

## Instance configuration

Property

Description

Required

Type

model

The name of the model of which to invoke the Query API.

yes

string

## Instance parameters

These are all specified by the chosen model.

### Example

`"model.query"``: {`

`"type"``:` `"ModelQuery"``,`

`"config"``: {`

`"model"``:` `"appc.arrowdb/acl"`

`},`

`"parameters"``: [`

`{`

`"name"``:` `"limit"``,`

`"value"``:` `"$.params.limit"`

`},`

`{`

`"name"``:` `"skip"``,`

`"value"``:` `"$.params.skip"`

`},`

`{`

`"name"``:` `"where"``,`

`"value"``:` `"$.params.where"`

`},`

`{`

`"name"``:` `"order"``,`

`"value"``:` `"$.params.order"`

`},`

`{`

`"name"``:` `"sel"``,`

`"value"``:` `"$.params.sel"`

`},`

`{`

`"name"``:` `"unsel"``,`

`"value"``:` `"$.params.unsel"`

`},`

`{`

`"name"``:` `"page"``,`

`"value"``:` `"$.params.page"`

`},`

`{`

`"name"``:` `"per_page"``,`

`"value"``:` `"$.params.per_page"`

`}`

`],`

`"response"``: {`

`"context"``: {`

`"$"``:` `"models"`

`},`

`"routes"``: [`

`{`

`"next"``:` `"response.success"`

`}`

`]`

`}`

`}`