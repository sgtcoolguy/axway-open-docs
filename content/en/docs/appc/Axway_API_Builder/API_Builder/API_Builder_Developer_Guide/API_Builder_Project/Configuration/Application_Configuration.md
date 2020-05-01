{"title":"Application Configuration","weight":"10"}

{{% alert title="❗️ API Builder 3.x is deprecated" color="danger" %}}Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.{{% /alert %}}

By default, each API Builder project includes a configuration file, in JSON format, called appc.json located in the project's top-level folder. The settings in the file tell the Appcelerator CLI and AMPLIFY Runtime Services the nature of the project, which API Builder components are required by the project and any special deployment settings.

**appc.json**

```json
{
    "type": "api",
    "group": "arrow",
    "dependencies": {
        "connector/appc.arrowdb": "*",
        "connector/appc.composite": "*"
    },
    "cloud": {
        "container": "Medium",
        "minimum": 1,
        "maximum": 1,
        "maxqueuesize": 50,
        "environment": {},
        "domain": null,
        "certificate": null
    }
}
```

## Cloud

The cloud object contains key-value pairs to configure AMPLIFY Runtime Services deployment settings. Instead of running a sequence of appc cloud commands, define the following keys:

| Key | Description |
| --- | --- |
| certificate | Specify the path to the custom SSL certificate to use for HTTPS requests. |
| container | Sets the container size to use. Value can either be Dev, Small, Medium, Large or Xlarge. Default is Medium. The use of Small containers should be avoided. For optimum memory performance, use Medium or larger containers. |
| domain | Set domain binding for the application to the specified domain name. A domain record must exist for the specified domain name, pointing to the application's cloud.appcelerator.com URL. Do not specify the protocol, that is, do not add \`http://\` or \`https://\`, when setting this parameter. |
| domainPath | Specifies a URL path for routing. Use this parameter when setting more than one application to the same domain name. You must also set the domain key. |
| environment | An object containing key-value pairs of environment variables to set for the application, where the key is the variable name and the value is the value to set. |
| maximum | Sets the maximum number of server containers that can be used when scaling the application. The default is 1. |
| maxqueuesize | Sets the maximum number of queued requests for autoscaling to occur. AMPLIFY Runtime Services will increase the number of containers if the queue is too high for at least one minute. The default is 50. |
| minimum | Sets the minimum number of server containers to use. The default is 1. |

## Dependencies

The dependencies object contains key-value pairs of API Builder components required by the project. The key is the name of the component and the value is the version of the component. By default, API Builder automatically adds the dependencies. You should not need to change the value unless you are removing a component from the project.

## Type

The type key is the project type. Values can be api, block, connector, or model. By default, API Builder sets this property when you generate a new project. You should not need to change the value.

## Configuration override

Since Release 5.0.0, you can override the configuration file settings with an environment variable. For the setting, you want to override, prefix the variable with ARROW\_. For example, if you want to override the apikey setting, set the ARROW\_APIKEY environment variable.

### Example

**./conf/foo.js**

```javascript
module.exports = {
    // These are generated when you create a new project
    apikey_production: 'xxxxxxxxxxxxxxxxxxxxxxxxx',
    apikey_development: 'yyyyyyyyyyyyyyyyyyyyyyyyy',

    // Selects the authorization type -- uses HTTP Basic Authorization by default
    APIKeyAuthType: 'basic',

    // All API paths will be prefixed with '/foo'
    apiPrefix: '/foo',

    // Sets body-parser middleware setting
    bodyParser: {
        limit: 1 * 1024 * 1024
    },

    // Sets busboy initialization settings
    busboy: {
        limit: {
            fieldNameSize: 100,
            fieldSize: 1 * 1024 * 1024
        }
    },

    // Connector settings...
    connectors: {
        connector_name: {
            collection: 'foobar'
        },
        another_connector: {
            name: 'foobaz'
        }
    },

    // et cetera
}
```
