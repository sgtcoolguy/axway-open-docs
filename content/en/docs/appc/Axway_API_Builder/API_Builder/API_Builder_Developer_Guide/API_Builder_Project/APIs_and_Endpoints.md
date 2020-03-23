{"title":"APIs and Endpoints","weight":"20"}

{{% alert title="❗️ Warning" color="danger" %}}*API Builder 3.x is deprecated*

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.{{% /alert %}}

## APIs

APIs are defined as Swagger documents which can contain one or more Endpoint definitions. The API swagger document must be formatted as JSON and contained within the /endpoints directory of your app.

When API Builder reads these API swagger definitions, it will create the specified routes for each Endpoint. The implementation of the business logic for each Endpoint is handled by the Flow associated with that Endpoint. This is delegated to Flows which are specified on a per-Endpoint level.

APIs have the following extensions to the swagger specification:

| Property | Description | Required | Type | Default | Example |
| --- | --- | --- | --- | --- | --- |
| x-enabled | If the API should be bound to the app on load. | No | object | { "enabled": true } | { "enabled": false } |
| x-flow | The name of the Flow to be executed when the endpoint is hit. | Yes | string |  | "greetflow" |

## Example

This example API below is similar to the one that comes with every API Builder Project. It contains an Endpoint which takes a username, invokes the flow called “greetflow”, and returns a greeting. However, since it has an x-enabled flag set, the Endpoint will be disabled, and no requests will be able to be made to it.

```
{
  "swagger": "2.0",
  "info": {
    "description": "Greeting functions",
     "version": "1.0.0",
     "title": "Greeting API"
  },
  "x-enabled": {
    "enabled": false
  },
  "paths": {
    "/greet": {
      "get": {
        "x-flow": "greetflow",
        "consumes": [
          "application/json"
         ],
         "description": "",
         "operationId": "Greet",
         "parameters": [
           {
             "description": "The username",
             "in": "query",
             "name": "username",
             "required": true,
             "type": "string"
           }
         ],
         "produces": [
           "application/json"
         ],
         "responses": {
           "200": {
             "description": "greeting",
             "schema": {
               "type": "string"
             }
           },
           "400": {
             "description": "bad request",
             "schema": {
               "type": "string"
             }
           }
         },
         "summary": "Greet a user",
         "tags": [
           "helloworld"
         ]
       }
     }
   }
}
```
