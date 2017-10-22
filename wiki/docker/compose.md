<!-- TITLE: Using Docker Compose -->
<!-- SUBTITLE: Install and run Wiki.js in a docker container using Docker Compose -->

# Prerequisites
- Docker

# Create config file
1) Create a copy of the [sample config file](https://github.com/Requarks/wiki/blob/master/config.sample.yml) on your host.
2) Modify the config file with your own settings.

Make sure to set the `db` parameter to point to the mongo container. In the example docker compose file, the mongo container is named `wikidb`. As such, the `db` connection string should be set to: `mongodb://wikidb:27017/wiki`
# Create Docker Compose file
1) Create a copy of the [sample Docker Compose](https://github.com/Requarks/wiki/blob/master/tools/docker-compose.yml) file.
2) Change the `ports` port to match the port entered in your config.yml file.
3) Replace the `WIKI_ADMIN_EMAIL` parameter value with the email of the administrator account. This account will be created when run the first time.
4) Replace the `./config.yml` value with the path of your config file created earlier. It will be linked to your docker container. Do **not** change the path of the config file inside the container (`/var/wiki/config.yml`)!
5) Change the local path of the MongoDB data folder (`./data/mongo`) if necessary.  Do **not** change the path of the data folder inside the mongo container (`/db/data`)!

# Run the container
It's now time to run the containers as defined in the previous step:
```bash
sudo docker-compose up
```

# First login
An administrator account is created the first time you run the container. The default password is `admin123`. Change it upon login!

