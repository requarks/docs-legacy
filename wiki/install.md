<!-- TITLE: Install -->
<!-- SUBTITLE: How to install Wiki.js on your server -->
![Wiki.js](/uploads/page-icons/logo.png "Logo"){.pagelogo}
# Prerequisites
Make sure you have read the [prerequisites](/wiki/prerequisites) page to ensure your server meets the minimum requirements.

# Installation
## Linux / macOS
**Create an empty folder** where Wiki.js should be installed.

From this folder, in a command prompt, **run** the following command:
```bash
curl -sSo- https://wiki.js.org/install.sh | bash
```
Wiki.js will be installed in the current directory.

## Windows
From a **PowerShell** prompt, **run** the following command:
```powershell
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; iex ((New-Object System.Net.WebClient).DownloadString('https://wiki.js.org/install.ps1'))
```
You'll be prompted where Wiki.js should be installed. The destination folder will be created automatically if it doesn't exist.

> **Execution Policy**
>
> Your powershell execution policy must be set to Bypass to allow this script to run:
> `Set-ExecutionPolicy Bypass`
{.is-info}

## Alternative NPM method (deprecated)
It is also possible to install Wiki.js via npm (all platforms).
The npm script will simply call the commands above depending on your OS.

**This installation method is deprecated. Please use the methods above to install or upgrade going forward.**

```bash
npm install wiki.js@latest
```
# Configuration
Once the installation is completed, you'll be prompted to run the configuration wizard.

Start the configuration wizard by running the command `node wiki configure`.  To use a custom port, use the following command: `node wiki configure 1234` where 1234 is the custom port.

Using your web browser, navigate to http://localhost:3000/ (replace `localhost` with the IP of your server / custom port if applicable) and follow the on-screen instructions.

All settings entered during the configuration wizard are saved in the file `config.yml`. See the [Configuration File](/wiki/install/configuration) guide for all the possible options you can use.

# Run Wiki.js
The configuration wizard will automatically start Wiki.js for you.

To start Wiki.js manually, in a command prompt, **run** the following command: `node wiki start`  
	- If using a Powershell prompt (default on Windows 10), you can instead use the `.\wiki start` command.  
	- **Wait** for the command to complete. This can take several seconds.  
	- **Browse** to your Wiki from your browser. You should see the Wiki.js welcome screen.

> Wiki.js runs as a background process, using [pm2](http://pm2.keymetrics.io/) as its process manager.

# Notes
### Stop Wiki.js
To stop Wiki.js, run the command: 
```bash
node wiki stop
```

### Restart Wiki.js
To restart Wiki.js, run the command: 
```bash
node wiki restart
```

### Run at startup

By default, Wiki.js will not start automatically following a system reboot. In order to make it start on boot, we need to setup pm2 as a global npm module and set it as a startup service:

1. Still in a command prompt, **install pm2** globally by running the following command: `npm install -g pm2`
	- Wait for the installation to complete.
2. We now need to tell pm2 to configure itself **as a startup service**.
	- On Linux/macOS, simply run the following command: `pm2 startup`
		- pm2 will generate a command for you to execute. Copy the command and execute it.
	- On Windows, we need to install an additional dependency:
		- Run the command: `npm install pm2-windows-startup -g`
		- Once finished, run the command: `pm2-startup install`
3. Finally, **save the current pm2 configuration** by running the command: `pm2 save`

### View installed version
To view the currently installed version, run the command:  
```bash
node wiki -V
```

# Troubleshooting
## Manual Installation

If you cannot use the above installation methods, you can manually install Wiki.js:

1. Download the `wiki-js.tar.gz` and `node_modules.tar.gz` files directly from the [GitHub Releases](https://github.com/Requarks/wiki/releases).
2. Extract `wiki-js.tar.gz` to the location of your choice.
3. Extract `node_modules.tar.gz` in a folder named `node_modules` in the same folder where you extracted the `wiki-js.tar.gz` package.
4. Rename the file `config.sample.yml` to `config.yml`
5. See steps above to configure and run Wiki.js.

## More
View more troubleshooting options [here](/wiki/troubleshooting#wiki-js-wont-start).