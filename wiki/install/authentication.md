<!-- TITLE: Authentication -->
<!-- SUBTITLE: How to setup authentication on your wiki. -->

Wiki.js supports multiple authentication providers. You may choose to enable one, some or even all of them.

> :warning: You must have at least 1 provider enabled as edits can only be performed while authenticated.
{.is-warning}
# Local
The local provider stores user accounts in the wiki database. It does not rely on any 3rd party service and accounts are unique to your wiki.

This is the most simple solution and **is enabled by default**.
# Microsoft Account
The Microsoft Account provider lets users login using their own Microsoft account.

1. Go to https://account.live.com/developers/applications/index
2. **Create** a new application (e.g. Wiki).
3. Under **Properties**, take note of the generated **Application Id**.
4. Under **Application Secrets**, click on **Generate New Password**. Take note of the provided password! It will not be shown again.
5. Under **Platforms**, click on **Add Platform**. Choose **Web**.
6. A **Redirect URIs** field just appeared. Enter the **full URL** of your wiki followed by `/login/ms/callback` as e.g.: `https://www.example.com/login/ms/callback`
7. Under **Microsoft Graph** > **Delegated Permissions**, click **Add**.
8. Find entry **User.ReadBasic.All** and **check** it, then click **Ok**. You should now have both **User.Read** and **User.ReadBasic.All** listed.
9. *(optional)* Add a logo, terms of service and privacy statement URLs if needed.
10. Click **Save**.

Under the auth section of your config.yml, you can now enter the required info:


```yaml
microsoft:
  enabled: true
  clientId: YOUR_APPLICATION_ID
  clientSecret: YOUR_APPLICATION_PASSWORD
```

# Google ID
The Google ID provider lets users login using their own Google ID.

1. Go to https://console.cloud.google.com/
2. **Create** a new Project (e.g. Wiki).
3. From the sidebar menu, click **API Manager**.
4. Click on the **Enable API** button.
5. Enable the **Google+ API**.
5. From the sidebar menu, click **Credentials**.
4. Under the **OAuth consent screen** tab, **fill in** the required info and click **Save**.
5. Back to the **Credentials** tab, click on **Create credentials** > **OAuth client Id**.
6. Choose **Web Application** and enter a **name** (e.g. Wiki).
7. Under **Restrictions**, enter the **authorised origin domain** of your wiki (e.g. https://www.example.com) and the **authorised redirect URL** (full URL of your wiki followed by `/login/google/callback` as e.g.: `http://www.example.com/login/google/callback`)
8. Click **Create** and take note of both the generated **Client ID** and **Client Secret**.

Under the auth section of your config.yml, you can now enter the required info:


```yaml
google:
  enabled: true
  clientId: YOUR_CLIENT_ID
  clientSecret: YOUR_CLIENT_SECRET
```
# Facebook
The Facebook provider lets users login using their own Facebook login.

*Documentation coming soon*