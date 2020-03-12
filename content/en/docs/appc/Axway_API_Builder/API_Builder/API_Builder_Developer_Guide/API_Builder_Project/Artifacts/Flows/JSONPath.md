{"title":"JSONPath","weight":"10"} 

# JSONPath

API Builder 3.x is deprecated

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.

JSONPath is referred to commonly throughout this documentation. It is a string that is used to select objects at a number of points within the flow. A query is run on a JSON object and will return the first match.

More details can be found here: [https://www.npmjs.com/package/jsonpath](https://www.npmjs.com/package/jsonpath)

## Query examples

This example shows a potential object which could be selected by JSONPath. The following examples show a selector and the object which would be resolved by the Flow when performing the query.

`// object being queried`

`var` `object = {`

`foo: {`

`bar:` `"baz"`

`}`

`};`

### Root object

Returns the value of the whole object.

`"$"`  `// {foo: { bar: "baz"} }`

### Property

Returns the value of the foo property on the root object.

`"$.foo"`  `// { bar: "baz" }`

### Nested property

Returns the value of bar on the foo property of the root object.

`"$.foo.bar"`  `// "baz"`

### Non-existent property

Returns the value of the bar property on the root object. The root object does not contain that property so nothing is matched.

`"$.bar"`  `// undefined`