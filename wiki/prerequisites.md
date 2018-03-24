<!-- TITLE: Prerequisites -->
<!-- SUBTITLE: Requirements to run Wiki.js -->
![Wiki.js](/uploads/page-icons/logo.png "Logo"){.pagelogo}

Wiki.js is cross-platform (Windows, Linux and Mac) and does not depend on any paid commercial product / service.

# Server

Wiki.js runs on pretty much any platform that supports the requirements below. However, the following environments are recommended and more thoroughly tested:

- Ubuntu Server 16.04 LTS
- Windows Server 2012 R2

**CPU:** Runs perfectly fine on a single CPU core machine. However, to maximize Wiki.js background agent feature, using 2 cores is highly recommended.

**RAM:** Wiki.js uses between 100-200MB of RAM. While Wiki.js itself is able to run with only 512MB total system RAM, it highly recommended to use a machine with at least 1GB of RAM. Note that Windows machines may require more RAM than their linux counterparts.

**Disk Space:** Wiki.js requires about 300MB of disk space when including the dependencies. The actual total space needed for your installation depends on the content and most importantly, the uploads. A wiki with only text content will only use a few megabytes, even for thousands of articles. However, if you start adding images, documents, videos, etc., you must plan required disk space accordingly.

## Recommended cloud providers
- [DigitalOcean](https://m.do.co/c/5f7445bfa4d0)
- [Vultr](https://www.vultr.com/?ref=7175356)

# Software
## Node.js

Node.js is a JavaScript runtime built on Chrome's V8 JavaScript engine. Node.js uses an event-driven, non-blocking I/O model that makes it lightweight and efficient.

:information_source: **Node.js** `6.11.1` **or later is required.**

- [Official Website](https://nodejs.org/)
- [Installation using the package manager (Linux)](https://nodejs.org/en/download/package-manager/)

> :globe_with_meridians: **Web Server**
>
> Wiki.js (or any HTTP Node.js app) can run without any actual web server (such as nginx or Apache).  
> However, it is highly recommended to put a standard web server in front of Wiki.js. This ensures you can use features like SSL, multiple websites, caching, etc.
{.is-info}

## MongoDB
MongoDB is a free and open-source cross-platform document-oriented database program. Classified as a NoSQL database program, MongoDB uses JSON-like documents with schemas.

:information_source: **MongoDB** `3.2` **or later is required.**

- [Official Website](https://www.mongodb.com/)
- [Installation Guide](https://docs.mongodb.com/manual/administration/install-community/)

Read the [Database Guide](/wiki/install/database) for more information.

## Git

:information_source: **Git** `2.7.4` **or later is required.** There is a bug in earlier versions causing the remote sync to fail during initialization.

Even though Linux usually comes with Git pre-installed, it is most likely an outdated version. You can verify the currently installed version by running `git --version`

You can download the [latest version](https://git-scm.com/downloads) from the official Git website.

## An empty Git repository (optional)

All content created in the Wiki is saved locally and synced regularly to a remote Git repository.  
Any Git repository will do, as long as the Wiki can connect to it using **basic** or **ssh** authentication.

While not recommended, it is possible to use Wiki.js in a complete offline mode with no remote sync.

Read the [Git Repository Guide](/wiki/install/git) for more information.

# End User Requirements
The following modern browsers are supported:

- Google Chrome
- Mozilla Firefox
- Microsoft Edge
- Microsoft Internet Explorer 11
- Apple Safari
- Opera

> :no_entry_sign: **Unsupported Browsers**
> 
> - For evergreen browsers listed above (aka auto-updating browsers), only the latest version is supported.
> - Internet Explorer 10 and below are not supported. Wiki.js makes heavy use of the latest HTML / CSS / JS standards, which simply doesn't work in these browsers. They are also deprecated and no longer supported by Microsoft.
{.is-danger}