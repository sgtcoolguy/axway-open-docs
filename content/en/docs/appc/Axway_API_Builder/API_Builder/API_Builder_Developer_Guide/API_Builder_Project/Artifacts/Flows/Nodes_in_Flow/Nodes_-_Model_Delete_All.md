{"title":"Nodes - Model Delete All","weight":"60"}

*API Builder 3.x is deprecated*

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.

This document describes model delete all and provides instance configuration and parameters information.

| Name | Description |
| --- | --- |
| ModelDeleteAll | A Model specific flow-node. Invokes the Delete All API on a specified model and returns the response. |

## Instance configuration

| Property | Description | Required | Type |
| --- | --- | --- | --- |
| model | The name of the model of which to invoke the Delete All API. | yes | string |

## Instance parameters

These are all specified by the chosen model.

### Example

```
"model.deleteall": {
 "type": "ModelDeleteAll",
 "config": {
   "model": "appc.arrowdb/acl"
 },
 "parameters": [],
 "response": {
   "context": {},
   "routes": [
     {
       "next": "response.success"
     }
   ]
 }
}
```
