<!-- TITLE: Authentication -->
<!-- SUBTITLE: How to setup authentication on your wiki. -->
![Wiki.js](/uploads/page-icons/logo.png "Logo"){.pagelogo}

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
6. From the sidebar menu, click **Credentials**.
7. Under the **OAuth consent screen** tab, **fill in** the required info and click **Save**.
8. Back to the **Credentials** tab, click on **Create credentials** > **OAuth client Id**.
9. Choose **Web Application** and enter a **name** (e.g. Wiki).
10. Under **Restrictions**, enter the **authorised origin domain** of your wiki (e.g. https://www.example.com) and the **authorised redirect URL** (full URL of your wiki followed by `/login/google/callback` as e.g.: `http://www.example.com/login/google/callback`)
11. Click **Create** and take note of both the generated **Client ID** and **Client Secret**.

Under the auth section of your config.yml, you can now enter the required info:


```yaml
google:
  enabled: true
  clientId: YOUR_CLIENT_ID
  clientSecret: YOUR_CLIENT_SECRET
```
# Facebook
The Facebook provider lets users login using their own Facebook account.

1. Go to https://developers.facebook.com
2. Choose 'Add a New App'
3. Your app id should be clearly visible on the top of the page. To get your app secret, go to the 'Dashboard' and click 'Show' next to the starred-out secret
4. You can now test logging in with your own account and users you explicitly give access. To open up logging in via your app to everyone, make your app 'public' under 'App Review'.

Under the auth section of your config.yml, you can now enter the required info:

```yaml
facebook:
  enabled: true
  clientId: YOUR_FACEBOOK_APP_ID
  clientSecret: YOUR_FACEBOOK_APP_SECRET
```

# GitHub
The GitHub provider lets users login using their own GitHub account.

1. Go to https://github.com/settings/applications/new
2. Enter an **Application Name** (e.g. Wiki).
3. Enter the **Homepage URL** to your wiki.
4. In the **Authorization Callback URL** field, enter the full URL of your wiki followed by `/login/github/callback` (e.g.: `http://www.example.com/login/github/callback`).
5. Click on **Register Application**.
6. Take note of both the generated **Client ID** and **Client Secret**.
7. (optional) Upload a logo for your application.

Under the auth section of your config.yml, you can now enter the required info:

```yaml
github:
	enabled: true
	clientId: GITHUB_CLIENT_ID
	clientSecret: GITHUB_CLIENT_SECRET
```

# Slack
The Slack provider lets users login using their own Slack account.

1. Go to https://api.slack.com/apps
2. Click on **Create an App**.
3. Enter a name under **App Name** (e.g. Wiki) and select a **Development Slack Team**.
4. Click on **Create App**.
5. In the left sidebar, navigate to **OAuth & Permissions**.
6. Under **Redirect URLs**, click **Add a New Redirect URL** and enter the full URL of your wiki followed by `/login/slack/callback` (e.g.: `http://www.example.com/login/slack/callback`).
7. Click **Add** and then **Save URLs**.
8. Under **Permissions**, add the following scopes: **identity.basic** and **identity.email**
9. **Save Changes** and navigate to **Basic Information** in the left sidebar.
10. Take note of the **Client ID** and **Client Secret** shown under **App Credentials**.
11. (optional) Upload a logo and customize the look and description of your app.

> :warning: Quote your slack client ID otherwise it will be treated as float instead as a string and this will cut it off.
{.is-warning}

Under the auth section of your config.yml, you can now enter the required info:

```yaml
slack:
	enabled: true
	clientId: SLACK_CLIENT_ID
	clientSecret: SLACK_CLIENT_SECRET
```

# LDAP (Active Directory)
The LDAP provider lets users login using their LDAP / Active Directory account.

This provider is only for classic LDAP / Active Directory systems, it is **not** compatible with Azure Active Directory. Use the **Azure Active Directory** provider instead (coming soon).

Under the auth section of your `config.yml`, enter the required info:

```yaml
ldap:
	enabled: true
	url: ldap://serverhost:389
	bindDn: cn='root'
	bindCredentials: BIND_PASSWORD
	searchBase: o=users,o=example.com
	searchFilter: (uid={{username}})
	tlsEnabled: false
	tlsCertPath: C:\example\root_ca_cert.crt
```

The `searchFilter` option has a variable `{{username}}` which contains the value entered by the user during login. You can use this variable however you want in your searchFilter expression.

For Active Directory, you should usually use the `samaccountname` in the `searchFilter`, e.g.: `(samaccountname={{username}})`

The user must have an email address associated with the account, or sign in will fail. This holds true regardless of `searchFilter` configuration.

# Azure Active Directory
The Azure AD provider lets users login using their Azure Active Directory (AAD) account.

This provider is only for Azure AD, it is **not** compatible with LDAP / classic Active Directory. Use the **LDAP (Active Directory)** provider instead.

1. Login to your [Azure AD Portal.](https://portal.azure.com)
2. Click on **Azure Active Directory**.
3. On the left menu bar, select **App Registrations**.
4. Create a new application integration with **New application registration**.
5. Name it something useful like *Wiki* and make sure the application type is *Web app / API*. 
6. Your *Sign-on URL* will be the full domain of your Wiki followed by `/login/azure/callback`.
	e.g `https://portal.example.com/login/azure/callback`
7. Click **Create**.
8. You will then see your application in the **App registrations** menu. Click on it.
9. The *Application ID* will be given to you. Add this to your `config.yml` as *clientId*.
10. A private app key will need to be generated now. Under **Settings** there will be a **Keys** option. Click on that. There should be no keys present. Write in a description for the key in **Key Description** and set a **Duration**. Something like *wiki_priv* and *Never expires* is fine. 
11. Click **Save**. Your private key will now be generated. Copy the key's value and add it to *clientSecret* in your `config.yml`. Be careful to note this down as this will be the only time that you see it. 
12. Make sure that in **Reply URLs** it contains your `https://portal.example.com/login/azure/callback` or the integration won't work. You must be using SSL on your Wiki site for Microsoft to allow the API integration. 
13. Check to make sure that correct permissions have been granted. Under the App Registration **Settings**, select the **Required Permissions** option. Select the *Windows Azure Active Directory* object. From here, make sure that *Sign in and read user profile* under **Delegated Permissions** is ticked.  
14. Your tenant ID is your `example.onmicrosoft.com`. Note: your regular domain `example.com` will not work here as it needs to be the Microsoft Azure AD name. Alternatively, you can find your tenant ID string via **Azure Active Directory** -> **Properties** -> **Directory ID**.

```yaml
azure:
	enabled: true
	clientId: YOUR_CLIENT_ID
	clientSecret: YOUR_CLIENT_SECRET
	resource: '00000002-0000-0000-c000-000000000000'
	tenant: YOUR_TENANT_ID_OR_AD_DOMAIN
```

Note: If you are receiving a *User Email Not Found* error from Wiki.js after trying to login with your Azure AD Credentials, this is a known bug and being worked on. The bug is described [here](https://github.com/Requarks/wiki/issues/307) and a solution is provided in the thread. 
