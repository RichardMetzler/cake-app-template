![CakePHP 3 Notifications Plugin](https://raw.githubusercontent.com/scherersoftware/cakephp-app-template/master/app-template.png)

[![Build Status](https://travis-ci.org/scherersoftware/cakephp-app-template.svg?branch=master)](https://travis-ci.org/scherersoftware/cakephp-app-template)
[![License](https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square)](LICENSE.txt)

Pre-Configured Application Template for CakePHP 3

## Installation

This is just a brief installation guide. A much more detailed version will be available soon:

Use composer to install the package:

`$ composer create-project --stability dev scherersoftware/cakephp-app-template <project-name>`

First, we have to install sass and some npm packages

```
$ gem install sass
$ npm install
```

Install the bower dependencies:

`$ bower install`

As the default `font` paths from font-awesome and source-sans-pro are not quite fitting for us, we have to change them.

Go to the `font-awesome _variables.scss` file, located at `webroot/vendors/bower_components/font-awesome/scss/` and change the `@fa-font-path` to <code>$fa-font-path: "/vendors/bower_components/font-awesome/fonts" !default;</code>

Next, open the `source-sans-pro _variables.scss` file, located at `webroot/vendors/bower_components/source-sans-pro/scss/` and change `$source-sans-pro-path:` to <code>$source-sans-pro-path: "/vendors/bower_components/source-sans-pro/fonts/source-sans-pro" !default;</code>

After that, run `$ bin/ext_compilse.sh` to recompile the assets.

Stuff like mySQL user and password is configured by using PHP Dotenv.
Just rename the `.env.deault` to `.env` and set the values.
Be sure to also set `SESSION_COOKIE_NAME`
and `MAIN_DOMAIN`, as these values are mandatory for a correct session setup.

Next, setup your database. We're using cakephp/migrations for that:

`$ bin/cake migrations migrate`

Also run the migrations from Josegonzalez/CakeQueuesadilla, as we use this plugin to send out the restore password emails.

`$ bin/cake migrations migrate -p Josegonzalez/CakeQueuesadilla`

Now seed the database with a default user

`$ bin/cake migrations seed`

Please also run the provided SQL-Query on the top of the demo page to enable the login.

Default email: `john.doe@example.com`, default password: `password`
