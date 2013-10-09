# A Lineman JS Template using Angular

This is a project template for Angular JS applications using [Lineman](http://www.linemanjs.com).

It includes the following features:

1. Template Precompilation into Angulars $templateCache using `grunt-angular-templates`
2. A basic login, logout service bound to sample routes inside `config/server.js`
3. A router, and 2 views `home` and `login`
4. A directive that shows a message on mouseover
5. 2 Controllers, for `home` and `login`, with $scope variables set and bound
6. A working, bound login form (username/password don't matter, but are required)
7. Configured [grunt-ngmin](https://github.com/btford/grunt-ngmin) so you don't have to fully qualify angular dependencies.
8. Auto generated [sourcemaps](http://www.html5rocks.com/en/tutorials/developertools/sourcemaps/) with inlined sources via [grunt-concat-sourcemap](https://github.com/kozy4324/grunt-concat-sourcemap) (you'll need to [enable sourcemaps](http://cl.ly/image/1d0X2z2u1E3b) in Firefox/Chrome to see this)
9. [Unit Tests](https://github.com/davemo/lineman-angular-template/tree/master/spec) and [End-to-End Tests](https://github.com/davemo/lineman-angular-template/tree/master/spec-e2e)
10. Configuration to run [Protractor](https://github.com/juliemr/protractor) for End-to-End Tests

# Instructions

1. `git clone https://github.com/davemo/lineman-angular-template.git my-lineman-app`
2. `cd my-lineman-app`
3. `sudo npm install -g lineman`
4. `npm install`
5. `lineman run`
6. open your web browser to localhost:8000

# Running Tests

This template was used as the basis of my [Testing Strategies for Angular JS](http://www.youtube.com/watch?v=UYVcY9EJcRs) screencast, and contains all the tests we wrote in the screencast and a few more!

To run the unit tests:

1. `lineman run` from 1 terminal window
2. `lineman spec` from another terminal window, this will launch Testem and execute specs in Chrome

To run the end-to-end tests:

1. `npm install protractor`
2. `brew install selenium-server-standalone`
3. Make sure you have firefox installed.
4. `lineman run` from 1 terminal window
5. `lineman grunt spec-e2e` from another terminal window

# Defining your apps angular.module in CoffeeScript

If you are using Coffeescript to define the angular.module for your app, you will need to swap the concat order in `config/application.js` such that coffeescript files are included _before_ javascript, here's a sample config. (If you are using JavaScript for defining the angular.module the default concat order is fine).

```javascript
js: {
  // if using coffeescript and your angular.module is defined in a .coffee file, files.coffee.generated comes first
  src: ["<%= files.js.vendor %>", "<%= files.coffee.generated %>", "<%= files.js.app %>", "<%= files.ngtemplates.dest %>"],
  dest: "<%= files.js.concatenated %>"
},
```

Hopefully this helps you get up and running with AngularJS!
