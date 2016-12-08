<!-- TITLE: Prerequisites -->
<!-- SUBTITLE: Requirements to run Wiki.js -->
![Prerequisites](/uploads/page-icons/prerequisites.png "Prerequisites"){.pagelogo}

Wiki.js is cross-platform (Windows, Linux and Mac) and does not depend on any paid commercial product / service.

While Wiki.js runs on pretty much any platform that supports the requirements below, the following environments are recommended and more thoroughly tested:

- Ubuntu Server 14.04 LTS / 16.04 LTS
- Windows Server 2012 R2

# Requirements

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

## Node.js Compile support

Your system must be able to compile node addons in order to install Wiki.js dependencies:

- On **Ubuntu/Debian Linux**: `sudo apt-get install -y build-essential`
- On **RedHat/CentOS/Fedora Linux**: `yum install gcc-c++ make`
- On **Windows**: In an elevated-priviledges command prompt: `npm install -g windows-build-tools`
- On **macOS**: Install the `Command Line Tools` via Xcode *(Xcode -> Preferences -> Downloads)*.

## MongoDB
MongoDB is a free and open-source cross-platform document-oriented database program. Classified as a NoSQL database program, MongoDB uses JSON-like documents with schemas.

:information_source: **MongoDB** `3.2` **or later is required.**

- [Official Website](https://www.mongodb.com/)
- [Installation Guide](https://docs.mongodb.com/manual/administration/install-community/)

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