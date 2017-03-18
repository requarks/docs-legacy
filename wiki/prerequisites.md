<!-- TITLE: Prerequisites -->
<!-- SUBTITLE: Requirements to run Wiki.js -->
![Prerequisites](/uploads/page-icons/prerequisites.png "Prerequisites"){.pagelogo}

Wiki.js is cross-platform (Windows, Linux and Mac) and does not depend on any paid commercial product / service.

# System

Wiki.js runs on pretty much any platform that supports the requirements below. However, the following environments are recommended and more thoroughly tested:

- Ubuntu Server 14.04 LTS / 16.04 LTS
- Windows Server 2012 R2

**CPU:** Runs perfectly fine on a single CPU core machine. However, to maximize Wiki.js background agent feature, using 2 cores is highly recommended.

**RAM:** Wiki.js uses between 100-200MB of RAM. While Wiki.js itself is able to run with only 512MB total RAM, you will not be able to install and compile the dependencies. You need a minimum of 1GB just to install the dependencies. Note that Windows machines may require more RAM.

**Disk Space:** Wiki.js requires about 300MB of disk space when including the dependencies. The actual total space needed for your installation depends on the content and most importantly, the uploads. A wiki with only text content will only use a few megabytes, even for thousands of articles. However, if you start adding images, documents, videos, etc., you must plan required disk space accordingly.

# Software
## Node.js

Node.js is a JavaScript runtime built on Chrome's V8 JavaScript engine. Node.js uses an event-driven, non-blocking I/O model that makes it lightweight and efficient.

:information_source: **Node.js** `4.6.0` **or later is required.**

- [Official Website](https://nodejs.org/)
- [Installation using the package manager (Linux)](https://nodejs.org/en/download/package-manager/)

> :globe_with_meridians: **Web Server**
>
> Wiki.js (or any HTTP Node.js app) can run without any actual web server (such as nginx or Apache).  
> However, it is highly recommended to put a standard web server in front of Wiki.js. This ensures you can use features like SSL, multiple websites, caching, etc.
{.is-info}

## Node.js native compilation support

Your system must be able to compile native Node.js addons in order to successfully install Wiki.js dependencies:

- On **Ubuntu/Debian Linux**: `sudo apt-get install -y build-essential python2.7 python-pip && npm install -g node-gyp`
- On **RedHat/CentOS/Fedora Linux**: `yum install gcc-c++ make && npm install -g node-gyp` *(You must also install Python 2.7 manually)*
- On **Windows**: From an elevated command prompt: `npm install -g windows-build-tools node-gyp`
- On **macOS**: Install the `Command Line Tools` via Xcode *(Xcode -> Preferences -> Downloads)*. Then run command `npm install -g node-gyp`

More info can be found on [node-gyp](https://github.com/nodejs/node-gyp#installation) project page, should you want to review and install the dependencies yourself.

## MongoDB
MongoDB is a free and open-source cross-platform document-oriented database program. Classified as a NoSQL database program, MongoDB uses JSON-like documents with schemas.

:information_source: **MongoDB** `3.2` **or later is required.**

- [Official Website](https://www.mongodb.com/)
- [Installation Guide](https://docs.mongodb.com/manual/administration/install-community/)

Read the [Database Guide](/wiki/install/database) for more information.

## Git

:information_source: **Git** `2.11.0` **or later is required.** There is a bug in earlier versions causing the remote sync to fail during initialization.

Even though Linux usually comes with Git pre-installed, it is most likely an outdated version. You can verify the currently installed version by running `git --version`

You can download the [latest version](https://git-scm.com/downloads) from the official Git website.

## An empty Git repository

All content created in the Wiki is saved locally and synced regularly to a remote Git repository.  
Any Git repository will do, as long as the Wiki can connect to it using **basic** or **ssh** authentication.

While not recommended, it is possible to use Wiki.js in a complete offline mode with no remote sync.

Read the [Git Repository Guide](/wiki/install/git) for more information.

# End User Requirements
The following modern browsers are supported:

- Google Chrome
- Mozilla Firefox
- Microsoft Edge
- Microsoft Internet Explorer 10, 11
- Apple Safari
- Opera

> :no_entry_sign: **Unsupported Browsers**
> 
> Internet Explorer 9 and below are not supported. Wiki.js makes heavy use of the latest HTML / CSS / JS standards, which simply doesn't work in these browsers.
{.is-danger}