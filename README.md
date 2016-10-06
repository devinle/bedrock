# [WP Starter](https://github.com/devinle/bedrock)

Fork that adds functionality and extends to Roots/Bedrock. We use this as a starter shell to quickly get up and running with Bedrock using Sage. Original repo is set as Upstream and can be sync'd back if necessary.

* Enabled major versioning of WP via Composer
* Added Better WP Security as a requirement
* Added W3 Total cache as a requirement
* Added WP SEO as a requirement
* Added submodule to Sage theme

NOTE: There is a composer-with-add-ons.json file. Typically we use [ACF Pro](https://www.advancedcustomfields.com/), [WP Migrate DB Pro](https://deliciousbrains.com/wp-migrate-db-pro/) and [WP Offload S3](https://deliciousbrains.com/wp-offload-s3/) which are included in the composer-with-add-ons.json file. If you have purchased a license for these add-ons, you can remove your composer.json file and rename the composer-with-add-ons.json file to composer.json. Next, you should update the following:

To use ACF you must add the following to your .env file

* ACF_PRO_KEY=YOUR_KEY_HERE

To use WP Migrate DB Pro you must update the following settings in your newly renamed composer.json file for all occurances of Migrate DB packages.
* ?licence_key=YOUR_KEY_HERE&site_url=yoursite.com

To use WP Offload S3 you must update the following settings in your newly renamed composer.json file for all occurances of S3 packages.
* ?licence_key=YOUR_KEY_HERE&site_url=yoursite.com

## [WP Starter > Sage Submodule](https://github.com/devinle/sage)

Fork that adds functionality and extends to Roots/Sage theme. Original repo is set as Upstream and can be sync'd back if necessary.

* Removed all SCSS files except for a main and common/buttons starter (required to have some KSS commenting so included to bootstrap project)
* Removed all bootstrap references in JS and Styles
* Added new cleanup file to remove extra unwanted wordpress markup from output templates (web/app/themes/sage/lib/cleanup.php)
* Added new editor file to add extra TinyMCE custom capabilities - commented out for now (web/app/themes/sage/lib/editor.php)
* Added KSS webpack plugin for living styleguide
* Added submodule for KSS workflow called ed-kss-template
* Removed jQuery

## [Sage > ED KSS Template Submodule](https://dleggett@bitbucket.org/enginedigital/ed-kss-template.git)

Soon to be custom KSS template built into the Sage WP theme webpack workflow.

* Added webpack plugin dependency for live stylesheets.

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

You must be on PHP 5.6 minimum!

* cd into root directory
* run composer install
* setup new MAMP and point to web dir
* setup a local database
* copy .env.sample -> .env and enter credentials and remember to add your salts!
* cd into sage theme root directory and run npm install, then run composer install
* load up your Mamp dev URL in browser and run WP setup
* log in and choose Appearance and set it to Sage Starter Theme
* To use BrowserSync during npm start you need to update devUrl at the bottom of web/app/themes/sage/assets/build/config.json to reflect your local development hostname that was set in your .env file

## Workflow instructions

You must be on the latest stable node version!

The following workflow commands should be run from the sage theme root folder.

* npm start — Compile assets when file changes are made, start BrowserSync session
* npm run build — Compile and optimize the files in your assets directory
* npm run build:production — Compile assets for production

# [See original Bedrock repo for more details](https://roots.io/bedrock/)
