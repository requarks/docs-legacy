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
The list of Git repository providers is actually quite long, but we'll focus on the 4 major ones, which all offer free repository hosting.

## GitHub

Public: **Yes (free)**  
Private: **Paid only**
Supported authentication methods: **SSL and Basic**

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
Supported authentication methods: **SSL, OAuth and Basic**

https://gitlab.com/

## Bitbucket

Public: **Yes (free, up to 5 users)**  
Private: **Yes (free, up to 5 users)**
Supported authentication methods: **SSL, OAuth and Basic**

https://bitbucket.org/

## Visual Studio Team Services

Public: **No**  
Private: **Yes (free, up to 5 users)**
Supported authentication methods: **SSL and Basic**

https://visualstudio.com/