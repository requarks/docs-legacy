<!-- TITLE: Using the Docker image -->
<!-- SUBTITLE: How to use the Docker image directly -->

This is the most direct and simple way to run a Docker container of Wiki.js. For more control and flexibility over its configuration, check out the [Dockerfile](/wiki/docker/dockerfile) and [Docker Compose](/wiki/docker/compose) guides.
# Prerequisites
- Docker
- A MongoDB database server (either running inside another container or on a remote machine)
# Create config file
1) Create a copy of the [sample config file](https://github.com/Requarks/wiki/blob/master/config.sample.yml) on your host.
2) Modify the config file with your own settings.
# Install
## Fetch image

```bash
sudo docker pull requarks/wiki
```
## Run container
You must provide 3 parameters when running a Wiki.js container:

- The port to expose
- The administrator account email
- The path of the config file created earlier

Adapt the example command below:

```bash
sudo docker run -p 8080:3000 -e "WIKI_ADMIN_EMAIL=admin@example.com" -v /home/bob/wiki-config.yml:/var/wiki/config.yml requarks/wiki
```

In the example above, the port `3000` is the port defined in your config.yml, while `8080` is the port that is exposed publicly.
The admin email is set to `admin@example.com`.
The path to the config.yml file is set to `/home/bob/wiki-config.yml`. Do **not** change the path in the container (`/var/wiki/config.yml`)!
# First login
An administrator account is created the first time you run the container. The default password is `admin123`. Change it upon login!