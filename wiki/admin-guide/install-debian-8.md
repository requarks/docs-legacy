<!-- TITLE: Install on Debian 8 -->
<!-- SUBTITLE: How to install Wiki.js on Debian 8 -->

# Create user
Let's create a new user for running Wiki.js: `adduser wiki`
# Install MongoDB
Follow the official installation guide: https://docs.mongodb.com/manual/tutorial/install-mongodb-on-debian/
# Install Git
The latest git package available for Debian 8 is outdated and cannot be used. We'll compile the latest release from source.

It is recommended to use the latest version available by looking at the https://github.com/git/git/releases page. Simply replace the version number in the instructions below.

1. Remove existing git package: `apt-get remove git`
2. Install build requirements: `apt-get install libcurl4-openssl-dev libexpat1-dev gettext libz-dev libssl-dev build-essential autoconf`
3. Go to tmp directory: `cd /tmp`
4. Download latest source: `curl -L --progress https://github.com/git/git/archive/v2.13.1.tar.gz | tar xz`
5. Go to extracted directory: `cd git-2.13.1/`
6. Run: `make configure`
7. Run: `./configure`
8. Run: `make prefix=/usr/local all`
9. Run: `make prefix=/usr/local install`
10. Confirm that `which git` produces `/usr/local/bin/git`

# Install Node.js
Install the LTS version of Node.js:

```bash
curl -sL https://deb.nodesource.com/setup_6.x | bash -
apt-get install -y nodejs
```

# Install sudo
**If sudo is already installed and configured, skip this step.**

Let's install sudo: `apt install sudo`
# Install Wiki.js


