# docker-compose-lamp
A simple set of dockers for running a local LAMP
- Apache 2.4
- PHP 7.0
- MariaDB 10.1

## General Usage Information

By default this mounts the /var/www/html directory to ./app on your host OS.  It is intended to keep all of the web application files outside of the containers so you can easily work on the files. The database files are persisted to the ./data directory.

The database hostname is set to `db`.

## Setup

If your running Ubuntu or Fedora as your local development environment you should create a user and group and folder to match the permission of the ~/public_html folder with the container's Apache user/group. The Apache runs as UID and GUID 33 (www-data).

`sudo useradd -u 33 www-data; sudo groupadd www-data -g 33; sudo usermod -g 33 www-data` (If you already have a group with GID 33, that is ok this command will fail)

`sudo usermod -aG 33 your_username;`

*now logout/login of linux as it is needed for the new permissions to take effect.

### To run the containers

`docker-compose up -d` (Starts the Containers)

## Example Fresh Drupal install:

`cd ~/public_html; drush dl drupal-7; mv ~/public_html/drupal*/* ~/public_html; mv ~/public_html/drupal*/.htaccess ~/public_html/drupal*/.gitignore ~/public_html; rm -rf drupal-*`

`sudo chown -R 33:33 ~/public_html`

`drush site-install standard --db-url='mysql://root:docker@172.17.0.2/drupaldb' --site-name=Example`

### Accessing the web server

Navigate to [http://localhost:8888](http://localhost:8888)

