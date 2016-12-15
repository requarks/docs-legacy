<!-- TITLE: Configuration File -->
<!-- SUBTITLE: List of all configuration settings -->
# General Site Settings

| Property            | Required | Description                                                                                                                          |   Default Value  |
|---------------------|:--------:|--------------------------------------------------------------------------------------------------------------------------------------|:----------------:|
| **title**           | yes | The title of the website. Displayed in the navigation bar. | Wiki |
| **host**            | yes | The full hostname of the site, as accessed by the user. Do not add a trailing slash. | http://localhost |
| **port**            | no  | The port on which the server should listen to. You can also use the environment variable process.env.PORT by omitting this property. | 80 |
| **paths.repo**      | yes | The path (absolute or relative to server.js) to the folder where markdown content will be synchronized with the Git repository. Make sure this folder has the necessary write permissions. Note that this folder will contain all uploads (images, documents, etc.), so make sure to allow enough disk space depending on your usage. | ./repo |
| **paths.data**      | yes | The path (absolute or relative to server.js) to the folder where temporary data will be stored (cache, thumbnails, search indexes, etc.). Make sure this folder has the necessary write permissions. | ./data |
| **lang**            | yes | The default language to use for the site UI. | en |

# Authentication

Wiki.js offers various authentication providers that you can enable. See the [authentication guide](authentication) to learn how to get the necessary info for each provider.

| Property            | Required | Description                                                                                                                          |   Default Value  |
|---------------------|:--------:|--------------------------------------------------------------------------------------------------------------------------------------|:----------------:|
| **public**          | yes      | Should the wiki be accessible publicly without a login. Set to false to require all users to login before accessing any wiki content. | false |
| **auth.local.enabled**          | no | Enable the local authentication provider. | true |
| **auth.google.enabled**         | no | Enable the Google authentication provider | false |
| **auth.google.clientId**        | no | Google client ID that uniquely identify your app. | |
| **auth.google.clientSecret**    | no | Google client secret for your app. | |
| **auth.microsoft.enabled**      | no | Enable the Microsoft account authentication provider. | false |
| **auth.microsoft.clientId**     | no | Microsoft account client ID that uniquely identify your app. | |
| **auth.microsoft.clientSecret** | no | Microsoft account client secret for your app. | |
| **auth.facebook.enabled**       | no | Enable the Facebook authentication provider | false |
| **auth.facebook.clientId**      | no | Facebook client ID that uniquely identify your app. | |
| **auth.facebook.clientSecret**  | no | Facebook client secret for your app. | |
| **sessionSecret**   | yes | A randomly generated string, used when encrypting sessions. 256-bit keys are usually a good choice. You can use this [key generator](http://randomkeygen.com/) to generate one. | |
| **admin**           | yes | The site administrator email address. An admin account will be created in the local database using this email. The default password is `admin123`. :warning: Change it immediately upon login, even if you don't use local authentication! | |

# Database

| Property            | Required | Description                                                                                                                          |   Default Value  |
|---------------------|:--------:|--------------------------------------------------------------------------------------------------------------------------------------|:----------------:|
| **db**                    | yes | The MongoDB-formatted [connection string](db). | |

# Git Repository

Wiki.js works with pretty much any Git repository. See the [Git repository guide](git) to learn how to get the necessary info from the most popular providers.

| Property            | Required | Description                                                                                                                          |   Default Value  |
|---------------------|:--------:|--------------------------------------------------------------------------------------------------------------------------------------|:----------------:|
| **git.url**               | yes | The full URL to your Git repository where all content will be synced. | |
| **git.branch**            | yes | The branch of your Git repository to sync. | master |
| **git.auth.type**         | yes | The type of authentication to use when connecting to your Git repository. Valid values: `basic`, `oauth` or `ssh` | basic |
| **git.auth.username**     | no  | The username to use when authenticating with your Git repository | |
| **git.auth.password**     | no  | The password (basic), the OAuth token (oauth) or the private key passphrase (ssh) to use when authenticating with your Git repository | |
| **git.auth.publicKey**    | no  | *(ssh only)* The full path to the public key (.pem) to use when authenticating with your Git repository | |
| **git.auth.privateKey**   | no  | *(ssh only)* The full path to the private key (.pem) to use when authenticating with your Git repository | |
| **git.auth.sslVerify**    | no  | *(ssh only)* Should the server check for a valid SSL certificate when connecting to your Git repository. | true |
| **git.signature .name**   | yes | The name to use as the author when pushing changes to your Git repository. | |
| **git.signature.email**   | yes | The email address to use as the author when pushing changes to your Git repository. | |