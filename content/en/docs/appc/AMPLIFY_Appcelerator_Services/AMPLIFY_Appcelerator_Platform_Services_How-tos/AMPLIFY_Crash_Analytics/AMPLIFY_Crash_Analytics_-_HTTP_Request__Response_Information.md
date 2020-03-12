{"title":"AMPLIFY Crash Analytics - HTTP Request /Response Information","weight":"20"} 

The AMPLIFY Crash Analytics (ACA) [API](https://docs.appcelerator.com/platform/latest/#!/api/Modules.ACA) can be used to log requests. Using breadcrumbs the REST API call's request/response information can be attached to crash events.

This sample code will automatically log the request time, response code, and response time in the breadcrumbs.

`function` `request(type, url, opts) {`

`const client = Ti.Network.createHTTPClient({`

`onload: e => {`

``aca.leaveBreadcrumb(`request.onload: ${e.source.status} -> ${url}`);``

`opts && opts.onload && opts.onload(e);`

`},`

`onerror: e => {`

``aca.leaveBreadcrumb(`request.onerror: ${e.source.status} (${e.error}) -> ${url}`);``

`opts && opts.onerror && opts.onerror(e);`

`},`

`timeout: (opts && opts.timeout) || 5000`

`});`

`client.open(type, url);`

`client.send();`

``aca.leaveBreadcrumb(`request: ${url}`);``

`}`

`// Example request to Google.`

`request(``'GET'``,` `'https://google.com/'``, {`

`onload: e => {`

``Ti.API.info(`onload: ${e.source.responseText}`);``

`}`

`});`

In the Dashboard , if you navigate to the Application's Crashes - > Crash Details -> Occurrences tab you can view the breadcrumb by expanding a crash occurrence.

![Screen_Shot_2019-09-20_at_11.17.25_AM](/Images/appc/download/attachments/60148834/Screen_Shot_2019-09-20_at_11.17.25_AM.png)