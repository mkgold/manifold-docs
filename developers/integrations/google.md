# Google OAuth Configuration

If this feature is enabled, Manifold will include a "Log in with Google" button on the login page. Clicking the button will open a popup that allows users to authenticate using their Google account. On successful authentication, Manifold will create a user record \(if it is the user's first time logging in\) and an associated identity record.

These instructions document the process for acquiring OAuth keys from Google. It's possible that their process has changed since this was written. If that's the case, please [open a pull request](https://github.com/ManifoldScholar/manifold-docs/pulls) against our documentation with a correction.

### Requirements

Before adding OAuth support for Google to Manifold, you will need a Google developer account and a Manifold Google project.

* If you do not have a developer account you can create one at through the [Google Developer Console](https://console.developers.google.com/).
* If you do not have a Manifold Google project you can create one by logging into your developer account and clicking "Create Project".

### Callback URL

The Manifold API handles OAuth callbacks. For Google, the callback route is located at `/auth/google/callback`. For your installation of Manifold, the callback URL will be the fully qualified domain name \(FQDN\) of the API server followed by that path. For example, my Manifold API is on the same domain as the client application, and that domain is `manifoldapp.org`, the callback URL would be `http://manifoldapp.org/auth/google/callback`. 

### Setup consent screen

1. Log into your account and app at [Google Developer Console](https://console.developers.google.com/).
2. From your Manifold project's API Manager, navigate to "Credentials" in the sidebar.
3. Click on the "OAuth consent screen" tab.
4. Select an email address in the dropdown.
5. Add a name to the "Product name shown to users" field.
6. Save the settings.

![Google Consent](/assets/google-consent.png)

### Create OAuth credentials

1. Click on the "Credentials" tab.
2. Click the button to "Create credentials" and select "OAuth client ID".
3. Select "Web application" for the "Application type".
4. Name the credential set.
5. In the "Authorized redirect URIs" field, add:

   ```
   [your-manifold-api-route]/auth/google_oauth2/callback
   ```

6. Click create.

![Google Credentials](/assets/google-credentials.png)

### Get App ID and Secret ID

1. Click on your new credential set under the "OAuth 2.0 client IDs" header.
2. Copy the values under "Client ID" and "Client Secret".

![Google Keys](/assets/google-keys.png)

### Add keys to .env file

Update your .env file with the new values:

```
export OAUTH_GO_ID={app id from your google project}
export OAUTH_GO_SECRET={app secret from your google project}
```



