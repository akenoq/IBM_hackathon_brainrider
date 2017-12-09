## dbrainserver

Webpack Web project with ExpressJS on NodeJS

[![](https://img.shields.io/badge/bluemix-powered-blue.svg)](https://bluemix.net)
![Platform](https://img.shields.io/badge/platform-NODE-lightgrey.svg?style=flat)

### Table of Contents
* [Summary](#summary)
* [Requirements](#requirements)
* [Configuration](#configuration)
* [Run](#run)

<a name="summary"></a>
### Summary
The Webpack starter contains an opinionated set of components for modern web development, including:

* [Webpack](https://webpack.github.io/)
* [Sass](http://sass-lang.com/) 
* [Babel](https://babeljs.io/) for ECMAScript 2015 (ES2015) 
* [gulp](http://gulpjs.com/)
* [jQuery](https://jquery.com/)

<a name="requirements"></a>
### Requirements
#### Local Development Tools Setup (optional)

- Install the latest [NodeJS](https://nodejs.org/en/download/) 6+ LTS version.

#### Bluemix development tools setup (optional)

1. Install [Docker](http://docker.io) on your machine.
2. Install the [Bluemix CLI](https://console.ng.bluemix.net/docs/cli/index.html)
3. Install the plugin with:

  `bx plugin install dev -r bluemix`


#### IBM Bluemix DevOps setup (optional)

[![Create Toolchain](https://console.ng.bluemix.net/devops/graphics/create_toolchain_button.png)](https://console.ng.bluemix.net/devops/setup/deploy/)

[IBM Bluemix DevOps](https://www.ibm.com/cloud-computing/bluemix/devops) services provides toolchains as a set of tool integrations that support development, deployment, and operations tasks inside Bluemix. The "Create Toolchain" button creates a DevOps toolchain and acts as a single-click deploy to Bluemix including provisioning all required services. 

***Note** you must publish your project to [Github](https://github.com/) for this to work.


<a name="configuration"></a>
### Configuration

The project contains Bluemix specific files that are used to deploy the application as part of a Bluemix DevOps flow. The `.bluemix` directory contains files used to define the Bluemix toolchain and pipeline for your application. The `manifest.yml` file specifies the name of your application in Bluemix, the timeout value during deployment, and which services to bind to.

Service credentials are taken from the VCAP_SERVICES environment variable if running Bluemix Cloud Foundry, from individual environment variables per service if running on Bluemix Container Service (see ./server/config/mappings.json), or from a config file if running locally, named`./server/config/localdev-config.js`.


<a name="run"></a>
### Run
#### Using Bluemix development CLI
The Bluemix development plugin makes it easy to compile and run your application if you do not have all of the tools installed on your computer yet. Your application will be compiled with Docker containers. To compile and run your app, run:

```
bash
bx dev build
bx dev run
```


#### Using your local development environment

Modern web applications require a compilation step to prepare your ES2015 JavaScript or Sass stylesheets into compressed Javascript ready for a browser. Webpack is used for bundling your JavaScript sources and styles into a `bundle.js` file that your `index.html` file can import. 

***Webpack***

For development mode, use `webpack -d` to leave the sources uncompress and with the symbols intact.

For production mode, use `webpack -p` to compress and obfuscate your sources for development usage.

***Gulp***

Gulp is a task runner for JavaScript. You can run the above Webpack commands in by running:

```bash
gulp
```


##### Endpoints

Your application is running at: `http://localhost:3000/` in your browser.

- Health endpoint: `/appmetrics-dash`


##### Session Store
You may see this warning when running `bx dev run`:
```
Warning: connect.session() MemoryStore is not
designed for a production environment, as it will leak
memory, and will not scale past a single process.
```
When deploying to production, it is best practice to configure sessions to be stored in an external persistence service.
