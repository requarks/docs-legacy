<!-- TITLE: Install on Debian 8 -->
<!-- SUBTITLE: How to install Wiki.js on Debian 8 -->

This installation guide is based on a new Debian 8 instance from DigitalOcean / Vultr.
# Create user
Let's create a new user for running Wiki.js: `adduser wiki`
# Install MongoDB
Follow the official installation guide: https://docs.mongodb.com/manual/tutorial/install-mongodb-on-debian/
# Install Git
The latest git package available for Debian 8 is outdated and cannot be used. We'll compile the latest release from source.

It is recommended to use the latest version available by looking at the https://github.com/git/git/releases page.  
Simply replace the version number in the instructions below.

```sh
# Remove existing git package: 
apt-get remove git

# Install build requirements:
apt-get install libcurl4-openssl-dev libexpat1-dev gettext libz-dev libssl-dev build-essential autoconf

# Fetch and build Git
cd /tmp
curl -L --progress https://github.com/git/git/archive/v2.13.1.tar.gz | tar xz
cd git-2.13.1/
make configure
./configure
make prefix=/usr/local all
make prefix=/usr/local install

# Confirm this command returns /usr/local/bin/git:
which git
```

# Install Node.js
Install the LTS version of Node.js:

```sh
curl -sL https://deb.nodesource.com/setup_6.x | bash -
apt-get install -y nodejs
```

# Install sudo
**If sudo is already installed and configured, skip this step.**

1. Install sudo: `apt install sudo`
2. Add the wiki user to sudo group: `adduser wiki sudo`
3. Edit the sudoers file: `nano /etc/sudoers`
	- Add the following line `wiki ALL=(ALL:ALL) ALL` right after `%sudo  ALL=(ALL:ALL) ALL`
	- Ctrl-X to save.
4. Disconnect from your SSH / Terminal session and reconnect.
# Install Wiki.js
1. Login as the wiki user: `sudo -i -u wiki`
2. Create a folder to install Wiki.js: `mkdir wiki`
3. Go inside the folder: `cd wiki`
4. Install Wiki.js: `curl -sSo- https://wiki.js.org/install.sh | bash`
5. Follow the instructions to complete the installation.
