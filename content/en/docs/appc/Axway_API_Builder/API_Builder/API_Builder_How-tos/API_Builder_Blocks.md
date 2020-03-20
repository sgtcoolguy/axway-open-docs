{"title":"API Builder Blocks","weight":"10"}

*API Builder 3.x is deprecated*

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.

* [Introduction](#introduction)

* [Block definition](#block-definition)

* [Example](#example)

## Introduction

This guide covers the basics for creating Blocks. Blocks are functions that run before or after an API endpoint is executed. They can be used to modify the API request, to modify the API response or to execute common tasks like audit logging, caching, rate limiting or recording analytics. Multiple Blocks can be executed before or after an API request. Blocks are optional.

To programmatically create a Block, see the [API Builder.Block API reference.](#!/api/Arrow.Block)

## Block definition

Place all Block files in the project's blocks folder. You can only declare one Block per file. A Block file is a JavaScript file, which:

1. Loads the arrow module

2. Calls the module's Block.extend() method, passing in an object defining the block identifier and logic to execute

3. Exports the defined block using the module.exports variable

Set the following keys in the object passed to the Block.extend() method to define the Block:

| Name | Required | Description |
| --- | --- | --- |
| name | true | Block name. This name should be used when specifying blocks in your API endpoint definition. Assign the name value to either the before or after property in the API definition object to use it. |
| description | true | Human useful description to display in the documentation. |
| execute | true | The function containing the logic for your block. All of your runnable code goes in the execute function. This function is passed a request, response, and next object to be used within your block. Once you are done with your block code, always call next() to continue on to the next step in the request flow. |
| documented | false | Determines whether to generate API documentation (true) or not (false). The default value is true. |

## Example

The following Block replaces the id parameter to 2 and logs the change.

```javascript
var Arrow = require('arrow');

var PreBlock = Arrow.Block.extend({
    name: 'pre_example',
    description: 'will set a header named "Foo"',

    execute: function(req, res, next) {
        req.params.id = 2;
        req.log.info("Changing params.id to 2");
        next();
    }
});

module.exports = PreBlock;
```
