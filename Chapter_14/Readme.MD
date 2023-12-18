Docker Compose Example for Wordpress using HTTP with MySQL

An example `docker-compose.yml` file for setting up WordPress with MySQL using HTTP. This example uses official Docker images for WordPress and MySQL.

Create a file named `docker-compose.yml` with the following content:

```yaml
version: '3.8'

services:
  wordpress:
    image: wordpress
    ports:
      - "80:80"
    environment:
      WORDPRESS_DB_HOST: mysql
      WORDPRESS_DB_USER: wordpress
      WORDPRESS_DB_PASSWORD: wordpress
      WORDPRESS_DB_NAME: wordpress
    volumes:
      - wordpress:/var/www/html

  mysql:
    image: mysql:5.7
    environment:
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wordpress
      MYSQL_PASSWORD: wordpress
      MYSQL_ROOT_PASSWORD: rootpassword
    volumes:
      - mysql:/var/lib/mysql

volumes:
  wordpress:
  mysql:
```

This `docker-compose.yml` file defines two services: `wordpress` and `mysql`. It also declares two volumes to persist data for WordPress and MySQL.

Explanation:

- The `wordpress` service uses the official WordPress image. It exposes port 80, and environment variables are set to configure the WordPress database connection.

- The `mysql` service uses the official MySQL 5.7 image. Environment variables are set to configure the MySQL database, user, and password.

- Volumes are used to persist data for WordPress and MySQL so that data is not lost when containers are stopped or removed.

To deploy the WordPress application, navigate to the directory where the `docker-compose.yml` file is located and run the following command:

```bash
docker-compose up -d
```

This command will download the necessary images and start the containers in the background. Once the containers are running, you can access the WordPress site by visiting `http://localhost` in your web browser.

To stop the containers, run:

```bash
docker-compose down
```

In a production environment, you should consider using secure passwords, configuring additional settings, and possibly using a reverse proxy with HTTPS for secure communication.

