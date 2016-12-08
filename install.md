<!-- TITLE: Install -->
<!-- SUBTITLE: How to install Wiki.js on your server -->
# Prerequisites
Make sure you have read the [prerequisites](prerequisites) page to ensure your server meets the minimum requirements.

# Get Wiki.js
1. **Download the latest release** from the project [Releases page](https://github.com/Requarks/wiki/releases).
	- On Linux, use the `wiki-js.tar.gz` version.
	- On Windows and Mac, use the `wiki-js.zip` version.
2. **Extract the archive** to the final location of your choice on your server.
	- On Linux, the standard location would be under `/var/www`
	- On Windows, the standard location would be under `C:\inetpub`
	- On Mac, the standard location would be under `/Library/WebServer/Documents`

# Install dependencies
3. In a command prompt, **run** the following command: `npm install --only=production`
	- On Linux, you are already in a command prompt! If you're in the GUI, launch a **Terminal** window and jump to the Wiki.js folder using the **cd** command. *e.g.* `cd /var/www/wiki`
	- On Windows, navigate to the Wiki.js folder in File Explorer. Right-click in an empty area and choose **Open a command window here**.
	- On Mac, launch the **Terminal** application and jump to the Wiki.js folder using the **cd** command. *e.g.* `cd /Library/WebServer/Documents/wiki`
4. **Wait** for the dependencies installation to finish. If you see any error(s) in red, make sure you fix them first. Wiki.js will most likely crash or refuse to start if all dependencies are not properly installed. Note that you can safely ignore warnings (in yellow).
	- If you get errors related to `node-gyp`, make sure you have the necessary build tools as explained in the [prerequisites](prerequisites) page!
# Configure
5. **Rename** the file `config.sample.yml` to `config.yml`
	- If you are upgrading, do not replace your existing `config.yml` file!
6. **Edit** the file `config.yml` you just renamed and enter the configuration values that are listed and explained in the table below:

# Run Wiki.js
You can now start Wiki.js and make sure everything runs smoothly:

7. In a command prompt, **run** the following command: `node server.js`
	- Wait for the server to initialize. Wiki.js uses 2 separate processes, identified by `[SERVER]` and `[AGENT]` in the logs.
	- Make sure no errors appear and that you have the following 2 lines:
		- `[SERVER] HTTP/WS server started successfully! [RUNNING]`
		- `[AGENT] All jobs completed successfully! Going to sleep for now.`
8. Now that you know that the server runs fine, **kill** the server sending key combination `CTRL-C` twice.
	- Why? Because we are not going to actually run the server this way. We were only making sure it runs without error.

# Run as a service
We'll now configure Wiki.js to run as a background service using pm2.

>[pm2](http://pm2.keymetrics.io/) is a process manager for Node.js applications. It runs applications in the background, restarts them automatically if a crash occurs, save logs to file and most importantly, starts the apps back after a system reboot.

9. Still in a command prompt, **install pm2** by running the following command: `npm install -g pm2`
	 - Wait for the installation to complete.
10. 
