# Facebook OAuth Configuration

Configure this feature to allow users to log in with their Facebook accounts.

### Requirements

Before adding OAuth support for Facebook to Manifold, you will need a Manifold Facebook app.

* If you do not have one, create a Facebook app by following the steps in the [Facebook Developer Docs](https://developers.facebook.com/docs/apps/register#developer-account).

### Setup redirect URL

1. Log into your account and app at [Facebook Developers](https://developers.facebook.com).
2. Under the "Products" header in the sidebar, add a new product.
3. Click "Get Started" on the "Facebook Login" item.
4. In the "Valid OAuth redirect URIs" field, enter a URL in the form:

  ```
  [your-manifold-api-route]/auth/facebook/callback
  ```

![Facebook Redirect Settings](/assets/facebook-redirect.png)

### Get App ID and Secret ID

1. Navigate back to the dashboard from the sidebar.
2. Copy the values under "App ID" and "App Secret".

![Facebook Dashboard](/assets/developer-dashboard.png)

### Add keys to .env file

Update your .env file with the new values:

```
export OAUTH_FB_ID={app id from your facebook app}
export OAUTH_FB_SECRET={app secret from your facebook app}
```