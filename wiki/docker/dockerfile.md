<!-- TITLE: Using a Dockerfile -->
<!-- SUBTITLE: Install and run Wiki.js in a docker container using a Dockerfile -->

# Prerequisites
- Docker
- A MongoDB database server (either running inside another container or on a remote machine)

# Create config file
1) Create a copy of the [sample config file](https://github.com/Requarks/wiki/blob/master/config.sample.yml) on your host.
2) Modify the config file with your own settings.

# Create Dockerfile
1) Create a copy of the [sample Dockerfile](https://github.com/Requarks/wiki/blob/master/tools/Dockerfile).
2) Replace the `WIKI_ADMIN_EMAIL` parameter value with the email of the administrator account. This account will be created when run the first time.
3) Replace the `your-config.yml` value with the name of your config file created earlier. This file must be located in the same folder as your Dockerfile if not providing the full path. It will be copied inside your docker container.
4) Change the `EXPOSE` port to match the port entered in your config.yml file.

# Build the image
From a command prompt in the same folder as your Dockerfile, execute the following command to build your Dockerfile:
```bash
sudo docker build -t wiki .
```

# Run the container
It's now time to run the container from the image created in the previous step:
```bash
sudo docker run -p 8080:3000 wiki
```

The `-p` parameter above is optional. Define it if you want to re-map the exposed port to something else.

# First login
An administrator account is created the first time you run the container. The default password is `admin123`. Change it upon login!