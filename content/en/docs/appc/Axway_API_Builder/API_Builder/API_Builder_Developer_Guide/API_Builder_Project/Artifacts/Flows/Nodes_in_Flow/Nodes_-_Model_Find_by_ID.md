{"title":"Nodes - Model Find by ID","weight":"100"} 

# Nodes - Model Find by ID

API Builder 3.x is deprecated

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.

This document describes the model find by ID and provides instance configuration and parameters information.

Name

Description

ModelFindByID

A Model specific flow-node. Invokes the Find by ID API on a specified model and returns the response.

## Instance configuration

Property

Description

Required

Type

model

The name of the model of which to invoke the Find by ID API.

yes

string

## Instance parameters

Property

Description

Type

Required

id

The ID of the record to find.

string

true

### Example

`"model.findByID"``: {`

`"type"``:` `"ModelFindByID"``,`

`"config"``: {`

`"model"``:` `"appc.arrowdb/acl"`

`},`

`"parameters"``: [`

`{`

`"name"``:` `"id"``,`

`"value"``:` `"$.params.id"`

`}`

`],`

`"response"``: {`

`"context"``: {`

`"$"``:` `"model"`

`},`

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