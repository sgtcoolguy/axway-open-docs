{"title":"Nodes - Model Find All","weight":"80"} 

API Builder 3.x is deprecated

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.

This document describes the model find all and provides instance configuration and parameters information.

Name

Description

ModelFindAll

A Model specific flow-node. Invokes the Find All API on a specified model and returns the response.

## Instance configuration

Property

Description

Required

Type

model

The name of the model of which to invoke the Find All API.

yes

number

## Instance parameters

These are all specified by the chosen model.

### Example

`"model.findAll"``: {`

`"type"``:` `"ModelFindAll"``,`

`"config"``: {`

`"model"``:` `"appc.arrowdb/acl"`

`},`

`"parameters"``: [],`

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