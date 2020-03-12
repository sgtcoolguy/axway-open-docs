{"title":"Mobile Backend Services SDK for Node.js","weight":"40"}

* [Installation](#Installation)

* [API usage](#APIusage)

  * [Setup](#Setup)

  * [Standard Mobile Back Services APIs](#StandardMobileBackServicesAPIs)

    * [User login example](#Userloginexample)

    * [Photo or file upload example](#Photoorfileuploadexample)

  * [Generic Mobile Back Services APIs](#GenericMobileBackServicesAPIs)

* [User login session management](#UserloginsessionmanagementUserloginsessionmanagement)

  * [Cookie-based session management](#Cookie-basedsessionmanagement)

  * [Manual session management](#Manualsessionmanagement)


The Mobile Back Services (MBS) Node SDK lets you easily integrate MBS services with your Node.js application. The SDK provides two APIs:

* An API for each class and method.

* A set of generic REST APIs.


Your Node application can optionally handle session data itself. For more information, see the [User login session management](#Userloginsessionmanagement) section.

## Installation

To use the module within your Node application, add the arrowdb module to the dependencies section of your package.json file, as follows:

`"dependencies"``: {`

`"arrowdb"``:` `">=1.0.6"`

`}`

You can then run npm install from your application folder to install the module and its dependencies.

You can also install the module directly using npm:

`[sudo] npm install arrowdb`

As of this writing, the latest version is **1.0.6**.

## API usage

### Setup

To use the MBS APIs, load the arrowdb module, then create an instance with the new constructor, passing it your MBS application key. Invoke API calls on the instance.

`var` `ArrowDB = require(``'arrowdb'``),`

`arrowDBApp =` `new` `ArrowDB(``'<App Key>'``);`

`arrowDBApp.usersLogin(params, callback);`

Invoking the API calls on the instance only needs to be done once, typically in the main app.js script file.

You may optionally pass the constructor an object as the second argument. You may set the following properties on the object:

* apiEntryPoint: Base URL of the MBS server. By default, it is https://api.cloud.appcelerator.com.

* autoSessionManagement: Set to false to manually manage the session cookie or session ID. By default, it is true, and the SDK automatically handles the sessions.

* responseJsonDepth: Sets the response\_json\_depth parameter for all API calls. By default, the value is 1. You may set the value from 1 to 8.


For example:

`var` `ArrowDB = require(``'arrowdb'``),`

`arrowDBApp =` `new` `ArrowDB(``'<App Key>'``, {`

`apiEntryPoint:` `'https://api.cloud.appcelerator.com'`

`autoSessionManagement:` `false``,`

`responseJsonDepth: 3`

`});`

### Standard Mobile Back Services APIs

The standard MBS APIs provide a standardized API name for each REST object and method. Invoke the method on the MBS SDK instance.

The API name of most of the standard MBS Node API calls is the concatenation of the REST class name and method in lower camel case notation. For example, the User's object login method will be usersLogin. Check the Node example of the method to see its exact name.

Pass each method, an optional parameter object, and a required callback.

Set any method parameters on the parameters object. The parameters object may be omitted. For middleware calls, such as Express, you may optionally pass the request, and response objects to the parameters object using the req and res keys, respectively.

The callback is passed an Error object (or null if successful) and the results of the method call. The results object contains the following properties:

* body: HTTP response body as a JSON object.

* cookieString: Session cookie string if the API returns a session ID else it will be an empty string.

* reason: HTTP error message.

* response: [Node.js http.ServerResponse object](https://nodejs.org/docs/latest/api/http.html#http_class_http_serverresponse).

* statusCode: HTTP status code.


To access the results from the returned object, use the object's body property to access the HTTP response body. The body object will contain a meta object, which contains the metadata of the response and a response object, which contains the results of the method call.

#### User login example

The following example uses the standard MBS APIs to log in to a user. It defines a custom login() function that takes the username and password properties from the HTTP request body, and in turn, pass those values as input to the User.login() method. On successful login, the user's information is displayed in the console, or, in case of an error, the error response is displayed.

`var` `ArrowDB = require(``'arrowdb'``),`

`arrowDBApp =` `new` `ArrowDB(``'<App Key>'``);`

`function` `login(req, res) {`

`var` `data = {`

`login: req.body.username,`

`password: req.body.password,`

`// the req and res parameters are optional`

`req: req,`

`res: res`

`};`

`arrowDBApp.usersLogin(data,` `function``(err, result) {`

`if` `(err) {`

`console.error(``"Login error:"` `+ (err.message || result.reason));`

`}` `else` `{`

`console.log(``"Login successful!"``);`

`console.log(``"UserInfo: "` `+ JSON.stringify(result.body.response.users[0]));`

`}`

`});`

`}`

#### Photo or file upload example

The following example uses the standard MBS APIs to upload a photo or a file. It defines a custom upload() function that captures the fileName and fileObject, creates a file buffer for string and readable stream, and logs in the user. If the login is successful, the file is uploaded. If a login error occurs, the login error response is displayed. If a file upload error occurs, the upload error response is displayed.

For increased file security, it is recommended that files be encrypted before uploading them.

`function` `upload(req, res) {`

`console.log(req.body.fileName);`

`//console.log(req.body.fileObject);`

`// Create buffer for string and readable stream`

`var` `buffer =` `new` `Buffer(req.body.fileObject);`

`var` `base64String = buffer.toString(``"base64"``);`

`var` `bufferStream =` `new` `stream.PassThrough();`

`bufferStream.end(buffer);`

`// Setup and login to ArrowDB`

`var` `ArrowDB = require(``'arrowdb'``),`

`arrowDBApp =` `new` `ArrowDB(``'<App Key>'``);`

`arrowDBApp.usersLogin({`

`login:` `'<login>'``,`

`password:` `'<password>'`

`},` `function``(err, result) {`

`if` `(err) {`

`console.error(err.message);`

`}` `else` `{`

`arrowDBApp.sessionCookieString = result.cookieString;`

`sessionID = result.body.meta.session_id;`

`bufferStream.end(base64String);`

`var` `fileInfo = {`

`value: bufferStream,`

`options: {`

`filename: req.body.fileName,`

`knownLength: req.body.fileObject.length`

`}`

`}`

`// On login success create the file`

`arrowDBApp.filesCreate({`

`name: req.body.fileName,`

`file: fileInfo`

`},` `function``(err, result) {`

`if` `(err) {`

`console.error(JSON.stringify(err,` `null``,` `"\t"``));`

`}` `else` `{`

`console.log(result.body.response.files[0]);`

`}`

`});`

`}`

`});`

`}`

### Generic Mobile Back Services APIs

The MBS Node SDK provides the following four methods for making generic calls to MBS:

* sdkObject.post(path, parameters, callback)

* sdkObject.put(path, parameters, callback)

* sdkObject.get(path, parameters, callback)

* sdkObject.delete(path, parameters, callback)


Each method is passed the following parameters:

* path: The path of the REST resource to call relative to the base URL (by default, it is https://api.cloud.appcelerator.com).

* parameters: The parameters to pass to the method. It can be omitted.

* callback: The function to call when the request completes. The callback is passed an Error object (or null if successful) and the results of the method call.


Below is a complete REST example that is functionally equivalent to the previous version that used the standard MBS APIs.

`var` `ArrowDB = require(``'arrowdb'``),`

`arrowDBApp =` `new` `ArrowDB(``'<App Key>'``);`

`function` `login(req, res) {`

`var` `data = {`

`login: req.body.username,`

`password: req.body.password`

`};`

`arrowDBApp.post(``'/v1/users/login.json'``, data,` `function``(err, result) {`

`if` `(err) {`

`console.error(``"Login error:"` `+ (err.message || result.reason));`

`}` `else` `{`

`console.log(``"Login successful!"``);`

`console.log(``"UserInfo: "` `+ JSON.stringify(result.body.response.users[0]));`

`}`

`});`

`}`

## User login session management

Most of the MBS APIs require a user to be logged in, so it is important to have a way to manage user sessions in your Node.js application. The MBS Node SDK provides two ways of managing MBS login sessions in a Node.js application:

* **Cookie-based**. Cookies are used to store session information and passed between the client and the server.

* **Session ID**. Must pass a session ID with every API call.


These methods are described in the following sections.

### Cookie-based session management

Cookies are frequently used by MBS applications to store session information and are passed between the client and server.

The MBS Node SDK retrieves the session ID from the request's cookies. If a \_session\_id cookie is present, it uses that session ID to make the MBS API call. If not, it performs a regular API call without session information.

If a session ID is returned in the API response (for example users/login.json), the session information is added to the response object. Specifically, it adds a Set-Cookie header to pass back to the client.

To manually manage cookie sessions, disable automatic session management by passing an object as the second parameter to the constructor with the autoSessionManagement property set to false. MBS will no longer automatically retrieve and set the session cookie. You must manually set the MBS instance's sessionCookieString property once you retrieve a cookie string. The cookie string is available in the cookieString property in the callback's result object if the API response returns a session ID.

The example below retrieves and sets the cookie string:

`var` `ArrowDB = require(``'arrowdb'``),`

`arrowDBApp =` `new` `ArrowDB(``'<App Key>'``, {autoSessionManagement:` `false``});`

`function` `login(req, res) {`

`var` `data = {`

`login: req.body.username,`

`password: req.body.password`

`};`

`arrowDBApp.post(``'/v1/users/login.json'``, data,` `function``(err, result){`

`if` `(err) {`

`console.error(``"Login error:"` `+ (err.message || result.reason));`

`}` `else` `{`

`console.log(``"Login successful!"``);`

`arrowDBApp.sessionCookieString = result.cookieString;`

`}`

`});`

`}`

**Important**

* The MBS Node SDK sets the cookie header in the response object, which must be done _before_ sending any response data (for example, by calling the response object's send method). If you send any response data _before_ the API callback function is invoked, the MBS Node SDK will throw an exception when it tries to set the cookie headers, with a message like, "Can't render headers after they are sent to the client."

* Session information is stored in a cookie named \_session\_id. You can also manually set this session ID cookie on the client-side. For example, if you are calling your AMPLIFY Runtime Services from a Titanium application that uses MBS directly, you can retrieve the active session ID from the Titanium.Cloud.sessionId property, and adding a Set-Cookie header when requesting the AMPLIFY Runtime Services.


### Manual session management

An MBS user login session is identified by a session\_id parameter in the request or response data. When logging in to a user account or creating a new user, the session\_id is returned in the response data of the API calls. It can be retrieved from the response data by using the body.meta.session\_id property of the callback's result object. For example:

`function` `loginUser(req, res) {`

`arrowDBApp.usersLogin({`

`login:` `'test'``,`

`password:` `'test'`

`},` `function``(err, result) {`

`console.log(``'Login session is: '` `+ result.body.meta.session_id);`

`});`

`}`

To reuse this session for making other API calls, pass it in as part of the request parameters (session\_id: \_stored\_session\_id\_). This gives you full control of the sessions. You can store a session and reuse it (as long as the session is not expired on the MBS server) later for making API calls. For example:

`function` `createPlace(req, res) {`

`arrowDBApp.placesCreate({`

`name:` `'test'``,`

`city:` `'city_name'``,`

`session_id:` `'<stored session_id>'`

`},` `function``(err, result) {`

`console.log(``'New place created!'``);`

`});`

`}`
