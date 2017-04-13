# Facebook OAuth Configuration

If this feature is enabled, Manifold will include a "Log in with Facebook" button on the login page. Clicking the button will open a popup that allows users to authenticate using their Facebook account. On successful authentication, Manifold will create a user record \(if it is the user's first time logging in\) and an associated identity record.

These instructions document the process for acquiring OAuth keys from Facebook. It's possible that their process has changed since this was written. If that's the case, please [open a pull request](https://github.com/ManifoldScholar/manifold-docs/pulls) against our documentation with a correction.

### Requirements

Before adding OAuth support for Facebook to Manifold, you will need a Facebook account, which will allow you to create a Manifold Facebook app.

* If you do not have one, create a Facebook app by following the steps in the [Facebook Developer Docs](https://developers.facebook.com/docs/apps/register#developer-account).

### Setup redirect URL

1. Log into your account and app at [Facebook Developers](https://developers.facebook.com).
2. Under the "Products" header in the sidebar, add a new product.
3. Click "Get Started" on the "Facebook Login" item.
4. In the "Valid OAuth redirect URIs" field, enter a URL in the form of `[your-manifold-api-route]/auth/facebook/callback`

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



