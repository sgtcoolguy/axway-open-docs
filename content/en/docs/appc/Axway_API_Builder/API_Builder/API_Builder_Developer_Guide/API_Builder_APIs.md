{"title":"API Builder APIs","weight":"50"}

{{% alert title="❗️ API Builder 3.x is deprecated" color="danger" %}}Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.{{% /alert %}}

* [Introduction](#introduction)

* [API endpoint definition](#api-endpoint-definition)

* [API example](#api-example)

* [Invoke API endpoints in API Builder](#invoke-api-endpoints-in-api-builder)

## Introduction

This chapter covers the basics for creating API endpoints. API endpoints are automatically generated for all models, but there may be cases where you will want to create your own custom API.

An API provides a way for a client to access your application, such as GET <SERVER\_ADDRESS>/api/users/query, execute custom logic and internally access the application's models and APIs, then return data back to the client application.

To programmatically create an API, see the [API Builder.API](#!/api/Arrow.API) reference.

## API endpoint definition

Place all API definition files in the project's apis folder. You can only declare one endpoint definition per file. An API definition file is a JavaScript file, which:

1. Loads the arrow module.

2. Calls the module'sAPI.extend() method, passing in an object defining the API endpoint and logic.

3. Exports the defined endpoint using the module.exports variable.

Set the following keys in the object passed to the API.extend() method to define the API endpoint:

| Name | Required | Description |
| --- | --- | --- |
| group | true | The logical name for grouping API endpoints. |
| path | true | Request path (for example, /api/user/:id). Prefix parameters with a colon (:). |
| method | true | HTTP verb (GET, POST, PUT, or DELETE). |
| description | true | Description of the endpoint, which is used in the generation of the API endpoint documentation. |
| model | true | The model to use for the response. An API endpoint can only specify **one** model, but models can be composed of other models and fields. |
| action | true | The function that is called to execute the API endpoint’s logic. The function is passed a request object, response object, and next() method. Use this function to make programmatic calls to your model’s methods for reading or writing data and to do other things related to the custom business logic of your API endpoint including making calls to other flow-node modules that your API endpoint requires. You should always make sure that your action function calls the next function regardless if the result is a success or an error. |
| documented | false | **Since Release 5.0.0.** Determines whether to generate API documentation (true) or not (false). The default setting is true. |
| response | false | The response model for the API. This should only be used if your request and response models are different. |
| plural | false | A string used as the property name when your API endpoint returns an array. By default, the plural value is the plural of the model name. For example, if your model is named **car**, the default plural would be **cars**. |
| singular | false | A string used as the property name when your API endpoint returns a single record. By default, the singular value is the name of the model. |
| before | false | One or more API Builder Blocks to be executed before the request. Blocks are referenced by their name property. If you want to execute multiple blocks, you should specify them as an array of block names. If multiple blocks are specified, they are executed in the order specified. |
| after | false | One or more API Builder Blocks to be executed after the request. Blocks are referenced by their name property. If you want to execute multiple blocks, you should specify them as an array of block names. If multiple blocks are specified, they are executed in the order specified. |
| parameters | false | Input parameters required to execute the API endpoint. This is an object of key-value pairs, where the key is the name of the parameter and the value is an object with the following properties:<br /><br />* optional (Boolean): Determines if the parameter is optional (true) or required (false).<br />    <br />* type (String): the type of input parameter: path, query, or body.<br />    <br />* description (String): used for generating API documentation. |

## API example

The following API definition file creates an endpoint that can be accessed by a client using GET <HOST\_ADDRESS>/api/test/:id. Before the request is initiated by the server, the formatRequestBlock is executed, then the server performs the request (executes the action logic). The action logic tries to find the user model with the specified ID. After the logic executes, the cachingBlock and analyticsBlocks are executed.

**apis/test.js**

```javascript
var Arrow = require('arrow');

var TestAPI = Arrow.API.extend({
    group: 'test',
    path: '/api/test/:id',
    method: 'GET',
    description: 'this is an api that shows how to implement an API',
    model: 'user',
    before: 'formatRequestBlock',
    after: ['cachingBlock', 'analyticsBlock'],
    parameters: {
        // 'id' is required to execute this endpoint
        id: {description:'the user id'}
    },
    action: function (req, res, next) {
        // call the 'find' method on our model to get the data passing the incoming path value id
        res.stream(req.model.find, req.params.id, next);
    }
});

module.exports = TestAPI;
```

## Invoke API endpoints in API Builder

Any callback in the application that is passed the request object can access the endpoints programmatically.

To invoke an API endpoint:

1. Retrieve an instance to API Builder using the request.server property.

2. Retrieve the API instance using API Builder's getAPI('endpoint', 'verb') method by passing it the endpoint without the server host or address as the first parameter and the HTTP verb as the second parameter.

3. Invoke the execute(params, callback) method on the API instance by passing it a dictionary of parameters as the first parameter and a callback function as the second parameter. The callback function is passed an error and results object.

**Example:**

The Route below is invoking the GET <SERVER\_ADDRESS>/api/car method programmatically.

**web/routes/testroute.js**

```javascript
var TestRoute = Arrow.Router.extend({
    name: 'car',
    path: '/car',
    method: 'GET',
    description: 'get some cars',
    action: function (req, res, next) {

        req.server.getAPI('api/car', 'GET').execute({}, function(err, results) {
            if (err) {
                next(err);
            } else {
                req.log.info('got cars ' + JSON.stringify(results));
                res.render('car', results);
            }
        });
    }
});

module.exports = TestRoute;
```
