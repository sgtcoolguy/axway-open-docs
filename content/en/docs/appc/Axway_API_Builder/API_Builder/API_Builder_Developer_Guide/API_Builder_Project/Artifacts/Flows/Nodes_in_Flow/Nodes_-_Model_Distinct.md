{"title":"Nodes - Model Distinct","weight":"70"} 

# Nodes - Model Distinct

API Builder 3.x is deprecated

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.

This document describes the model distinct flow-node and provides instance configuration and parameters information.

Name

Description

ModelDistinct

A Model specific flow-node. Invokes the Distinct API on a specified model and returns the response.

## Instance configuration

Property

Description

Required

Type

model

The name of the model of which to invoke the Distinct API.

yes

string

## Instance parameters

Property

Description

Required

Type

field

The field name that must be distinct.

yes

number

### Example

`"model.distinct"``: {`

`"type"``:` `"ModelDistinct"``,`

`"config"``: {`

`"model"``:` `"appc.arrowdb/acl"`

`},`

`"parameters"``: [`

`{`

`"name"``:` `"field"``,`

`"value"``:` `"$.params.field"`

`},`

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

`"conditions"``: [`

`{`

`"key"``:` `"$.error"``,`

`"exists"``:` `true`

`}`

`],`

`"next"``:` `"response.error"`

`},`

`{`

`"next"``:` `"response.success"`

`}`

`]`

`}`

`}`