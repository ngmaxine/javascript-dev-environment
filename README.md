# Building a JavaScript Development Environment

## Starter Kit / Boilerplate Components
* Package Management
* Bundling
* Minification
* Sourcemaps
* Transpiling
* Dynamic HTML Generation
* Centralized HTTP
* Mock API Framework
* Component Libraries
* Development Webserver
* Linting
* Automated Testing
* Continuous Integration
* Automated Build
* Automated Deployment
* Working example app


## Editors
Javascript Editors
* Atom
* WebStorm
* Brackets
* VSCode

Other (Not best for JavaScript - best for backend)
* Visual Studio
* Eclipse
* Netbeans


## Package Management
* Bower
* npm
* JSPM (JavaScript Package Manager)
* Jam
* volo


## Development Webservers
* http-server (simple, lightweight, single command serves current directory)
* live-server (lightweight, live-reloading)
* Express (comprehensive, highly configurable, production grade)
    * Alternatives: koa, hapi
* budo (integrates with Browserify, hot reloading)
* Webpack dev server (built in to Webpack, serves from memory, hot reloading)
* Browsersync (dedicated IP for sharing work on LAN, all interactions remain in sync, great for cross-device testing, integrates with Webpack/Browserify/Gulp)

Sharing Work-In-Progress
* localtunnel (share work on local machine, easiest setup, ultra-versatile)
    * `npm install localtunnel -g`
    * Start your app
    * `lt --port 3000 (--subdomain <name>)`
* ngrok (share work on local machine, easy setup, secure)
    * Sign up
    * Install ngrok
    * Install authtoken
    * Start your app
    * `./ngrok http 80`
* Surge (hosts only static files, simple, hosting persists, no firewall hole)
    * `npm install -g surge`
    * `surge`
* now (quickly deploy Node.js to cloud, hosting persists, no firewall hole)
    * `npm install -g now`
    *  Create start script
    * `now`


## Automation
* Grunt (configuration over code, writes intermediary files between steps, large plugin ecosystem)
* Gulp (in-memory streams, fast, code over configuration, large plugin ecosystem)
* npm Scripts (declared in package.json, leverage OS command line, directly use npm packages, call separate Node scripts, convention-based pre/post hooks, leverage npm)
    * Use tools directly
    * No need for separate plugins
    * Simpler debugging
    * Better docs
    * Easy to learn
    * Simple

Scripts
* `npm run <scriptName>`
* Run tasks in parallel: `npm-run-all --parallel <scriptName1> <scriptName2>`
