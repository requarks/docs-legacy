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

# Configure
3. **Rename** the file `config.sample.yml` to `config.yml`
4. **Edit** the file `config.yml` you just renamed.

# Run Wiki.js
You can now start Wiki.js and makes sure