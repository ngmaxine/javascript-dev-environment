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
### Javascript Editors
* Atom
* WebStorm
* Brackets
* VSCode

### Other (Not best for JavaScript - best for backend)
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

### Sharing Work-In-Progress
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

### Scripts
* `npm run <scriptName>`
* Run tasks in parallel: `npm-run-all --parallel <scriptName1> <scriptName2>`


## Transpiling
* Babel (modern standards-based JS, leverage full JS ecosystem, use experimental features earlier, no type defs, annotations required)
* TypeScript (superset of JavaScript, enhanced autocompletion/readability, safer refactoring, clearer intent, nonstandard features such as interfaces)
* Elm (compiles down to JS, clean syntax, immutable data structures, friendly errors, all errors are compile-time errors, interops with JS)

### Babel Configuration Styles
* .babelrc (not npm specific, easier to read since isolated
* package.json (one less file in your project)
    * `"babel": { // babel config }`

### Build Script JS Style
* ES6 (no waiting for transpile, no transpiler dependency)
* Transpiled (use latest features, consistent coding style, use same linting rules everywhere)


## Bundling
### Module Formats
* IIFE (Immediately Invoked Function Expressions)
* Asynchronous Module Definition (AMD) - RequireJS
* CommonJS (CJS) - Node.js
* Universal Module Definition (UMD)
* ES6 Modules
    * Standardized - won't have to transpile when platforms have full support for ES6
    * Statically analyzable
        * Improved autocomplete
        * Intelligent refactoring
        * Fails fast
        * Tree shaking - dead code elimination
    * Easy to read
        * Named imports
        * Default exports

### Bundlers
* Require.js (first popular bundler, utilizes and helped popularize AMD pattern)
* Browserify (first bundler to reach mass adoption, bundle npm packages for web, large plugin ecosystem)
* Webpack (bundles more than just JS, import CSS/images/etc. like JS, bundle splitting, built in hot-reloading web server, Webpack 2 offers tree shaking)
* Rollup (tree shaking, faster loading production code, quite new, great for library authors, no hot reloading and code splitting)
* JSPM (uses SystemJS - a universal module loader, can load modules at runtime, has own package manager, can install from npm/git, uses Rollup)

### Sourcemaps
* Maps code back to original source
* Part of our build
* Downloaded if you open developer tools


## Linting
* Enforce consistency (curly brace position, confirm/alert, trailing commas, globals, eval)
* Avoid mistakes (extra parenthesis, overwriting function, assignment in conditional, missing default case in switch, debugger / console.log)

### Linters
* JSLint
* JSHint
* ESLint

### Core Decisions
* Config format?
    * Dedicated config file (not tied to npm)
    * package.json (one less file)
* Which built-in rules?
* Warnings or Errors?
    * Warning (can continue development, can be ignored, team must agree: fix warnings, good for minor stylistic issues)
    * Error (breaks the build, cannot be ignored, team forced to comply, useful for items likely to produce bugs)
* Which plugins?
    * Add checks for specific languages (ie. React/Angular/Node.js)
* Use a preset?
    * From scratch, recommended, preset (Airbnb, Standard JS)

### Watching with ESLint
* eslint-loader (re-lints all files upon save)
* eslint-watch (ESLint wrapper that adds file watch, not tied to webpack, better warning/error formatting, displays clean message, easily lint  tests and build scripts)
* eslint rules values (0 = Off, 1 = Warning, 2 = Error)


## Testing and Continuous Integration
### Unit Testing Decisions
* Framework
    * Mocha (most popular, highly configurable, large ecosystem of support)
    * Jasmine (similar to Mocha, includes built-in assertion library)
    * Tape (lean/simple)
    * QUnit (oldest)
    * AVA (runs tests in parallel, reruns impacted tests)
    * Jest (popular amongst React developers)
* Assertion Library
    * Chai, Expect
    * Assertion = Declare what you expect
    * Most libraries just differ by syntax
* Helper Libraries
    * JSDOM - simulate browser's DOM, run DOM-related tests without a browser
    * Cheerio - jQuery for the server, query virtual DOM using jQuery selectors
* Where to run tests
    * Browser - Karma, Testem (requires more configuration, slower)
    * Headless Browser (browser doesn't have visible UI) - PhantomJS
    * In-memory DOM - JSDOM (lighter-weight alternative to PhantomJS)
* Where to place tests
    * Centralized - less 'noise' in src folder, deployment confusion, inertia
    * Alongside - easy imports, clear visibility, convenient to open, no recreating folder structure, easy to move files
* When to run tests
    * Unit tests should run when hit save - rapid feedback, facilitates TDD, automatic = low friction, increase test visibility

### Unit Tests vs Integration Tests
* Unit tests - test a small unit, often single function, fast, run upon save
* Integration tests - test multiple units, involves clicking and waiting, slow, run on demand or in QA

### Continuous Integration
* Confirm commit works as expected on another machine
* Why CI?
    * Forgot to commit new file
    * Forgot to update package.json
    * Commit doesn't run cross-platform
    * Node version conflicts
    * Bad merge
    * Didn't run tests
    * Catch mistakes quickly
* Runs automated build, runs tests, checks code coverage, automate deployment
* Travis CI (popular, linux-based, hosted solution)
* Appveyor (Windows-based)
* Jenkins (popular, highly-configurable)
* CircleCI
* Semaphore
* SnapCI
