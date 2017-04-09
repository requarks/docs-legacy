<!-- TITLE: Git -->
<!-- SUBTITLE: Guide on connecting to various Git providers -->
![Git Logo](/uploads/page-icons/git-logo.png "Git Logo"){.pagelogo}
# What is Git
Git is a version control system (VCS) that is used mainly for software development and other version control tasks. As a distributed revision control system it is aimed at speed, data integrity, and support for distributed, non-linear workflows. In other words, it backups and keeps track of everything you add, modify or delete in a repository.
# Why do I need it?
Because the documentation you write should always be stored in a safe location. Even though databases and file storages can be configured to have backups, they are either costly or completely ineffective. Storing documents into a Git repository not only make sense, it's cost effective (free in most cases), fast and safe.

Having all your documentation in a central Git repository means you control 100% of your data at all times.
- Want to modify content outside the Wiki? **You can**.
- Want to transfer content somewhere else? **You can**.
- You want to completely stop using Wiki.js? Hopefully not, but should you want to, **you can** and there's nothing to extract or backup because everything is already in that Git repository.
# Providers
There's quite an extensive list of Git providers, but we'll focus on the 4 major ones, which all offer free repository hosting.

## GitHub

Public: **Yes (free)**  
Private: **Paid only**  
Supported authentication methods: **SSH and Basic**

https://github.com/

### Using SSH (Repository):

:white_check_mark: This method gives access only to the repository, which is the recommended way.

- From the repository **Settings** page, select **Deploy Keys** in the sidebar.
- Click the **Add deploy key** button.
- Enter a **title** for the key (e.g. Wiki.js).
- Enter your **public key** content in the textbox. Learn how to [create a new SSH key](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/).
- Check the box [x] **Allow write access**.
- **Save** the key.
- Follow the instructions for SSH below.

### Using SSH (Global):

:warning: This method gives access to all repository owned by the account. Do not use unless you know what you're doing!

- From the user dropdown menu, click **Settings** and select **SSH and GPG Keys** in the sidebar.
- Click the **New SSH Key** button.
- Enter a **title** for the key (e.g. Wiki.js).
- Enter your **public key** content in the textbox. Learn how to [create a new SSH key](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/).
- **Save** the key.
- Follow the instructions for SSH below.

### Using Basic:

- From the **Settings** page, select **Personal Access Tokens** in the sidebar.
- Click on **Generate New Token**.
- Enter a description for this token (e.g. Wiki.js) and enable the **repo** permissions.
- Follow the instructions for Basic below.

## GitLab

Public: **Yes (free)**  
Private: **Yes (free)**  
Supported authentication methods: **SSH and Basic**

https://gitlab.com/

### Using SSH (Repository):

:white_check_mark: This method gives access only to the repository, which is the recommended way.

- From the a project page, select **Deploy Keys** from the Settings dropdown menu.
- Enter a **title** for the key (e.g. Wiki.js).
- Enter your **public key** content in the textbox. Learn how to [create a new SSH key](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/).
- Check the box [x] **Write access allowed**.
- **Save** the key.
- Follow the instructions for SSH below.

### Using SSH (Global):

:warning: This method gives access to all repository owned by the account. Do not use unless you know what you're doing!

- From the user dropdown menu, click **Settings** and select **SSH Keys** from the top menu.
- Enter your **public key** content in the textbox. Learn how to [create a new SSH key](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/).
- Enter a **title** for the key (e.g. Wiki.js).
- **Save** the key.
- Follow the instructions for SSH below.

### Using Basic:

- From the **Settings** page, select **Access Tokens** from the top menu.
- Enter a **name** and **expiration** for this token (e.g. Wiki.js) and enable all permission scopes.
- **Save** the token.
- Follow the instructions for Basic below.

## Bitbucket

Public: **Yes (free, up to 5 users)**  
Private: **Yes (free, up to 5 users)**  
Supported authentication methods: **SSH and Basic**

https://bitbucket.org/

## Visual Studio Team Services

Public: **No**  
Private: **Yes (free, up to 5 users)**  
Supported authentication methods: **SSH and Basic**

https://visualstudio.com/

### Using SSH:

- From User dropdown menu, select **Security**.
- Click on **SSH Public Keys** from the left sidebar.
- Click on the **Add** button.
- Enter a **title** for the key (e.g. Wiki.js).
- Enter your **public key** content in the textbox. Learn how to [create a new SSH key](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/).
- **Save** the key.
- Follow the instructions for SSH below.

### Using Basic (Personal Access Tokens):

- From User dropdown menu, select **Security**.
- Click on **Personal Access Tokens** from the left sidebar.
- Click on the **Add** button.
- Enter a **description** for the key (e.g. Wiki.js) and set the desired **expiration date**.
- Check [x] the follow authorized scopes: **Code (read, write and manage)** and **Code (status)**.
- **Create** the token.
- Follow the instructions for Basic below.

### Using Basic (Alternate Credentials):

- From User dropdown menu, select **Security**.
- Click on **Personal Authentication Credentials** from the left sidebar.
- Check [x] the **Enable alternate authentication credentials** checkbox.
- Enter a **username** and **password**.
- **Save** the login.
- Follow the instructions for Basic below.
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
	
    # Type: basic or ssh
    type: ssh
		
    # Only for Basic authentication:
    username: marty@doc.com
    password: MartyMcFly88
		
    # Only for SSH authentication:
    privateKey: /etc/wiki/keys/git-private.pem
		
    # Check for valid SSL certificate
    sslVerify: true
		
  signature:
    name: Marty
    email: marty@doc.com
```

## Using SSH

You must define private key (**privateKey**) location when using the SSH authentication method. The private key must **NOT** be protected by a passphrase. If you want to a passphrase, you must configure your ssh-agent to handle it. Wiki.js will use the standard ssh executable installed on your system.

Example:
```yaml
git:
  url: git@server.com:org/repo.git
  branch: master
  auth:
    type: ssh
    privateKey: /etc/wiki/keys/git-private.pem
    sslVerify: true
  signature:
    name: Marty
    email: marty@doc.com
```

## Using Basic (User/Pass or Token)

Using a standard username and password/token combination. Make sure to use a long and strong password.

Example:
```yaml
git:
  url: https://server.com/org/repo
  branch: master
  auth:
    type: basic
    username: marty@doc.com
    password: MartyMcFly88
    sslVerify: true
  signature:
    name: Marty
    email: marty@doc.com
```
# Using an existing repository
You can use an existing repository (from an existing Wiki.js installation or any standard markdown-based documentation system), as long as the filenames match the requirements below. The existing content will be fetched during the first sync.
- All markdown files (.md) and folders are in lowercase (including the file extension).
- All markdown files (.md) and folders use the hyphen `-` to separate words. e.g. `sample-file-tutorial.md`

You can leave the `README.md` file as is; it will be ignored by Wiki.js.

# Disable remote sync
It is **highly recommended** to have remote sync enabled for backups and changes tracking purposes. It can however be disabled should you want to by setting `git: false` in your `config.yml` file:


```yaml
# Remote sync disabled:

git: false

# Remote sync enabled:

git:
  url: https://github.com/Organization/Repo
  branch: master
  auth:
    type: ssh
    privateKey: /etc/wiki/keys/git.pem
    sslVerify: true
  signature:
    name: Marty
    email: marty@example.com
```
