# Google OAuth Configuration

Configure this feature to allow users to log in with their Gmail accounts.

### Requirements

Before adding OAuth support for Google to Manifold, you will need a Google developer account and a Manifold Google project.

* If you do not have a developer account you can create one at through the [Google Developer Console](https://console.developers.google.com/).
* If you do not have a Manifold Google project you can create one by logging into your developer account and clicking "Create Project".

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



