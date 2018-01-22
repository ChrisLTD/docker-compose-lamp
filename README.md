# docker-compose-lamp
A simple set of dockers for running a local LAMP
- Apache 2.4
- PHP 7.0
- MariaDB 10.1

## General Usage Information

By default this mounts the `/var/www/html` directory to `./app` on your host OS.  It is intended to keep all of the web application files outside of the containers so you can easily work on the files. The database files are mounted to the `./data` directory.

The database hostname is set to `db`.

### To run the containers

`docker-compose up -d` (Starts the Containers)


### Accessing the web server

Navigate to [http://localhost:8888](http://localhost:8888)

