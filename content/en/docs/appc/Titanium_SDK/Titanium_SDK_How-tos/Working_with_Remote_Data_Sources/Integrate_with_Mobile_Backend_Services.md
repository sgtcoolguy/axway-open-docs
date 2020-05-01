{"title":"Integrate with Mobile Backend Services","weight":"70"}

* [Integrating Mobile Backend Services into your app](#integrating-mobile-backend-services-into-your-app)

    * [Step 1. Register Your App with API Builder](#step-1.-register-your-app-with-api-builder)

    * [Step 2. Configure your Titanium project](#step-2.-configure-your-titanium-project)

    * [Step 3. Authentication](#step-3.-authentication)

    * [Step 4. Implement the Titanium Mobile Backend Services APIs](#step-4.-implement-the-titanium-mobile-backend-services-apis)

    * [Step 5. Managing your app's data](#step-5.-managing-your-app's-data)

    * [Step 6. Sharing MBS Objects](#step-6.-sharing-mbs-objects)

* [References](#references)

## Objective

In this section, you will learn how to utilize the Mobile Backend Services (MBS) APIs for your mobile apps.

## Contents

Mobile Backend Services provide a wide array of automatically-scaled network features and data objects for your app. Tasks such as push notifications, user logins, photo uploads, checkins and status updates that usually require server programming or tedious integration with multiple SDKs are performed through one simple interface.

We worry about the database, file storage, search engine and application stack so that you can focus on what’s really important: your app and your users. As usage of your app increases, MBS scales up automatically to handle the load without requiring you to do any additional work. Photos and other files are redundantly stored on multiple devices across multiple storage facilities, preventing data corruption and loss.

Over 25 APIs are available for immediate use in your app to provide the most popular network features. Writing, testing, and deploying server code is a thing of the past. Focus on your users and app features.

{{% alert title="💡 ACS API support" color="info" %}}Note that when new APIs are added to MBS, they may not be immediately available in the Titanium Cloud module.
The since version listed after some APIs indicates the Titanium Mobile SDK release that included support for
that API. (Note that the Titanium Cloud module version is not always the same as the SDK version that it ships with.){{% /alert %}}

MBS is open to all app publishers, regardless of the development technology used to build the app – Titanium, Objective-C, Java, or HTML5 via frameworks like Sencha Touch or PhoneGap – we’ve got you covered. MBS provide a complete REST API along with iOS, Android and JavaScript SDKs. Any device that can make HTTP requests over the Internet can securely use MBS as its server backend.

### Integrating Mobile Backend Services into your app

To integrate MBS into your app, you'll need to follow these four general steps:

1. Register your app with API Builder

2. Configure your Titanium project to use Arrow

3. Authenticate your API calls to the Arrow Cloud infrastructure

4. Implement the Titanium MBS API calls within your app

You might want to add a fifth step to this list: Manage the data your app collects by using the MBS control panel or RESTful API.

#### Step 1. Register Your App with API Builder

Using MBS API to store and retrieve data for your app is easy.

* When creating a new application in Appcelerator Studio, make sure the **Enable Appcelerator Services** checkbox is enabled.

* For a previously created project, open your tiapp.xml file, then click the **Enable Services** button under the _Appcelerator Service_ section.

#### Step 2. Configure your Titanium project

MBS support is baked into Titanium. However, you must include the cloud services module into your project to use Arrow functionality. In your app.js (or other suitable file), include the require() statement as shown here:

```javascript
var Cloud = require('ti.cloud');
Cloud.debug = true;  // optional; if you add this line, set it to false for production
```

In order for the ti.cloud module to be recognized, ensure that the modules directive has been added to tiapp.xml.

```xml
<modules>
    <module platform="commonjs">ti.cloud</module>
</modules>
```

#### Step 3. Authentication

Your app must prove that it is allowed to talk to MBS. This keeps your data secure by preventing anyone from making requests to MBS that impersonate your app. In order to make MBS calls, add the Cloud App Key to your tiapp.xml file.

If you add MBS support to your application when you create it in Studio, Studio adds the authentication keys to your tiapp.xml file:

**tiapp.xml**

```xml
<property name="acs-api-key" type="string">ARROW_APP_KEY</property>
```

#### Step 4. Implement the Titanium Mobile Backend Services APIs

Add cloud services to your app using the MBS APIs. With over 25 APIs available for you to use, we obviously can't cover them all here. But let's take a look at a couple of examples.

**Create a user**

```javascript
// example assumes you have a set of text fields named username, password, etc.
Cloud.Users.create({
    username: username.value,
    password: password.value,
    password_confirmation: confirmPassword.value,
    first_name: firstName.value,
    last_name: lastName.value
}, function (e) {
    if (e.success) {
    // user created successfully
    } else {
        // oops, something went wrong
    }
});
```

**Post a photo**

```javascript
// assumes you've obtained a photo from the camera or gallery, with blob data stored in an object named photo
// collectionID is an ID generated by ArrowDB for a grouping of photos, you could retrieve via code or hard-code it
Cloud.Photos.create({
    photo: photo,
    collection_id: collectionID,
    'photo_sync_sizes[]': 'small_240'
}, function (e) {
    if (e.success) {
    // null out our photo objects to clean up memory
        photo = null;
        collectionID = null;
    } else {
        // oops, something went wrong
    }
});
```

**Linking a Facebook login with your app**

```javascript
// Not shown is the code to implement the Facebook module in your app

// call the ArrowDB Facebook SocialIntegrations API to link logged in states
function updateLoginStatus() {
    if (Facebook.loggedIn) {
        label.text = 'Logging in to ArrowDB as well, please wait...';
        Cloud.SocialIntegrations.externalAccountLogin({
            type: 'facebook',
            token: Facebook.accessToken
        }, function (e) {
            if (e.success) {
                var user = e.users[0];
                alert('Logged in! You are now logged in as ' + user.id);
            }
            else {
                error(e);
            }
        });
    }
    else {
        label.text = 'Please login to Facebook.';
    }
}

// when the user logs into or out of Facebook, link their login state with ArrowDB
Facebook.addEventListener('login', updateLoginStatus);
Facebook.addEventListener('logout', updateLoginStatus);

// add the Facebook login button
win.add(Facebook.createLoginButton({
    top: 10
}));
```

Of course, there are many more examples we could show. Instead, head on over to the API documentation to view the samples included there plus the full explanation of MBS APIs.

The Cloud module also includes a sample application demonstrating each of the MBS request types. You can find this in the modules folder under the Titanium SDK folder. For example:

```
/Library/Application Support/Titanium/modules/commonjs/ti.cloud/<version>/example
```

#### Step 5. Managing your app's data

Of course, there's no sense in collecting data if you don't use it. Data created by your app is stored within the Arrow cloud. You can view and manage this data through the Appcelerator Dashboard. You can also use the RESTful API (or any of the other APIs) to extract the data you need.

#### Step 6. Sharing MBS Objects

The Cloud module supports Access Control Lists (ACLs) to control access to ACL resources. An ACL lets you grant read and write access to users other than the owner of an MBS object. An access control list controls read and write access to any MBS objects it's attached to. For MBS, read and write permission are defined as follows:

* **Read permission**. Includes the ability to show, query and search MBS objects.

* **Write permission**. Includes the ability to update and delete MBS objects.

An ACL can include:

* A list of user IDs granted read permission.

* A list of user IDs granted write permission.

* A public read flag granting read permission to **all** users.

* A public write flag granting write permission to **all** users.

The object's owner always has read and write permission.

You can specify an ACL when you create or update an object.

Currently, ACLs can be used with the following MBS objects: Checkins, Custom Objects, Events, Files, Photos, Photo Collections, Places, Posts, Reviews and Statuses.

See [Ti.Cloud.ACLs](#!/api/Modules.Cloud.ACLs) for methods to create and update ACLs.

### References

* [Cloud Module Reference](#!/api/Modules.Cloud)

* [Mobile Backend Services Getting Started](/docs/appc/Mobile_Backend_Services/Mobile_Backend_Services_Getting_Started/)

## Summary

In this section, you briefly explored how to use the Mobile Backend Services APIs in your mobile apps.
