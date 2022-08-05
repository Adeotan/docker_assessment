Create a data directory on your host system, ./php/app

The ./php/app:/var/www/html/ part mounts the ./php/app directory from the underlying host system as /var/www/html inside the container, where apache by default will read the data files.

Create a data directory on your host system, ./datadir

The ./datadir:/var/lib/mysql part mounts the ./datadir directory from the underlying host system as /var/lib/mysql inside the container, where MariaDB by default will write its data files.

Create a data directory on your host system, ./mysqlconfdir

If you want to use a customized MariaDB configuration, you can create your alternative configuration file in a directory on the host machine under ./mysqlconfdir as it is already mounted on /etc/mysql/conf.d

The docker compose file has two services configured php-apache-environment and db

php-apache-environment service runs a container which has both apache server and php installed and db service runs a container with mariadb server.

php container exposes port 80 and mariadb container exposes port 3306. We are mapping these ports to ports 80 and 3306 on host system to access the services.

We are building the php image as part of docker compose file to avoid creating image every time there is a change in application code. And, we are using the official mariadb image from the dockerhub.

To bring up the development environment, run below docker compose command:

docker compose up -d

To stop the services, run below docker compose command:

docker compose stop <service name>
