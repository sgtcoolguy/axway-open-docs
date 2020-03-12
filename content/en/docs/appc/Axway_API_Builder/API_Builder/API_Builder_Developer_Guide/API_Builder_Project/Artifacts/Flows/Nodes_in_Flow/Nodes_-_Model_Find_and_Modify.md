{"title":"Nodes - Model Find and Modify","weight":"90"} 

# Nodes - Model Find and Modify

API Builder 3.x is deprecated

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.

This document describes the model find and modify flow-node and provides instance configuration and parameters information.

Name

Description

ModelFindAndModify

A Model specific flow-node. Invokes the Find and Modify API on a specified model and returns the response.

## Instance configuration

Property

Description

Required

Type

model

The name of the model of which to invoke the Find and Modify API.

yes

string

## Instance parameters

Property

Description

Type

Default

limit

The number of records to fetch. The value must be greater than 0, and no greater than 1000.

number

10

skip

The number of records to skip. The value must not be less than 0.

number

where

Constrains values for fields. The value should be encoded JSON.

string

order

A dictionary of one or more fields specifying sorting of results. In general, you can sort based on any predefined field that you can query using the where operator, as well as on custom fields. The value should be encoded JSON.

string

sel

Selects which fields to return from the query. Others are excluded. The value should be encoded JSON.

string

unsel

Selects which fields not return from the query. Others are included. The value should be encoded JSON.

string

page

Request page number starting from 1.

number

1

per\_page

The number of results per page.

number

10

### Example

`"model.findAndModify"``: {`

`"type"``:` `"ModelFindAndModify"``,`

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