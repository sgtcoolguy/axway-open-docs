{"title":"Nodes - Model Update","weight":"120"}

API Builder 3.x is deprecated

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.

This document describes the model update and provides instance configuration and parameters information.

Name

Description

ModelUpdate

A Model specific flow-node. Invokes the Update API on a specified model and returns the response.

## Instance configuration

Property

Description

Required

Type

model

The name of the model of which to invoke the Update API.

yes

string

## Instance parameters

Property

Description

Type

Required

id

The ID of the record to update.

string

true

### Example

`"model.update"``: {`

`"type"``:` `"ModelUpdate"``,`

`"config"``: {`

`"model"``:` `"appc.arrowdb/acl"`

`},`

`"parameters"``: [`

`{`

`"name"``:` `"id"``,`

`"value"``:` `"$.params.id"`

`},`

`{`

`"name"``:` `"name"``,`

`"value"``:` `"$.params[\"appc.arrowdb/acl\"].name"`

`},`

`{`

`"name"``:` `"readers"``,`

`"value"``:` `"$.params[\"appc.arrowdb/acl\"].readers"`

`},`

`{`

`"name"``:` `"writers"``,`

`"value"``:` `"$.params[\"appc.arrowdb/acl\"].writers"`

`},`

`{`

`"name"``:` `"public_read"``,`

`"value"``:` `"$.params[\"appc.arrowdb/acl\"].public_read"`

`},`

`{`

`"name"``:` `"public_write"``,`

`"value"``:` `"$.params[\"appc.arrowdb/acl\"].public_write"`

`},`

`{`

`"name"``:` `"user"``,`

`"value"``:` `"$.params[\"appc.arrowdb/acl\"].user"`

`},`

`{`

`"name"``:` `"created_at"``,`

`"value"``:` `"$.params[\"appc.arrowdb/acl\"].created_at"`

`},`

`{`

`"name"``:` `"updated_at"``,`

`"value"``:` `"$.params[\"appc.arrowdb/acl\"].updated_at"`

`},`

`{`

`"name"``:` `"pretty_json"``,`

`"value"``:` `"$.params[\"appc.arrowdb/acl\"].pretty_json"`

`},`

`{`

`"name"``:` `"custom_fields"``,`

`"value"``:` `"$.params[\"appc.arrowdb/acl\"].custom_fields"`

`},`

`{`

`"name"``:` `"user_id"``,`

`"value"``:` `"$.params[\"appc.arrowdb/acl\"].user_id"`

`}`

`],`

`"response"``: {`

`"context"``: {},`

`"routes"``: [`

`{`

`"conditions"``: [`

`{`

`"key"``:` `"$"``,`

`"exists"``:` `false`

`}`

`],`

`"next"``:` `"response.error.notfound"`

`},`

`{`

`"next"``:` `"response.success"`

`}`

`]`

`}`

`}`
