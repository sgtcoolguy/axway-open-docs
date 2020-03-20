{"title":"API Runtime Configuration","weight":"80"}

*API Builder 3.x is deprecated*

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.

By default, each project includes a configuration file, in JSON format, called appc.json located in the project's top-level folder. The settings in the file tell the Appcelerator CLI and AMPLIFY Runtime Services the nature of the project, which components are required by the project, and any special deployment settings.

*appc.json*

```json
{
  "type": "api",
  "group": "arrow",
  "dependencies": {
    "connector/appc.arrowdb": "*",
    "connector/appc.composite": "*"
  },
  "cloud": {
    "container": "Dev",
    "minimum": 1,
    "maximum": 1,
    "maxqueuesize": 50,
    "environment": {},
    "cname": null,
    "certificate": null
  }
}
```

## Cloud

The cloud object contains key-value pairs to configure AMPLIFY Runtime Services deployment settings. Instead of running a sequence of appc cloud commands, define the following keys:

| Key | Description |
| --- | --- |
| certificate | Specify the path to the custom SSL certificate to use for HTTPS requests. |
| container | Sets the container size to use. Value can either be Dev, Small, Medium, Large or Xlarge. The default value is Medium. The use of small containers should be avoided. For optimum memory performance, use medium or higher size containers. |
| domain | Set domain binding for the application to the specified domain name. A domain record must exist for the specified domain name, pointing to the application's cloud.appcelerator.com URL. Do not specify the protocol, that is, do not add http:// or https://, when setting this parameter. |
| domainPath | Specifies a URL path for routing. Use this parameter when setting more than one application to the same domain name. You must also set the domain key. |
| environment | An object containing key-value pairs of environment variables to set for the application, where the key is the variable name and the value is the value to set. |
| maximum | Sets the maximum number of server containers that can be used when scaling the application. The default value is 1. |
| maxqueuesize | Sets the maximum number of queued requests for autoscaling to occur. AMPLIFY Runtime Services will increase the number of containers if the queue is too high for at least one minute. The default value is 50. |
| minimum | Sets the minimum number of server containers to use. The default value is 1. |

## Dependencies

The dependencies object contains key-value pairs of components required by the project. The key is the name of the component and the value is the version of the component. By default, API Builder automatically adds the dependencies. You should not need to change the value unless you are removing a component from the project.

## Type

The type key is the project type. Values can be api, block, connector, or model. By default, API Builder sets this property when you generate a new project. You should not need to change the value.
