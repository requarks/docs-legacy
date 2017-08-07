<!-- TITLE: Troubleshooting -->
<!-- SUBTITLE: A collection of common issues / errors and their possible solutions. -->
![Wiki.js](/uploads/page-icons/logo.png "Logo"){.pagelogo}

# General Info
Wiki.js runs using background processes, which means you may not see an error right away. The best way to look for errors / potential issues is by running these useful commands:

```sh
# View status of Wiki.js:
pm2 status wiki

# View active logs of Wiki.js:
pm2 logs wiki --lines 100
```

Output and error logs are also available in the `/logs` folder located in your Wiki.js installation folder.

# Wiki.js won't start
### Error: Listening on port XX requires elevated privileges!

**Cause**: Some Linux installations prevent Node.js from binding to ports in the lower range (e.g. < 1024). This occurs if you set a port such as **80** in config.yml.

**Solution A**: Allow the node process to safely access the port requested:
```sh
# Ubuntu / Debian

sudo apt-get install libcap2-bin
sudo setcap cap_net_bind_service=+ep `readlink -f \`which node\``
```

**Solution B**: Create a port redirection rule: *(In the example below, you must set the port to 3000 in config.yml)*
```sh
sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3000
```

**Solution C**: Use a web server in front of Wiki.js. For example, use nginx to listen to port 80 / 443 and proxy all requests to Wiki.js running on a higher port (e.g. 3000).

### Error: Port XX is already in use!

**Cause**: Another program is already listening to this port or an orphaned Wiki.js process was not closed properly.

**Solutions**: Make sure there are no orphaned Wiki.js process still running (look for **node** instances on Linux and **node.exe** processes on Windows). Look for applications that could be using this port (web servers, http applications, etc.)

# Weird display, no styling
**Cause**: The value you entered for the `host` config parameter is wrong.

**Solution**: This value should correspond to the host/domain users are using to access your wiki, **including the port if different than 80 / 443**.