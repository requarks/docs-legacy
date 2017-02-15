<!-- TITLE: Install -->
<!-- SUBTITLE: How to install Wiki.js on your server -->
![Wiki](/uploads/page-icons/wiki.png "Wiki"){.pagelogo}
# A - Prerequisites
Make sure you have read the [prerequisites](prerequisites) page to ensure your server meets the minimum requirements.

# B - Installation
## The easy way, using npm
1. **Create an empty folder** where Wiki.js should be installed.
2. From this folder, in a command prompt, **run** the following command (exactly as displayed): `npm install wiki.js@latest`
3. **Wait** for the installation to complete. If you see any error(s) in red, make sure you fix them first. Wiki.js will most likely crash or refuse to start if all dependencies are not properly installed. Note that you can safely ignore warnings (in yellow).
	- If you get errors related to `node-gyp`, make sure you have the necessary build tools for Node.js native compilation as explained in the [prerequisites](prerequisites) page, then run the command again!
4. Continue reading from section **C - Configuration** below.

## Manually
1. **Download the latest release** from the project [Releases page](https://github.com/Requarks/wiki/releases).
	- On Linux, use the `wiki-js.tar.gz` version.
	- On Windows and macOS, use the `wiki-js.zip` version.
2. **Extract the archive** to the final location of your choice on your server.
	- On Linux, the standard location would be under `/var/www`
	- On Windows, the standard location would be under `C:\inetpub`
	- On macOS, the standard location would be under `/Library/WebServer/Documents`
3. In a command prompt, **run** the following command: `npm install --only=production && npm rebuild`
	- On Linux, you are already in a command prompt! If you're in the GUI, launch a **Terminal** window and jump to the Wiki.js folder using the **cd** command. *e.g.* `cd /var/www/wiki`
	- On Windows, navigate to the Wiki.js folder in File Explorer. While holding **Shift**, right-click in an empty area and choose **Open a command window here**. On Windows 10, you may instead have **Open a Powershell window here**.
	- On macOS, launch the **Terminal** application and jump to the Wiki.js folder using the **cd** command. *e.g.* `cd /Library/WebServer/Documents/wiki`
4. **Wait** for the dependencies installation to finish. If you see any error(s) in red, make sure you fix them first. Wiki.js will most likely crash or refuse to start if all dependencies are not properly installed. Note that you can safely ignore warnings (in yellow).
	- If you get errors related to `node-gyp`, make sure you have the necessary build tools for Node.js native compilation as explained in the [prerequisites](prerequisites) page, then run the command again!
5. **Rename** the file `config.sample.yml` to `config.yml`
	- If you are upgrading, do not replace your existing `config.yml` file!

# C - Configuration
6. **Edit** the file `config.yml` and enter the configuration values to match your setup. See the [Configuration File](install/configuration) guide for all the possible properties you can use.

# D - Run Wiki.js
You can now start Wiki.js and make sure everything runs smoothly:

7. In a command prompt, **run** the following command: `wiki start`
	- If using a Powershell prompt (default on Windows 10), you must instead use the `.\wiki start` command.
	- **Wait** for the command to complete. This can take several seconds.
	- **Browse** to your Wiki from your browser. You should see the Wiki.js welcome screen.

> Wiki.js runs as a background process, using [pm2](http://pm2.keymetrics.io/) as its process manager.

# E - Run at startup (optional)
By default, Wiki.js will not start automatically following a system reboot. In order to make it start on boot, we need to setup pm2 as a global npm module and set it as a startup service:

8. Still in a command prompt, **install pm2** globally by running the following command: `npm install -g pm2`
	- Wait for the installation to complete.
9. We now need to tell pm2 to configure itself **as a startup service**.
	- On Linux/macOS, simply run the following command: `pm2 startup`
		- pm2 will generate a command for you to execute. Copy the command and execute it.
	- On Windows, we need to install an additional dependency:
		- Run the command: `npm install pm2-windows-startup -g`
		- Once finished, run the command: `pm2-startup install`
10. Finally, **save the current pm2 configuration** by running the command: `pm2 save`

# Notes
To stop Wiki.js, run the command: `wiki stop`
- If using a Powershell prompt (default on Windows 10), you must instead use the `.\wiki stop` command.

To view the currently installed version, run the command: `wiki -V`
- If using a Powershell prompt (default on Windows 10), you must instead use the `.\wiki -V` command.
