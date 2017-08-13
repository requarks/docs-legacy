<!-- TITLE: Developer Guide -->
<!-- SUBTITLE: How to run and build Wiki.js for developers -->
![Wiki.js](/uploads/page-icons/logo.png "Logo"){.pagelogo}

# Getting Started
It is highly recommended to download the source code from a published release and **not** from the master branch directly.

You can find the latest release source code on the [GitHub Releases](https://github.com/Requarks/wiki/releases) page. Use either the `Source code (zip)` or `Source code (tar.gz)` file.

Make sure you have installed all dependencies and created the `config.yml` file (or run the setup wizard to generate it).

# Project Structure
- **assets**: Contains production-ready assets (js, css, images, fonts, etc.). *No modifications should be done here!*
- **client**: Contains dev source files for js and scss. This is where you should edit the client js and scss files.
	- **content**: Server-side text templates.
	- **js**: Client-side Javascript source files.
	- **scss**: Client-side SCSS source files.
- **data** \*: Contains cache, search index and temporary uploads. Contents are always flushed and re-created on start.
	- **cache**: Page cache (compiled HTML, metadata, table of contents, etc.)
	- **temp-upload**: Temporary uploads being uploaded / processed.
	- **thumbs**: Image upload thumbnails.
- **logs** \*: Contains the server process output and error logs.
- **npm**: Contains the installation scripts to download and install Wiki.js. *(deprecated)*
- **repo** \*: The git repository containing pages and uploads.
- **server**: Contains server files
	- **app**: Contains app date and configuration that shouldn't be modified by the user.
	- **controllers**: Contains the server-side logic for loading pages and responding to POST/PUT queries.
	- **libs**: Contains server modules, used by multiple controllers or server functions.
		- **search-index**: Modified search-index files to remove native compilation requirements.
		- **winston-transports**: Extra winston transport integrations.
	- **locales**: Contains the localization files for multilingual UI capibilities.
	- **middlewares**: Contains server middlewares that alter the requests for authentication, user funtions and security.
	- **models**: Contains the database models for MongoDB.
	- **views**: Contains the view templates for pages, in Pug format.
- **test**: The linting and unit test files
- **tools**: Build and CI scripts / tools
- **wiki.js**: Main entry point, which runs the main server or configure (setup wizard) process depending on the provided arguments.

\* Not included in source code. These folders are generated automatically on first-time run.

# Requirements
- Node.js native compilation dependencies
- Yarn
# Compile client assets
To compile all client assets:

```bash
yarn run build
```

This will generate new bundles and copy the necessary 3rd-party libraries in `/assets/js`. Notice there is no CSS folder/files being generated as they are included directly into the js bundle.
# Run development server
Running Wiki.js in development mode has the following extra features over production mode:
- Automatic restart on changes
- Automatic re-compilation of client-side js and css assets
- Hot-reload for the setup wizard. *(Disabled on main server, as it causes layout issues on reload)*
- Runs in debug mode *(obviously)*, easier to catch errors.

Start Wiki.js in development mode (using port defined in `config.yml`):

```bash
yarn run dev
```

Start Wiki.js setup wizard in development mode (using port `3000`):

```bash
yarn run dev-configure
```

# Run tests
To run linting and unit tests:

```bash
yarn test
```
