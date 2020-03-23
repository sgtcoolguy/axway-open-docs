{"title":"Preventing Man-in-the-middle Attacks for AMPLIFY Runtime Services API Calls","weight":"40"}

This info only applies to users who intend to do API calls to AMPLIFY Runtime Services (API Runtime Services) while using the HTTPS module.

You only need to generate your certificate if you are using the HTTPS module and NOT the ti.cloud modules.

{{% alert title="⚠️ Warning" color="primary" %}}You will need the HTTPS module and the ti.cloud module to test this sample app.{{% /alert %}}

```javascript
var Cloud = require('ti.cloud');
var win = Ti.UI.createWindow({
  backgroundColor: 'white'
});

Cloud.createX509CertificatePinningSecurityManager([
    {
        url: "https://api.cloud.appcelerator.com",
        serverCertificate: "api.cloud.appcelerator.com.der"
    }
]);

var btn = Ti.UI.createButton({
  title: 'Login User in Ti.Cloud',
  top: '50%'
});

btn.addEventListener('click', function(e) {
//any Cloud calls here will do
  Cloud.Users.login({
      login: 'test@mycompany.com',
      password: 'test_password'
  }, function (e) {
      if (e.success) {
          var user = e.users[0];
          alert('Success:\n' +
              'id: ' + user.id + '\n' +
              'sessionId: ' + Cloud.sessionId + '\n' +
              'first name: ' + user.first_name + '\n' +
              'last name: ' + user.last_name);
      } else {
          alert('Error:\n' +
              ((e.error && e.message) || JSON.stringify(e)));
      }
  });
});
win.add(btn);
win.open();
```

## Steps to test

1. Create a **new Classic app**.

2. **Enable cloud services** and include both **ti.cloud** and **https modules**.

3. Include the attached .der certificate in the **Resources** directory.

4. Build and run.

5. Click **btn**.

When testing the HTTP client connecting to the https site at this point, you should get an error message saying that no user or password was found, which is what is expected to report if everything was set up properly.
