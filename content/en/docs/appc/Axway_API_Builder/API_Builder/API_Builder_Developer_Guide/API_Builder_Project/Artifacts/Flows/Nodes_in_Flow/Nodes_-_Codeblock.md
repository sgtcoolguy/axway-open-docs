{"title":"Nodes - Codeblock","weight":"20"} 

API Builder 3.x is deprecated

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.

This document describes a Codeblock flow-node and provides information on Codeblock flow-node configuration, metadata, and functionality.

Name

Description

Codeblock

A flow-node that can be used for executing user code and returns the response. This flow-node allows custom business logic to be executed as part of the flow.

## Instance configuration (config)

Property

Description

Required

Type

method

The name of the Codeblock to execute.

yes

string

The typical usage of code blocks in a flow involves setting parameters, mapping responses, and setting required configs as noted in the example below.

## Metadata

Codeblock metadata should be included in the /codeblocks directory of an API Builder Project. It is defined as a JSON file with the following properties:

Property

Description

Required

Type

name

The name of the Codeblock

yes

string

description

The description of the Codeblock

yes

string

path

The relative path to the function to be invoked.

yes

string

### Configuration and metadata example

`{`

`"schemaVersion"``:` `"1"``,`

`"name"``:` `"Greet"``,`

`"description"``:` `"Some codeblock to run with Greet flow"``,`

`"path"``:` `"Greet.js"``,`

`"parameter"``: {`

`"type"``:` `"object"``,`

`"properties"``: {`

`"username"``: {`

`"type"``:` `"string"`

`}`

`},`

`"required"``: [`

`"username"`

`],`

`"additionalProperties"``:` `false`

`},`

`"outputs"``: {`

`"next"``: {`

`"description"``:` `"The codeblock completed."``,`

`"context"``:` `"$.greeting"``,`

`"schema"``: {`

`"$ref"``:` `"schema:///schema/foo/greeting"`

`}`

`},`

`"error"``: {`

`"description"``:` `"The codeblock failed to complete."``,`

`"context"``:` `"$.error"``,`

`"schema"``: {`

`"$ref"``:` `"schema:///schema/foo/error"`

`}`

`}`

`}`

`}`

## Functionality

The functional part of a Codeblock should be a .js file which exports a function of the following signature:

**invoke(arrow, params, cb);**

*   arrow <Arrow> - The API Builder instance.
    
*   params <Object> - Key/value pairs of parameters passed to the flow-node instance.
    
*   cb <Function> - Callback.
    
    *   err - Error. Passing this will cause the flow to cease processing and a 500 error to be returned from the endpoint which called it.
        
    *   response - The data to be returned as the flow-node response.
        

Most of the time errors should be returned in the callback as a standard response. Using the first parameter to return errors is the same as throwing an error in the Codeblock and should rarely need to be used.

### Functionality example

`function` `invoke(arrow, params, cb) {`

`const salutation = arrow.config.helloworld.salutation;`

`if` `(!params.username) {`

`return` `cb(``null``, {`

`error:` `'Invalid name'`

`});`

`}`

`const body = salutation +` `' '` `+ params.username;`

`cb(``null``, body);`

`}`

`exports = module.exports = invoke`