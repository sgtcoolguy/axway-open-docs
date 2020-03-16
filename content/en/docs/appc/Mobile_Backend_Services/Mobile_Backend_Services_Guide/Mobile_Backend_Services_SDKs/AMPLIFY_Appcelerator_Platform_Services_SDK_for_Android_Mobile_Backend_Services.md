{"title":"AMPLIFY Appcelerator Platform Services SDK for Android Mobile Backend Services","weight":"20"}

* [Getting the SDK](#getting-the-sdk)

* [Running the APSCloud example application](#running-the-apscloud-example-application)

* [Enabling Cloud services in a new project](#enabling-cloud-services-in-a-new-project)

* [Making API Calls and Handling Responses](#making-api-calls-and-handling-responses)

    * [Building Request Parameters](#building-request-parameters)

    * [Handling Responses](#handling-responses)

        * [Example: APSUsers Login Call with Response Handler](#example:-apsusers-login-call-with-response-handler)

    * [Monitoring Request Progress](#monitoring-request-progress)

        * [Example: APSFiles Create Call with Progress Handler](#example:-apsfiles-create-call-with-progress-handler)

* [Making Generic REST APIs Method Calls](#making-generic-rest-apis-method-calls)

* [Working with Push Notifications](#working-with-push-notifications)

    * [Android Project Requirements for using APSCloud Push](#android-project-requirements-for-using-apscloud-push)

        * [Add Google Play services](#add-google-play-services)

        * [AndroidManifest changes](#androidmanifest-changes)

    * [Subscribe to push notifications](#subscribe-to-push-notifications)

    * [CloudPush sample application](#cloudpush-sample-application)

The AMPLIFY Appcelerator Platform Services SDK for Android provides APIs for your Android application built with Java to access Mobile Backend Services (MBS).

## Getting the SDK

To download and start using the SDK, you first need to register your Android application in [Dashboard](https://platform.axway.com/). See [Managing Non-Titanium Client Applications in Dashboard](/docs/appc/Appcelerator_Dashboard/Appcelerator_Dashboard_Guide/Managing_Applications/Managing_Client_Applications/Managing_Non-Titanium_Client_Applications_in_Dashboard/) for details on registering a new application. After you register the application, a service key is generated that associates your application with all the Platform services. Appcelerator Dashboard also provides full instructions for enabling all Platform Services in your application. This guide will deal specifically with enabling and using MBS in an Android application.

![dashboard_latest](/Images/appc/download/attachments/49153767/dashboard_latest.png)

## Running the APSCloud example application

The SDK ZIP file includes an Android sample project that demonstrates the basic usage of each of the Cloud APIs. To run the sample, you first need to register a new application in Dashboard to obtain the necessary service key. You will then copy the key into the imported sample project's main Activity and then run the application.

**To create the APSCloudExample application in Dashboard:**

1. Log into the [AMPLIFY Platform](https://platform.axway.com/).

2. Select the **Dashboard** link on the Dashboard tile.

3. From the **Orgs** menu, select the organization to associate with the application. Note that the Orgs menu will not appear if you are not a member of multiple organizations.

4. Click the Add menu (+) and select **Register App for Services**.

5. In the dialog:

    * Type **APSCloudExampleApp** (or another name) in the **Name** field.

    * Select **Android** from the **Platform** menu.

    * Select any category from the **Category** menu.

6. Click **Next** and then click the **Overview** tab.

7. Click the **Services** tab, then click **Show Key** under **Cloud** \> **Performance** \> **Analytics**.

8. Select **Development** from the Environment menu, then click the **clipboard icon** to copy the key to your clipboard.

Next, import the APSCloudExample project into Eclipse, copy the key from your clipboard into the application's main activity, and run the application.

**To import the completed APSCloudExample project:**

1. In Eclipse, select **File** \> **Import** \> **General** \> **Existing Code into Workspace**, then click **Next**.

2. Click **Browse** and navigate to the **appcelerator-sdk-android-<VERSION>/examples/APSCloudExample** folder, and click **Open**.

3. Click **Finish**.

4. Open the **src/main/java/com/appcelerator/apscloudexample/MainActivity.java** file.

5. Locate the following line of code and replace **<< YOUR APP KEY >>** with the application key you copied to your clipboard previously.

    `APSServiceManager.getInstance().enable(getApplicationContext(),` `"<< YOUR APP KEY >>"``);;`

6. Run the application on an Android device or emulator.

Once the application is running, try the following:

* Create a new user by selecting **Users** \> **Create User**. Enter a username, password, and password confirmation, then click **Create**. If the user is created successfully, the following dialog is shown:

    ![new_user_success](/Images/appc/download/attachments/49153767/new_user_success.png)

* View the newly created user in Dashboard:

    1. Log into the [AMPLIFY Platform](https://platform.axway.com/).

    2. Select the **Dashboard** link on the Dashboard tile.

    3. Select your MBS application from the **Apps** tab.

    4. Select **Manage Data**, then click **Users** in the Manage Data Objects table. You should see the user you created listed in the Users table.

        ![verify_new_user_latest](/Images/appc/download/attachments/49153767/verify_new_user_latest.png)

## Enabling Cloud services in a new project

Once you've [registered an application in Dashboard](/docs/appc/Appcelerator_Dashboard/Appcelerator_Dashboard_Guide/Managing_Applications/Managing_Client_Applications/Managing_Non-Titanium_Client_Applications_in_Dashboard/), downloaded the SDK, and obtained your application service key, there are few steps to enable Cloud services in your Android project.

**To enable the Cloud services in your project**:

1. Copy the **appcelerator-sdk-android-<VERSION>.jar** file to your project's libs folder.

2. Add the following permission to your project's AndroidManifest.xml file:

    `<``uses``-permission` `android:name``=``"android.permission.INTERNET"```/>` ``

3. Import the APSServiceManager class into the project's main Activity:

    `import com.appcelerator.aps.APSServiceManager;`

4. Call APSServiceManager.getInstance().enable(), passing it the application context and the application key provided by Dashboard:

    `APSServiceManager.getInstance().enable(getApplicationContext(),` `"<<YOUR APP KEY>>"``);`

    At this point, your application can begin making API calls. Note that the application will need to import additional classes, depending on which APS APIs it uses.

## Making API Calls and Handling Responses

The [com.appcelerator.aps](http://docs.appcelerator.com/aps-sdk-apidoc/latest/android/index.html?com/appcelerator/aps/package-summary.html) package contains a collection of classes whose methods map to individual REST API method endpoints. For example, the APSUsers.create() method corresponds to the /users/create.json method endpoint.

Alternatively, you can use the generic [APSCloud.sendRequest()](http://docs.appcelerator.com/aps-sdk-apidoc/latest/android/com/appcelerator/aps/APSCloud.html#sendRequest(java.lang.String, java.lang.String, java.util.Map, com.appcelerator.aps.APSResponseHandler)) method to make REST calls directly against the Cloud APIs. For more information, see [Making Generic REST API Calls](#making-generic-rest-apis-method-calls).

All Cloud API calls must be made on the UI (main) thread, and callbacks are executed on the UI thread.

### Building Request Parameters

The first parameter of each Cloud API method is a HashMap object that contains the parameters to send with the request. For example, the APSPhotos.show() method takes a photo\_id parameter whose value is, naturally, the ID of the photo to show.

`// Create dictionary of parameters to be passed with the request`

`HashMap<String, Object> data =` `new` `HashMap<String, Object>();`

`data.put(``"photo_id"``, photoId);`

`APSPhotos.show(data,` `new` `APSResponseHandler() {`

`...`

`});`

### Handling Responses

The second parameter of each method call is an instance of [APSResponseHandler](http://docs.appcelerator.com/aps-sdk-apidoc/latest/android/com/appcelerator/aps/APSResponseHandler.html), an interface that has the following signature:

`public interface APSResponseHandler {`

`void onResponse(final APSResponse e);`

`void onException(final APSCloudException e);`

`}`

The instance you specify must override the onResponse and onException methods. The onResponse method is invoked upon completion of a Cloud API call, and the onException handler is invoked if there is an exception while communicating with the MBS server.

The [APSResponse](http://docs.appcelerator.com/aps-sdk-apidoc/latest/android/com/appcelerator/aps/APSResponse.html) object provides getter methods to access information about the response. For instance, the getSuccess() method returns a boolean indicating if the method call was successful or not; the getResponse() method returns a JSON-encoded object with the results of the method call.

`@Override`

`public void onResponse(final APSResponse e) {`

`if` `(e.getSuccess()) {`

`// Read JSON response`

`JSONObject res = e.getResponse();`

`}` `else` `{`

`// Log error message:`

`Log.e(``"LOGIN"``, e.getMessage());`

`}`

`}`

The onException() handler is invoked for any exceptions that occur during communication with the MBS server.

`@Override`

`public void onException(APSCloudException e) {`

`// Handle exception`

`Log(e.getErrorType(), e.getErrorCode());`

`}`

#### Example: APSUsers Login Call with Response Handler

The following example logs in an existing MBS user by their username and password. After a successful login, the application updates a TextView object with the user's MBS username.

`HashMap<String, Object> data =` `new` `HashMap<String, Object>();`

`data.put(``"login"``,` `"username"``);`

`data.put(``"password"``,` `"password"``);`

`try` `{`

`APSUsers.login(data,` `new` `APSResponseHandler() {`

`@Override`

`public void onResponse(final APSResponse e) {`

`if` `(e.getSuccess()) {`

`try` `{`

`JSONObject res = e.getResponse();`

`// Response returns an array containing a single user`

`JSONArray payload = res.getJSONArray(``"users"``);`

`res = payload.getJSONObject(0);`

`loginTextView.setText(res.getString(``"username"``));`

`}` `catch` `(Exception e) {`

`Log.e(``"LOGIN"``,` `"Error parsing JSON object: "` `+ e.toString());`

`}`

`}`

`else` `{`

`Log.e(``"LOGIN"``, e.getMessage());`

`}`

`}`

`@Override`

`public void onException(APSCloudException e) {`

`// Handle exception that occured`

`}`

`});`

`}` `catch` `(APSClientError e) {`

`Log.e(``"LOGIN"``, e.getErrorType());`

`}`

### Monitoring Request Progress

For Cloud API methods that involve uploading large files, such as APSPhotos.create() or APSFiles.create(), there is an overloaded version that takes an optional progressHandler parameter. This parameter takes an [APSProgressHandler](http://docs.appcelerator.com/aps-sdk-apidoc/latest/android/com/appcelerator/aps/APSProgressHandler.html) instance, which must provide an onProgress handler. This handler is periodically triggered as the file transfer continues and is passed an integer between 0-100, indicating the current upload progress.

#### Example: APSFiles Create Call with Progress Handler

The following example uploads a file from the device (/res/raw/reference.pdf) to the MBS storage server. Since the method call requires that uploaded data be an instance of java.io.File, the application needs to copy the resource to a read-write directory before uploading it. Locally storing the file requires that the [WRITE\_EXTERNAL\_STORAGE](http://developer.android.com/reference/android/Manifest.permission.html#WRITE_EXTERNAL_STORAGE) permission is included in your AndroidManifest.xml file.

The progress callback calls the setProgress() method on a ProgressBar object, displaying the status of the upload. After the request completes, the application displays a toast notification.

`HashMap<String, Object> data =` `new` `HashMap<String, Object>();`

`String filename =` `"reference.pdf"``;`

`// Need to copy the resource to a read-write directory to upload it`

`if` `(!createExternalStoragePrivateFile(R.raw.reference, filename))` `return``;`

`File file =` `new` `File(currentActivity.getExternalFilesDir(``null``), filename);`

`data.put(``"file"``, file);`

`data.put(``"name"``,` `"Reference Manual"``);`

`try` `{`

`APSFiles.create(data,` `new` `APSClient.APSResponseHandler() {`

`@Override`

`public void onResponse(final APSResponse e) {`

`if` `(e.getSuccess()) {`

`APSCloud.log(``"PUSH"``,` `"Successfully subscribed to push!"``);`

`progressBar.setVisibility(View.GONE);`

`Toast.makeText(currentActivity,` `"File uploaded!"``, Toast.LENGTH_SHORT).show();`

`}`

`else` `{`

`Log.e(``"UPLOAD"``, e.getMessage());`

`}`

`}`

`},`

`new` `APSClient.APSProgressHandler() {`

`@Override`

`public void onProgress(final int percentProgress, final boolean upload) {`

`if` `(currentActivity !=` `null``) {`

`progressBar.setProgress(percentProgress);`

`}`

`});`

`}` `catch` `(APSClientError e) {`

`Log.e(``"UPLOAD"``, e.getMessage());`

`}`

`// Helper function to copy a resource to external storage, modified from:`

`// http://developer.android.com/reference/android/content/Context.html#getExternalFilesDir(java.lang.String)`

`public static boolean createExternalStoragePrivateFile(int inputResource, String filename) {`

`File file =` `new` `File(currentActivity.getExternalFilesDir(``null``), filename);`

`try` `{`

`InputStream is = currentActivity.getResources().openRawResource(inputResource);`

`OutputStream os =` `new` `FileOutputStream(file);`

`byte[] data =` `new` `byte[is.available()];`

`is.read(data);`

`os.write(data);`

`is.close();`

`os.close();`

`return`  `true``;`

`}` `catch` `(IOException e) {`

`Log.w(``"ExternalStorage"``,` `"Error writing "` `+ file, e);`

`return`  `false``;`

`}`

`}`

## Making Generic REST APIs Method Calls

The [APSCloud.sendRequest()](http://docs.appcelerator.com/aps-sdk-apidoc/latest/android/com/appcelerator/aps/APSCloud.html#sendRequest(java.lang.String, java.lang.String, java.util.Map, com.appcelerator.aps.APSResponseHandler)) method lets you quickly make REST API calls directly against MBS, rather than using the specialized classes (like APSUsers). In general, you should use specialized classes as they provide an easier API. However, if new REST methods are deployed to the APS Cloud backend, this approach lets you immediately start using those methods without waiting for an update to the SDK.

To make a generic request, you call APSCloud.getInstance() to get a reference to the shared APSCloud object and call its sendRequest() method. For each call, you must specify the following:

* REST API method endpoint relative to api.cloud.appcelerator.com/v1. Method endpoints are listed in the corresponding entries in the [REST API](/docs/appc/Mobile_Backend_Services/Mobile_Backend_Services_Guide/Using_the_REST_API/) documentation.

* The HTTP method to use.

* Data to send with the request.

For example, to [create a post](/arrowdb/latest/#!/api/Posts-method-create), pass the sendRequest() method the following information:

* REST API method endpoint: posts/create.json

* The HTTP method to use: POST

* Data to send with the request: at a minimum, you must specify the content property.

The following uses the sendRequest() API to create a new Post object.

`HashMap<String, Object> data =` `new` `HashMap<String, Object>();`

`data.put(``"title"``,` `"What's up?"``);`

`data.put(``"content"``,` `"The sun, the cloud, space..."``);`

`try` `{`

`APSCloud.getInstance().sendRequest(``"posts/create.json"``,` `"POST"``, data,` `new` `APSClient.APSResponseHandler() {`

`public void onResponse(final APSResponse e) {`

`if` `(e.getSuccess()) {`

`try` `{`

`JSONObject res = e.getResponse();`

`JSONArray payload = res.getJSONArray(``"posts"``);`

`res = payload.getJSONObject(0);`

`latestPost.setText(res.getString(``"title"``));`

`}` `catch` `(Exception err) {`

`Log.e(``"REST"``,` `"JSON Error: "` `+ err.getMessage());`

`}`

`}`

`else` `{`

`Log.e(``"REST"``, e.getMessage());`

`}`

`}`

`});`

`}` `catch` `(APSClientError e) {`

`Log.e(``"REST"``,` `"Error: "` `+ e.getMessage());`

`}`

## Working with Push Notifications

The [APSPushNotifications](http://docs.appcelerator.com/aps-sdk-apidoc/latest/android/com/appcelerator/aps/APSPushNotifications.html) class lets your application subscribe, send, and receive push notifications. To use the class, you also need the [APSCloudPush](http://docs.appcelerator.com/aps-sdk-apidoc/latest/android/com/appcelerator/aps/APSCloudPush.html) class, which provides the underlying services to handle incoming push notifications.

To use these classes:

* [Configure push services](/docs/appc/Titanium_SDK/Titanium_SDK_How-tos/Notification_Services/Push_Notifications/Configuring_Push_Services/) for your application.

* Add Google Play services as a dependency to your project and update the project's AndroidManifest.xml file. See the [Android Project Requirements section below](#android-project-requirements-for-using-apscloud-push).

* Retrieve the device token and subscribe to push notifications with MBS. See the [Subscribe to push notifications](#Subscribetopushnotifications) section below.

### Android Project Requirements for using APSCloud Push

Once you have configured your Google Cloud Messaging (GCM) or Firebase Cloud Messaging (FCM) settings in Dashboard, there are some required configuration changes to your Android project to use APSCloudPush. [Firebase Cloud Messaging](http://firebase.google.com/docs/cloud-messaging/) (FCM) is the new version of GCM.

#### Add Google Play services

APSCloudPush requires that Google Play services be included in your application.

1. Download the Google Play services SDK using the Android SDK Manager.

2. Copy the <android-sdk>/extras/google/google\_play\_services/libproject/google-play-services\_lib folder to the same workspace folder as your Android projects (not into your Android project).

3. Add the following inside the **<application/>** element of your AndroidManifest.xml file:

    `<``meta``-data` `android:name``=``"com.google.android.gms.version"`  `android:value``=``"@integer/google_play_services_version"` `/>`

For **Android Studio** projects, update the dependencies field of the build.gradle file, then save and sync the gradle file.

`...`

`dependencies {`

`...`

`compile` `'com.google.android.gms:play-services:6.5.87'`

`}`

For **Eclipse** projects:

1. Import the library project into Eclipse. (From the menu, click **File** > **Import**, then select **Android** > **Existing Android Code into Workspace**, and browse to the copy of the library project to import it.)

2. In the application project, reference the Google Play services library project. Right-click the project folder and select **Properties**, then select **Android**, click **Add..** and select the library project.

For other projects, update the project.properties file to reference the library project:

`android.library.reference.1=../google-play-services_lib`

For detailed directions, see [Android Developer: Setting Up Google Play Services](http://developer.android.com/google/play-services/setup.html).

#### AndroidManifest changes

The following changes must be added to your project's AndroidManifest.xml file to use APSCloudPush. Replace each occurrence of _"YOURAPPSPACKAGENAME"_ with the actual package name of your application.

* Inside the <manifest/> element:

    `<``uses``-permission` `android:name``=``"android.permission.INTERNET"``/>`

    `<``uses``-permission` `android:name``=``"android.permission.GET_ACCOUNTS"``/>`

    `<``uses``-permission` `android:name``=``"android.permission.WAKE_LOCK"``/>`

    `<``uses``-permission` `android:name``=``"com.google.android.c2dm.permission.RECEIVE"``/>`

    `<``uses``-permission` `android:name``=``"android.permission.ACCESS_NETWORK_STATE"``/>`

    `<``uses``-permission` `android:name``=``"android.permission.RECEIVE_BOOT_COMPLETED"``/>`

    `<``uses``-permission` `android:name``=``"android.permission.READ_PHONE_STATE"``/>`

    `<``uses``-permission` `android:name``=``"android.permission.VIBRATE"``/>`

    `<``uses``-permission` `android:name``=``"android.permission.WRITE_EXTERNAL_STORAGE"`

    `android:maxSdkVersion``=``"18"` `/>`

    `<``permission`  `android:name``=``"YOURAPPSPACKAGENAME.permission.C2D_MESSAGE"`

    `android:protectionLevel``=``"signature"``/>`

    `<``uses``-permission` `android:name``=``"YOURAPPSPACKAGENAME.permission.C2D_MESSAGE"``/>`

* Inside the <application/> element:

    `<``receiver`  `android:name``=``"com.appcelerator.aps.IntentReceiver"``/>`

    `<``receiver`

    `android:name``=``"com.appcelerator.aps.GCMReceiver"`

    `android:permission``=``"com.google.android.c2dm.permission.SEND"``>`

    `<``intent``-filter>`

    `<``action`  `android:name``=``"com.google.android.c2dm.intent.RECEIVE"``/>`

    `<``category`  `android:name``=``"YOURAPPSPACKAGENAME"``/>`

    `</``intent``-filter>`

    `</``receiver``>`

    `<``receiver`  `android:name``=``"com.appcelerator.aps.PushBroadcastReceiver"`

    `android:permission``=``"com.google.android.c2dm.permission.SEND"``>`

    `<``intent``-filter>`

    `<``action`  `android:name``=``"android.intent.action.BOOT_COMPLETED"``/>`

    `<``action`  `android:name``=``"com.google.android.c2dm.intent.REGISTRATION"` `/>`

    `<``action`  `android:name``=``"com.appcelerator.aps.intent.DEL_GROUPED_MSG"` `/>`

    `<``category`  `android:name``=``"YOURAPPSPACKAGENAME"` `/>`

    `</``intent``-filter>`

    `</``receiver``>`

    `<``receiver`  `android:name``=``"com.appcelerator.aps.PushBroadcastReceiver"``>`

    `<``intent``-filter>`

    `<``action`  `android:name``=``"android.intent.action.PACKAGE_ADDED"``/>`

    `<``action`  `android:name``=``"android.intent.action.PACKAGE_REPLACED"``/>`

    `<``data`  `android:scheme``=``"package"`  `android:path``=``"YOURAPPSPACKAGENAME"` `/>`

    `</``intent``-filter>`

    `</``receiver``>`

### Subscribe to push notifications

Once the project is set up, the application needs to register with MBS to receive push notifications. The application should do this once the application starts, for example, in the onCreate() method of the application's main activity.

To register push notifications, the application needs to retrieve the device token using the [APSCloudPush.getInstance.retrieveDeviceToken()](http://docs.appcelerator.com/aps-sdk-apidoc/latest/android/com/appcelerator/aps/APSCloudPush.html#retrieveDeviceToken(com.appcelerator.aps.APSRetrieveDeviceTokenHandler)) method, then pass the token to either the [APSPushNotifications.subscribe()](http://docs.appcelerator.com/aps-sdk-apidoc/latest/android/com/appcelerator/aps/APSPushNotifications.html#subscribe(java.util.Map,com.appcelerator.aps.APSResponseHandler)) or [APSPushNotifications.subscribeToken()](http://docs.appcelerator.com/aps-sdk-apidoc/latest/android/com/appcelerator/aps/APSPushNotifications.html#subscribeToken(java.util.Map,com.appcelerator.aps.APSResponseHandler)) method to subscribe to a push channel.

Call [APSServiceManager.getInstance()](http://docs.appcelerator.com/aps-sdk-apidoc/latest/android/com/appcelerator/aps/APSServiceManager.html#getInstance()) before calling any methods on APSCloudPush; otherwise, an exception will be thrown.

For example, the code below can be added to the main activity's onCreate() method to subscribe the device to the friend\_channel:

`APSCloudPush.getInstance().retrieveDeviceToken(``new` `APSRetrieveDeviceTokenHandler() {`

`@Override`

`public void onError(String message) {`

`Log.e(``"APSCloudPush"``,` `"Could not retrieve device token: "` `+ message);`

`}`

`@Override`

`public void onSuccess(String deviceToken) {`

`HashMap<String, Object> data =` `new` `HashMap<String, Object>();`

`data.put(``"type"``,` `"android"``);`

`data.put(``"channel"``,` `"friend_channel"``);`

`data.put(``"device_token"``, deviceToken);`

`try` `{`

`APSPushNotifications.subscribeToken(data,` `new` `APSResponseHandler() {`

`@Override`

`public void onResponse(final APSResponse e) {`

`if` `(e.getSuccess()) {`

`Log.i(``"APSPushNotifications"``,` `"Subscribed!"``);`

`}` `else` `{`

`Log.e(``"APSPushNotifications"``,` `"ERROR: "` `+ e.getErrorMessage());`

`}`

`}`

`@Override`

`public void onException(final APSCloudException e) {`

`Log.e(``"APSPushNotifications"``,` `"Exception throw: "` `+ e.toString());`

`}`

`});`

`}` `catch` `(APSCloudException e) {`

`Log.e(``"APSPushNotifications"``,` `"Exception thrown: "` `+ e.toString());`

`}`

`}`

`});`

Once push services have been configured, and you've obtained a device token by registering your application to receive push notifications, you can start calling methods of the APSCloudPush and APSPushNotifications classes.

### CloudPush sample application

The SDK includes the APSCloudPushExample application that demonstrates the use of the APSPushNotifications and APSCloudPush APIs. To run the sample application, you'll first need to create an Android application in Dashboard (or use an existing application) and configure its push notification settings to include a GCM or FCM sender ID and application key. APSCloudPush requires Google Play services, so you'll also need to add that library as a dependency to your project.

**To import and run the APSCloudPushExample application**:

1. In Eclipse, select **File** \> **Import** \> **General** \> **Existing Projects into Workspace** and click **Browse**.

2. Navigate to the **appcelerator-sdk-android-<VERSION>/examples/APSCloudPushExample** folder and click **Open**.

3. Click **Finish** to import the project.

4. Add the Google Play services to your project (see [Android Project Requirements](#android-project-requirements-for-using-apscloud-push) for instructions).

5. In MainActivity.java, locate the following line and replace **<< YOUR APP KEY >>** with the application key generated by Dashboard:

    `String appKey =` `"<< YOUR APP KEY >>"``;`

6. Run the application on an Android device or emulator.
