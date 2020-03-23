{"title":"Nodes - Model Delete","weight":"50"}

{{% alert title="❗️ Warning" color="danger" %}}*API Builder 3.x is deprecated*

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.{{% /alert %}}

This document describes model delete and provides instance configuration and parameters information.

| Name | Description |
| --- | --- |
| ModelDelete | A Model specific flow-node. Invokes the Delete API on a specified model and returns the response. |

## Instance configuration

| Property | Description | Required | Type |
| --- | --- | --- | --- |
| model | The name of the model of which to invoke the Delete API. | yes | string |

## Instance parameters

These are all specified by the chosen model.

### Example

```
"model.delete": {
 "type": "ModelDelete",
 "config": {
   "model": "appc.arrowdb/acl"
 },
 "parameters": [
   {
     "name": "id",
     "value": "$.params.id"
   }
 ],
 "response": {
   "context": {
     "$": "model"
   },
   "routes": [
     {
       "conditions": [
         {
           "key": "$._deleted",
           "eq": true
         }
       ],
       "next": "response.success"
     },
     {
       "next": "response.error.notfound"
     }
   ]
 }
}
```
