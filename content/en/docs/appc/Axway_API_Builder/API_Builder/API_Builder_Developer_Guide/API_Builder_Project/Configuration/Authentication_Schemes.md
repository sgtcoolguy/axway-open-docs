{"title":"Authentication Schemes","weight":"30"}

*API Builder 3.x is deprecated*

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.

* [Introduction](#introduction)

* [HTTP basic authentication](#http-basic-authentication)

* [HTTP header authentication](#http-header-authentication)

* [LDAP](#ldap)

* [Custom authentication](#custom-authentication)

## Introduction

An API Builder project provides different types of security mechanisms to authenticate requests. Typically, you want to restrict which client applications have access to your APIs, and you want the client to prove it has permission to access your API Builder application's APIs.

By default, a new API Builder project uses HTTP basic authentication, where the client must pass the API key in the Authorization header for each request. A new API Builder project contains two generated API keys, apikey\_development and apikey\_production, located in the conf/default.js file. The apikey\_development key contains the key used to test your project locally, while apikey\_production is used to make requests to your project when it is published. You may change the values for these keys but make sure you generate a sufficiently unique value and do not share these keys with other API projects as they control access to your APIs. These keys should only be used by one API Builder project.

To change the authentication mechanism, open the conf/default.js file and change the APIKeyAuthType key to one of the following:

* **none** : No authentication. The client does not need any authentication to access these APIs. In this case, all client requests are accepted without any security. Use the value none for the key APIKeyAuthType.

* **basic** : Use HTTP basic authentication (default). The client uses the HTTP Authorization header to send an encoded version of the API Key using the [HTTP Basic Authentication](http://en.wikipedia.org/wiki/Basic_access_authentication) standard. The username part is the value of the API Key and the password part should be blank (empty string). Use the value basic for the key APIKeyAuthType.

* **apikey** : Use HTTP header authentication. The client sets the HTTP APIKey header to the value of the API Key. In this scenario, the server must only support HTTPS only endpoints so the key is not passed in plain text. Use the value apikey for the key APIKeyAuthType.

* **ldap** (since API Builder (Arrow) 1.2.x): Use the LDAP plugin for authentication. You must also set the ldap key to an object containing settings for the LDAP configuration. The client uses the HTTP Authorization header to send an encoded version of the API Key using the [HTTP Basic Authentication](http://en.wikipedia.org/wiki/Basic_access_authentication) standard. The username and password will be sent to the configured LDAP server for authentication. Use the value ldap for the key APIKeyAuthType.

* **plugin** : Use a custom or third-party authentication mechanism. Using the plugin strategy, you can extend the authentication to use any third-party or custom API authentication. To build your own plugin, set the value plugin for the key APIKeyAuthType to use this strategy, then set the key APIKeyAuthPlugin to the location of your plugin. The location can be a file path (relative to the current work directory of your server project directory) or the name of the module package available in the standard node\_modules location.

Separate API keys are configured for each environment. For example, separate API keys are configured for the development environment and for the production environment. The API key for the current environment must be used for basic and apikey authentication. The development API key must be used for authentication in the development environment and the production API key must be used for authentication in the production environment.

The following describes the authentication mechanisms.

## HTTP basic authentication

In HTTP basic access authentication, the client needs to send a username and password, sent as a base64-encoded string "<username>:<password>", in the Authorization header of the HTTP request, for example:

```
GET api/model HTTP/1.0
Authorization: Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ==
```

For API Builder applications, the username is the API key and the password field is left blank. For a Titanium application, you can construct the header and request as follows:

```javascript
var xhr = Ti.Network.createHTTPClient({
    onload: function onLoad() {
        alert("Loaded: " + this.status + ": " + this.responseText);
    },
    onerror: function onError() {
        alert("Error: " + this.status + ": " + this.responseText);
    }
});

xhr.open("GET", REQUEST_URL);
var authstr = 'Basic ' + Ti.Utils.base64encode(API_KEY + ':');
xhr.setRequestHeader("Authorization", authstr);
xhr.send();
```

## HTTP header authentication

In HTTP header authentication, the client sends the API key in a custom APIKey header. The server must only support HTTPS requests, so the key is not sent as plain text (unencrypted).

```javascript
var xhr = Ti.Network.createHTTPClient({
    onload: function onLoad() {
        alert("Loaded: " + this.status + ": " + this.responseText);
    },
    onerror: function onError() {
        alert("Error: " + this.status + ": " + this.responseText);
    }
});

xhr.open("GET", REQUEST_URL);
xhr.setRequestHeader("APIKey", API_KEY);
xhr.send();
```

## LDAP

Starting with API Builder 1.2.x, you may use the LDAP plugin to authenticate requests. The client application will need to use HTTP basic authentication to send the username and password in the HTTP authorization header to the API Builder application.

To use the plugin, you need to pass your LDAP settings to the ldap object in the conf/default.js file. Define the following key-value pairs:

| Key | Optional | Description |
| --- | --- | --- |
| url | No | LDAP URL to connect to. |
| adminDn | No | Distinguished name (DN) of the user that is allowed to connect to the LDAP database and read user and group data. |
| adminPassword | Yes | Password for the directory administrator. |
| searchBase | No | The base DN to search for users. |
| searchFilter | No | LDAP search filter to find a user. |
| groupSearchBase | Yes | The base DN to search for groups. |
| groupSearchFilter | Yes | LDAP search filter to find a group. |
| cache | Yes | Set to true to cache up to 100 sessions for five minutes. The default is false. |
| tlsOptions | Yes | Additional options to pass to the [Node.js tls.connect() callback](https://nodejs.org/api/tls.html#tls_tls_connect_options_callback). |

**Example:**

*conf/default.js*

```javascript
module.exports = {
    ...
    APIKeyAuthType: 'ldap',
    ldap: {
        url: 'ldap://ldap.foo.com:389',
        adminDn: 'cn=read-only-admin,dc=example,dc=com',
        adminPassword: 'password',
        searchBase: 'dc=example,dc=com',
        searchFilter: '(uid={{username}})'
    },
    ...
}
```

## Custom authentication

To use a custom authentication mechanism, you need to create a CommonJS module that exposes a plugin class and implements the following methods. All methods are optional, but to validate requests, you need to implement the validateRequest method, either the synchronous version or asynchronous version.

| Method Signature | Description |
| --- | --- |
| Plugin(server) | Constructor. Passed the server instance. The passed server instance has not registered any models or connectors and has not been started. |
| Plugin.prototype.matchURL(request): Boolean | Determines if the URL should be authenticated by the plugin. Return true if the plugin should handle the validation else return false. |
| Plugin.prototype.validateRequest(request, response): Boolean | Validates the request synchronously. Return a Boolean value indicating if the request passed validation (true) or not (false). Do not implement if you implemented the asynchronous version of this method. |
| Plugin.prototype.validateRequest(request, response, callback): void | Validates the request asynchronously. Pass the callback an Error as its first argument (or null if successful) and a Boolean indicating if validation was a successful or not as its second argument. Do not implement if you implemented the synchronous version of this method. |
| Plugin.prototype.applyCredentialsForTest(options): void | Used by the API Doc tab in the API Builder Console to allow the plugin to apply any authentication headers to the request before it is made. The options object is the same options object passed to the [request library](https://www.npmjs.com/package/request). |
| Plugin.prototype.applyRequestsForTest(response, body): Object | Used by the API Doc tab in the API Builder Console to allow the plugin to modify the authentication response headers, body, etc. |
| Plugin.prototype.getSwaggerSecurity | Used by Swagger generation to describe the Swagger Definitions Object and the Swagger Requirement Object authentication mechanism. |

In the conf/default.js file, set the APIKeyAuthPlugin key to the location of the plugin file or to the name of the flow-node module if you specify it as a dependency in the package.json file.

For example, if your client applications send a custom header, called X-Secret, for each request and you want to check the value sent with the request against one stored in your configuration file, you can use the plugin below.

*conf/default.js*

```javascript
module.exports = {
    ...
    APIKeyAuthType: 'plugin',
    APIKeyAuthPlugin: './lib/plugin.js',
    secret: 'secret',
    ...
}
```

*lib/plugin.js*

```javascript
// Constructor to get a reference to the config object
function Plugin(server) {
    this.config = server.config || {secret: null};
}

// Only validate requests to /api/foo
Plugin.prototype.matchURL = function(request) {
    return request.url.indexOf('/api/foo') !== 0;
};

// Check if the request has the X-Secret header and its value matches the config file
Plugin.prototype.validateRequest = function(request, response) {
    if (request.headers['x-secret'] && request.headers['x-secret'] === this.config.secret) {
        return true;
    } else {
        return false;
    }
};

// Add the X-Secret header for internal requests
Plugin.prototype.applyCredentialsForTest = function(options) {
    options.headers['x-secret'] = this.config.secret;
};

// Do not process the response
Plugin.prototype.applyResponseForTest = function(response, body) {
    return body;
};

// Describe the x-security header for the Swagger 2.0 feed
Plugin.prototype.getSwaggerSecurity = function () {
  return {
    securityDefinitions: {
      app_auth: {
        type: 'apiKey',
        name: 'x-secret',
        in: 'header',
        description: 'Require authorized access to API'
      }
    },
    security: [{
      app_auth: []
    }]
  }
}

module.exports = Plugin;
```

To test the plugin, add the \-H 'X-Secret: secret' command-line option to the cURL request.

```
$ curl "http://127.0.0.1:8080/api/foo"
{"id":"com.appcelerator.api.unauthorized","message":"Unauthorized","success":false}
$ curl "http://127.0.0.1:8080/api/foo" -H 'X-Secret: secret'
{"success":true,"request-id":"0d2141f7-57ea-4c78-82cf-b6fa9497c16a", "foo":"bar"}
```
