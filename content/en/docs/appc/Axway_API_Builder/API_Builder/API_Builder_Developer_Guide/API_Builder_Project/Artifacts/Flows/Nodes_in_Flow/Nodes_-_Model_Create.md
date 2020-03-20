{"title":"Nodes - Model Create","weight":"40"}

*API Builder 3.x is deprecated*

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.

This document describes model create and provides instance configuration and parameters information.

| Name | Description |
| --- | --- |
| ModelCreate | A Model specific flow-node. Invokes the Create API on a specified model and returns the response. |

## Instance configuration

| Property | Description | Required | Type |
| --- | --- | --- | --- |
| model | The name of the model of which to invoke the Create API. | yes | string |

## Instance parameters

These are all specified by the chosen model.

### Example

```
"model.create": {
 "type": "ModelCreate",
 "config": {
   "model": "appc.arrowdb/acl"
 },
 "parameters": [
   {
     "name": "name",
     "value": "$.params[\"appc.arrowdb/acl\"].name"
   },
   {
     "name": "readers",
     "value": "$.params[\"appc.arrowdb/acl\"].readers"
   },
   {
     "name": "writers",
     "value": "$.params[\"appc.arrowdb/acl\"].writers"
   },
   {
     "name": "public_read",
     "value": "$.params[\"appc.arrowdb/acl\"].public_read"
   },
   {
     "name": "public_write",
     "value": "$.params[\"appc.arrowdb/acl\"].public_write"
   },
   {
     "name": "user",
     "value": "$.params[\"appc.arrowdb/acl\"].user"
   },
   {
     "name": "created_at",
     "value": "$.params[\"appc.arrowdb/acl\"].created_at"
   },
   {
     "name": "updated_at",
     "value": "$.params[\"appc.arrowdb/acl\"].updated_at"
   },
   {
     "name": "pretty_json",
     "value": "$.params[\"appc.arrowdb/acl\"].pretty_json"
   },
   {
     "name": "custom_fields",
     "value": "$.params[\"appc.arrowdb/acl\"].custom_fields"
   },
   {
     "name": "user_id",
     "value": "$.params[\"appc.arrowdb/acl\"].user_id"
   }
 ],
 "response": {
   "context": {
     "$": "model"
   },
   "routes": [
     {
       "next": "response.success"
     }
   ]
 }
}
```
