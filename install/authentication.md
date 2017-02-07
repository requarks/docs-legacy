<!-- TITLE: Authentication -->
<!-- SUBTITLE: How to setup authentication on your wiki. -->

Wiki.js supports multiple authentication providers. You may choose to enable one, some or even all of them.

> :warning: You must have at least 1 provider enabled as edits can only be performed while authenticated.
{.is-warning}
# Local
The local provider stores user accounts in the wiki database. It does not rely on any 3rd party service and accounts are unique to your wiki.

This is the most simple solution and is enabled by default.
# Microsoft Account
The Microsoft Account provider lets users login using their own Microsoft account.

1. Go to https://account.live.com/developers/applications/index
2. **Create** a new application and name it `Wiki` (can be anything).
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

*Documentation coming soon*
# Facebook
The Facebook provider lets users login using their own Facebook login.

*Documentation coming soon*