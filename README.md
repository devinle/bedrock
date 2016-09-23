# [WP Starter](https://github.com/devinle/bedrock)

Fork that adds functionality and extends to Roots/Bedrock. We use this as a starter shell to quickly get up and running with Bedrock using Sage. Original repo is set as Upstream and can be sync'd back if necessary.

* Enabled major versioning of WP via Composer
* Added Better WP Security as a requirement
* Added W3 Total cache as a requirement
* Added WP SEO as a requirement
* Added submodule to Sage theme

## [WP Starter > Sage Submodule](https://github.com/devinle/sage)

Fork that adds functionality and extends to Roots/Sage theme. Original repo is set as Upstream and can be sync'd back if necessary.

* Removed all SCSS files except for a main and common/buttons starter (required to have some KSS commenting so included to bootstrap project)
* Removed all bootstrap references in JS and Styles
* Added new cleanup file to remove extra unwanted wordpress markup from output templates (web/app/themes/sage/lib/cleanup.php)
* Added new editor file to add extra TinyMCE custom capabilities - commented out for now (web/app/themes/sage/lib/editor.php)
* Added KSS webpack plugin for living styleguide
* Added submodule for KSS workflow called ed-kss-template

## [Sage > ED KSS Template Submodule](https://dleggett@bitbucket.org/enginedigital/ed-kss-template.git)

Soon to be custom KSS template built into the Sage WP theme webpack workflow.

* No changes just yet. Soon to come.

# Fork Instructions (follow these for initial clone setup, more original Bedrock directions to follow below)

## Clone instructions

Clone the bedrock fork. The --recursive flag allows you to also fetch the submodule sage fork

* git clone https://github.com/devinle/bedrock --recursive

If you forget to run the --recursive flag, do this

* git submodule init (Initialize local confiuration file for submodule)
* git submodule update (Fetch data from project and check out)

To pull latest submodule updates

* submodule update --remote --merge

Upstream details: Both this Kit and the Sage submodule are set as upstreams. To sync with the latest Roots updates (if desired) follow these 2 links.

* https://help.github.com/articles/configuring-a-remote-for-a-fork/
* https://help.github.com/articles/syncing-a-fork/

## Setup instructions

* cd into root directory
* run composer install
* setup new MAMP and point to web dir
* setup a local database
* copy .env.sample -> .env and enter credentials and salts
* cd into sage theme root directory and run npm install, then run composer install
* load up your Mamp dev URL in browser and run WP setup
* log in and choose Appearance and set it to Sage Starter Theme
* To use BrowserSync during npm start you need to update devUrl at the bottom of web/assets/config.json to reflect your local development hostname that was set in your .env file
* By default, BrowserSync will use webpack's HMR, which won't trigger a page reload in your browser. If you would like to force BrowserSync to reload the page whenever certain file types are edited, then add them to watch in web/assets/config.json.

  "watch": [
    "assets/scripts/**/*.js",
    "templates/**/*.php",
    "src/**/*.php"
  ],

## Workflow instructions

* npm start — Compile assets when file changes are made, start BrowserSync session
* npm run build — Compile and optimize the files in your assets directory
* npm run build:production — Compile assets for production

# [Bedrock](https://roots.io/bedrock/)
[![Packagist](https://img.shields.io/packagist/v/roots/bedrock.svg?style=flat-square)](https://packagist.org/packages/roots/bedrock)
[![Build Status](https://img.shields.io/travis/roots/bedrock.svg?style=flat-square)](https://travis-ci.org/roots/bedrock)

Bedrock is a modern WordPress stack that helps you get started with the best development tools and project structure.

Much of the philosophy behind Bedrock is inspired by the [Twelve-Factor App](http://12factor.net/) methodology including the [WordPress specific version](https://roots.io/twelve-factor-wordpress/).

## Features

* Better folder structure
* Dependency management with [Composer](http://getcomposer.org)
* Easy WordPress configuration with environment specific files
* Environment variables with [Dotenv](https://github.com/vlucas/phpdotenv)
* Autoloader for mu-plugins (use regular plugins as mu-plugins)
* Enhanced security (separated web root and secure passwords with [wp-password-bcrypt](https://github.com/roots/wp-password-bcrypt))

Use [Trellis](https://github.com/roots/trellis) for additional features:

* Easy development environments with [Vagrant](http://www.vagrantup.com/)
* Easy server provisioning with [Ansible](http://www.ansible.com/) (Ubuntu 14.04, PHP 7, MariaDB)
* One-command deploys

See a complete working example in the [roots-example-project.com repo](https://github.com/roots/roots-example-project.com).

## Requirements

* PHP >= 5.6
* Composer - [Install](https://getcomposer.org/doc/00-intro.md#installation-linux-unix-osx)

## Installation

1. Create a new project in a new folder for your project:

  `composer create-project roots/bedrock your-project-folder-name`

2. Copy `.env.example` to `.env` and update environment variables:
  * `DB_NAME` - Database name
  * `DB_USER` - Database user
  * `DB_PASSWORD` - Database password
  * `DB_HOST` - Database host
  * `WP_ENV` - Set to environment (`development`, `staging`, `production`)
  * `WP_HOME` - Full URL to WordPress home (http://example.com)
  * `WP_SITEURL` - Full URL to WordPress including subdirectory (http://example.com/wp)
  * `AUTH_KEY`, `SECURE_AUTH_KEY`, `LOGGED_IN_KEY`, `NONCE_KEY`, `AUTH_SALT`, `SECURE_AUTH_SALT`, `LOGGED_IN_SALT`, `NONCE_SALT`

  If you want to automatically generate the security keys (assuming you have wp-cli installed locally) you can use the very handy [wp-cli-dotenv-command][wp-cli-dotenv]:

      wp package install aaemnnosttv/wp-cli-dotenv-command

      wp dotenv salts regenerate

  Or, you can cut and paste from the [Roots WordPress Salt Generator][roots-wp-salt].

3. Add theme(s) in `web/app/themes` as you would for a normal WordPress site.

4. Set your site vhost document root to `/path/to/site/web/` (`/path/to/site/current/web/` if using deploys)

5. Access WP admin at `http://example.com/wp/wp-admin`

## Deploys

There are two methods to deploy Bedrock sites out of the box:

* [Trellis](https://github.com/roots/trellis)
* [bedrock-capistrano](https://github.com/roots/bedrock-capistrano)

Any other deployment method can be used as well with one requirement:

`composer install` must be run as part of the deploy process.

## Documentation

Bedrock documentation is available at [https://roots.io/bedrock/docs/](https://roots.io/bedrock/docs/).

## Contributing

Contributions are welcome from everyone. We have [contributing guidelines](https://github.com/roots/guidelines/blob/master/CONTRIBUTING.md) to help you get started.

## Community

Keep track of development and community news.

* Participate on the [Roots Discourse](https://discourse.roots.io/)
* Follow [@rootswp on Twitter](https://twitter.com/rootswp)
* Read and subscribe to the [Roots Blog](https://roots.io/blog/)
* Subscribe to the [Roots Newsletter](https://roots.io/subscribe/)
* Listen to the [Roots Radio podcast](https://roots.io/podcast/)

[roots-wp-salt]:https://roots.io/salts.html
[wp-cli-dotenv]:https://github.com/aaemnnosttv/wp-cli-dotenv-command
