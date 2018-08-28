# LANDO Drupal 8 #

### What is Lando? ###

It's a free, open source, cross-platform, local development environment and DevOps tool built on Docker container technology, Lando is for developers who want to quickly specify and painlessly spin up the services and tools needed to develop their projects.

Do you want to know more?, visit [https://docs.devwithlando.io/](https://docs.devwithlando.io/)

### Requirements ###

Lando works over Docker which is needed to install lando.

[Install Lando](https://docs.devwithlando.io/installation/installing.html)

### How do I get set up? ###

0- [Install Lando](https://docs.devwithlando.io/installation/installing.html) in your local machine.
1. You can check out this repo by typing this command: `git clone https://github.com/alejomc/drupal8-lando.git`.
2. Open the project folder and build Lando typing : `lando start`.
3. This repo assumes there is a existing project in `docroot/` folder an has a `composer.json` file. Require project dependencies: `lando composer install`.
4. Load the database, you can import a database using this lando command `lando db-import DATABASE.sql.gz`, i.e: `lando db-import mariadb/sql/sitename_2018-08-03.sql.gz`
5. Verify the Drupal CMS settings. review `settings.php`, `settings.local.php`
6. Run Drupal Updates & configurations by typing: `lando cms-update`.
7. Done!, you could now visit your site at: `http://mydrupalsite.lndo.site` (You could see other URLs at the end of each lando build), feel free to change your lando site name.


### Lando commands ###

#### General Commands ####

Each Lando Drupal 8 recipe will also ship with helpful dev utilities. This means you can use things like drush, drupal, composer and php-cli via Lando and avoid mucking up your actual computer trying to manage php versions and tooling.

| Command           | Description |
| ----------------- | ------------- |
| lando composer    | Run composer commands  |
| lando db-import <file>   | Import <file> into database. File is relative to approot.  |
| lando db-export   | Export a database. Resulting file: {DB_NAME}.TIMESTAMP.gz |
| lando drupal      | Run drupal console commands |
| lando drush       | Run drush commands |
| lando mysql       | Drop into a MySQL shell |
| lando php         | Run php commands |

examples:

* `lando composer install`
* `lando composer update nothing`
* `lando drush cr`
* `lando drupal generate:module`
* `lando php -v`

#### CMS Commands ####

| Command           | Description |
| ----------------- | ------------- |
| lando cms-update    | Build composer dependencies, import config and run database updates  |



#### Front End Commands ####

| Command           | Description |
| ----------------- | ------------- |
| lando node    | Run node commands  |
| lando npm  | Run npm commands  |
| lando gulp  | Run gulp commands  |
| lando sass  | Run sass commands  |


#### phpMyAdmin ####

phpMyAdmin is a free software tool written in PHP, intended to handle the administration of MySQL over the Web and it is included for this project.

URL `http://pma.mydrupalsite.lndo.site/`.

Do not use phpMyAdmin to import and export Database in those cases please use lando commands.

### Altering Lando.yml file ###

You can see lando detailed information by typing `lando info`, and also make changes on the `lando.yml` file to add extra services, change php version or other needs. Once you make a change ensure rebuild the app by`lando rebuild` command, this might take a while.
You can also alter Nginx configurations and php.ini files under `config_lando/` folder. Please follow Drupal 8 recipe documentation [here](https://docs.devwithlando.io/tutorials/drupal8.html).
