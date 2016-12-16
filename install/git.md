<!-- TITLE: Git -->
<!-- SUBTITLE: Guide on connecting to various Git providers -->
![Git Logo](/uploads/page-icons/git-logo.png "Git Logo"){.pagelogo}
# What is Git
Git is a version control system (VCS) that is used mainly for software development and other version control tasks. As a distributed revision control system it is aimed at speed, data integrity, and support for distributed, non-linear workflows. In other words, it backups and keeps track of everything you add, modify or delete in a repository.
# Why do I need it?
Because the documentation you write should always be stored in a safe location. Even though databases and file storages can be configured to have backups, they are either costly or completely ineffective. Storing documents into a Git repository not only make sense, it's cost effective (free in most cases), fast and safe.

Having all your documentation in a central Git repository means you control 100% of your data at all times.
- Want to modify that content outside the Wiki? **You can**.
- Want to transfer content somewhere else? **You can**.
- You want to completely stop using Wiki.js? Hopefully not, but should you want to, **you can** and there's nothing to extract or backup because everything is already in that Git repository.
# Providers
There's quite an extensive list of Git providers, but we'll focus on the 4 major ones, which all offer free repository hosting.

## GitHub

Public: **Yes (free)**  
Private: **Paid only**
Supported authentication methods: **SSH and Basic**

https://github.com/

### Using SSH:

- From the **Settings** page, select **SSH Keys** in the sidebar.
- Click the **New SSH Key** button.
- Enter your **public key** content in the textbox. Learn how to [create a new SSH key](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/).
- Follow the instructions for SSH below.

### Using Basic:

- From the **Settings** page, select **Personal Access Tokens** in the sidebar.
- Click on **Generate New Token**.
- Enter a description for this token (e.g. Wiki.js) and enable the **repo** permissions.
- Follow the instructions for Basic below.

## GitLab

Public: **Yes (free)**  
Private: **Yes (free)**
Supported authentication methods: **SSH, OAuth and Basic**

https://gitlab.com/

## Bitbucket

Public: **Yes (free, up to 5 users)**  
Private: **Yes (free, up to 5 users)**
Supported authentication methods: **SSH, OAuth and Basic**

https://bitbucket.org/

## Visual Studio Team Services

Public: **No**  
Private: **Yes (free, up to 5 users)**
Supported authentication methods: **SSH and Basic**

https://visualstudio.com/

# Configure Wiki.js
Now that your repository is setup using the instructions above, it's time to enter the info in the configuration file. Different parameters are required depending on the authentication type:

## Common

Set the **sslVerify** parameter to `false` if the Git repository is using an SSL certificate that can't be verified by Wiki.js (e.g. self-signed or expired certificates). Setting it to false is obviously not recommended and a security risk.

The **signature** block is required and must be identical to the account info of your Git provider. For example, if using Github, you must put your name and email exactly as entered in your GitHub profile.

```yaml
git:
  url: https://server.com/org/repo
  branch: master
  auth:
	
    # Type: basic, oauth or ssh
    type: ssh
		
    # Username / Email
    username: marty@doc.com
		
    # Password, OAuth token or private key passphrase:
    password: MartyMcFly88
		
    # Only for SSH authentication:
    publicKey: /etc/wiki/keys/git-public.pem
    privateKey: /etc/wiki/keys/git-private.pem
		
    # Check for valid SSL certificate
    sslVerify: true
		
  signature:
    name: Marty
    email: marty@doc.com
```

## Using SSH

You must define the public (**publicKey**) and private key (**privateKey**) locations when using the SSH authentication method. If the private key is encrypted with a passphrase (which is recommended), put the passphrase in the **password** parameter. The username can be an email depending on the provider.

Example:
```yaml
git:
  url: https://server.com/org/repo
  branch: master
  auth:
    type: ssh
    username: marty@doc.com
    password: MartyMcFly88
    publicKey: /etc/wiki/keys/git-public.pem
    privateKey: /etc/wiki/keys/git-private.pem
  signature:
    name: Marty
    email: marty@doc.com
```

## Using OAuth

The OAuth token must be set in the **password** field.

Example:
```yaml
git:
  url: https://server.com/org/repo
  branch: master
  auth:
    type: oauth
    username: marty@doc.com
    password: abcdef1234567890abcdef1234567890
  signature:
    name: Marty
    email: marty@doc.com
```

## Using Basic (User/Pass)

Using a standard username / password combination. Make sure to use a long and strong password.

Example:
```yaml
git:
  url: https://server.com/org/repo
  branch: master
  auth:
    type: oauth
    username: marty@doc.com
    password: MartyMcFly88
  signature:
    name: Marty
    email: marty@doc.com
```
# Using an existing repository
You can use an existing repository (from an existing Wiki.js installation or any standard markdown-based documentation system), as long as the filenames match the requirements below. The existing content will be fetched during the first sync.
- All markdown files (.md) and folders are in lowercase (including the file extension).
- All markdown files (.md) and folders use the hyphen `-` to separate words. e.g. `sample-file-tutorial.md`

You can leave the `README.md` file as is; it will be ignored by Wiki.js.