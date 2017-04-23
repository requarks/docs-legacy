<!-- TITLE: Dev Guide -->
<!-- SUBTITLE: How to run and build Wiki.js for developers -->

# Getting Started
It is highly recommended to download the source code from a published release and **not** from the master branch directly.

*Until the final 1.0 release, the master branch may contain unstable code that prevents build / running the app completely.*

You can find the latest release source code on the [GitHub Releases](https://github.com/Requarks/wiki/releases) page. Use either the `Source code (zip)` or `Source code (tar.gz)` file.

Make sure you have installed all dependencies and created the `config.yml` file (or run the setup wizard to generate it).

# Project Structure
- **app**: Contains app date and configuration that shouldn't be modified by the user.
- **assets**: Contains production-ready assets (js, css, images, fonts, etc.). *No modifications should be done here!*
- **client**: Contains dev source files for js and scss. This is where you should edit the client js and scss files.
- **controllers**: Contains the server-side logic for loading pages and responding to POST/PUT queries.
- **data**\*: Contains cache, search index and temporary uploads. Contents are always flushed and re-created on start.
- **libs**: Contains server modules, used by multiple controllers or server functions.
- **locales**: Contains the localization files for multilingual UI capibilities.
- **logs**\*: Contains the server process output and error logs.
- **middlewares**: Contains server middlewares that alter the requests for authentication, user funtions and security.
- **models**: Contains the database models for MongoDB.
- **npm**: Contains the installation scripts to download and install Wiki.js.
- **repo**\*: The git repository containing pages and uploads.
- **test**: The linting and unit test files
- **views**: Contains the view templates for pages, in Pug format.

\* Not included in source code. These folders are generated automatically on first-time run.

## Root files

- **agent.js**: Runs background tasks such as indexing, thumbnail processing, etc. which shouldn't impact the main server process. Never run this process directly! It is spawned by the main server process.
- **configure.js**: Runs the setup wizard server.
- **fuse.js**: Build, compilation and dev server scripts.
- **init.js**: Contains the init scripts. It cannot run by itself.
- **server.js**: Runs the main server process.
- **wiki.js**: Main entry point, which runs the main server or configure (setup wizard) process depending on the provided arguments.
# Compile client assets
To compile all client assets:

```bash
npm run build
```

This will generate new bundles and copy the necessary 3rd-party libraries in `/assets/js`. Notice there is no CSS folder/files being generated as they are included directly into the js bundle.
# Run development server
Start Wiki.js in development mode (using port defined in `config.yml`):

```bash
npm run dev
```

Start Wiki.js setup wizard in development mode (using port `3000`):

```bash
npm run dev-configure
```

# Run tests
To run linting and unit tests:

```bash
npm test
```
