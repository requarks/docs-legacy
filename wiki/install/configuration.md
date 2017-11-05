<!-- TITLE: Configuration File -->
<!-- SUBTITLE: List of all configuration settings -->
![Wiki.js](/uploads/page-icons/logo.png "Logo"){.pagelogo}

The configuration file is automatically generated for you during the Configuration Wizard.  
You may however change settings or additional options not shown during the wizard, based on the list below.

The configuration file is located at the root, named `config.yml`. Environment variables can be used to set property values with the syntax `$(ENV_VAR_NAME)`. **Note that any changes will not be applied until Wiki.js is restarted**.

# General Site Settings

| Property            | Required | Description                                                                                                                          |   Default Value  |
|---------------------|:--------:|--------------------------------------------------------------------------------------------------------------------------------------|:----------------:|
| **title**           | yes | The title of the website. Displayed in the navigation bar. | Wiki |
| **host**            | yes | The full hostname of the site, as accessed by the user. Do not add a trailing slash. You must add the port if you expect users to access your wiki via a non-standard port. | http://localhost |
| **port**            | no  | The port on which the server should listen to. You can also use the environment variable PORT using $(PORT). | 80 |
| **paths.repo**      | yes | The path (absolute or relative to server.js) to the folder where markdown content will be synchronized with the Git repository. Make sure this folder has the necessary write permissions. Note that this folder will contain all uploads (images, documents, etc.), so make sure to allow enough disk space depending on your usage. | ./repo |
| **paths.data**      | yes | The path (absolute or relative to server.js) to the folder where temporary data will be stored (cache, thumbnails, search indexes, etc.). Make sure this folder has the necessary write permissions. | ./data |
| **lang**            | yes | The default language to use for the site UI. Possible values: `en`,  `es`, `fr`, `ko`, `pt`, `ru` or `zh` | en |

# Authentication

Wiki.js offers various authentication providers that you can enable. See the [authentication guide](/wiki/install/authentication) to learn how to get the necessary info for each provider.

| Property            | Required | Description                                                                                                                          |   Default Value  |
|---------------------|:--------:|--------------------------------------------------------------------------------------------------------------------------------------|:----------------:|
| **public**          | yes      | Should the wiki be accessible publicly without a login. If set to true, creates a Guest user whose access can be configured in the Users Settings. Set to false to require all users to login before accessing any wiki content. | false |
| **defaultReadAccess**          | yes      | Should users that logged in using a social authentication provider have read-only access by default. | false |
| **auth.local.enabled**          | no | Enable the local authentication provider. | true |
| **auth.google.enabled**         | no | Enable the Google authentication provider | false |
| **auth.google.clientId**        | no | Google client ID that uniquely identify your app. | |
| **auth.google.clientSecret**    | no | Google client secret for your app. | |
| **auth.microsoft.enabled**      | no | Enable the Microsoft account authentication provider. | false |
| **auth.microsoft.clientId**     | no | Microsoft account client ID that uniquely identify your app. | |
| **auth.microsoft.clientSecret** | no | Microsoft account client secret for your app. | |
| **auth.facebook.enabled**       | no | Enable the Facebook authentication provider. | false |
| **auth.facebook.clientId**      | no | Facebook client ID that uniquely identify your app. | |
| **auth.facebook.clientSecret**  | no | Facebook client secret for your app. | |
| **auth.github.enabled**       | no | Enable the GitHub authentication provider. | false |
| **auth.github.clientId**      | no | GitHub client ID that uniquely identify your app. | |
| **auth.github.clientSecret**  | no | GitHub client secret for your app. | |
| **auth.slack.enabled**       | no | Enable the Slack authentication provider. | false |
| **auth.slack.clientId**      | no | Facebook Slack ID that uniquely identify your app. | |
| **auth.slack.clientSecret**  | no | Facebook Slack secret for your app. | |
| **auth.ldap.enabled**       | no | Enable the LDAP / Active Directory authentication provider. | false |
| **auth.ldap.url**      | no | The URL of the LDAP / AD server. | |
| **auth.ldap.bindDn**  | no | The security object to use when connecting to the LDAP server, e.g. cn='root' | |
| **auth.ldap.bindCredentials**  | no | The password to use when connecting to the LDAP server. | |
| **auth.ldap.searchBase**  | no | The base LDAP directory where authentication should look for users. | |
| **auth.ldap.searchFilter**  | no | The expression to use when matching the username. Use `{{username}}` to specify the username provided by the user during login. | |
| **auth.ldap.tlsEnabled**  | no | Should TLS encryption be used when connecting to the LDAP server. | |
| **auth.ldap.tlsCertPath**  | no | The full local path to a certificate used to authenticate with the LDAP server. | |
| **auth.azure.enabled**       | no | Enable the Azure AD authentication provider. | false |
| **auth.azure.clientId**      | no | Azure AD ID that uniquely identify your app. | |
| **auth.azure.clientSecret**  | no | Azure AD secret for your app. | |
| **auth.azure.resource**      | no | Resource GUID used during authentication. | 00000002-0000-0000-c000-000000000000 |
| **auth.azure.tenant**  | no | Azure AD tenant hostname. Usually `SOMETHING.onmicrosoft.com` | |
| **sessionSecret**   | yes | A randomly generated string, used when encrypting sessions. 256-bit keys are usually a good choice. You can use this [key generator](http://randomkeygen.com/) to generate one. | |

# Database

| Property            | Required | Description                                                                                                                          |   Default Value  |
|---------------------|:--------:|--------------------------------------------------------------------------------------------------------------------------------------|:----------------:|
| **db**                    | yes | The MongoDB-formatted [connection string](/wiki/install/database). | |

# Git Repository
Wiki.js works with pretty much any Git repository. See the [Git repository guide](/wiki/install/git) to learn how to get the necessary info from the most popular providers.

| Property            | Required | Description                                                                                                                          |   Default Value  |
|---------------------|:--------:|--------------------------------------------------------------------------------------------------------------------------------------|:----------------:|
| **git.url**               | yes | The full URL to your Git repository where all content will be synced. | |
| **git.branch**            | yes | The branch of your Git repository to sync. | master |
| **git.auth.type**         | yes | The type of authentication to use when connecting to your Git repository. Valid values: `basic` or `ssh` | basic |
| **git.auth.username**     | no  | The username to use when authenticating with your Git repository | |
| **git.auth.password**     | no  | The password (basic), the OAuth token (oauth) or the private key passphrase (ssh) to use when authenticating with your Git repository | |
| **git.auth.privateKey**   | no  | *(ssh only)* The full path to the private key (.pem) to use when authenticating with your Git repository | |
| **git.auth.sslVerify**    | no  | *(ssh only)* Should the server check for a valid SSL certificate when connecting to your Git repository. | true |
| **git.serverEmail**    | yes | The default/fallback email address to use as the author when committing changes to your Git repository. | |
| **git.showUserEmail**   | yes | Should the commit author email be set to the current user. | true |

# Features
You can enable / disable specific optional features.

| Property            | Required | Description                                                                                                                          |   Default Value  |
|---------------------|:--------:|--------------------------------------------------------------------------------------------------------------------------------------|:----------------:|
| **features.mathjax**  | no      | Enable math equations processing (in TeX and MathML formats) and display them as SVG graphics. | true |
# Logging
By default, all logs are stored locally in the `/logs` directory. You can send logs to additional remote logging services:

| Property            | Required | Description                                                                                                                          |   Default Value  |
|---------------------|:--------:|--------------------------------------------------------------------------------------------------------------------------------------|:----------------:|
| **externalLogging.bugsnag**               | no | Key to use for Bugsnag | |
| **externalLogging.loggly.token**            | no | Token to use for Loggly |  |
| **externalLogging.loggly.subdomain**            | no | Subdomain to use for Loggly |  |
| **externalLogging.papertrail.host**            | no | Host to use for Papertrail |  |
| **externalLogging.papertrail.port**            | no | Port to use for Papertrail |  |
| **externalLogging.rollbar**               | no | Key to use for Rollbar | |
| **externalLogging.sentry**               | no | Key to use for Sentry | |
