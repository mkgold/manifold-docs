# Twitter OAuth Configuration

Configure this feature to allow users to log in with their Twitter accounts.

### Requirements

Before adding OAuth support for Twitter to Manifold, you will need a Manifold Twitter app.

* If you do not have one, create a Twitter app through the [Twitter App Interface](https://apps.twitter.com).

### Setup required URLs

1. Log into your account and app at [Twitter Apps](https://apps.twitter.com).
2. Navigate to the "Settings" tab.
3. In the "Callback URL" field, enter a URL in the form:

  ```
  [your-manifold-api-route]/auth/twitter/callback
  ```
4. In the Privacy Policy field, add:

  ```
  this-doesnt.exist/yet
  ```
5. In the Terms of Service field, add:

  ```
  this-doesnt.exist/yet
  ```
6. Save the settings.

![Twitter URLs](/assets/twitter-urls.png)

### Add permission settings

1. Navigate to the "Permissions" tab.
2. Change your app's Access Level to "Read Only".
3. Check the box to "Request email addresses from users".

![Twitter Permissions](/assets/twitter-access.png)

### Get App ID and Secret ID

1. Navigate to the "Keys and Access Tokens" tab.
2. Copy the values under "Consumer Key (API Key)" and "Consumer Secret (API Secret)".

![Twitter Settings](/assets/twitter-settings.png)

### Add keys to .env file

Update your .env file with the new values:

```
export OAUTH_TW_ID={api key from your twitter app}
export OAUTH_TW_SECRET={api secret from your twitter app}
```