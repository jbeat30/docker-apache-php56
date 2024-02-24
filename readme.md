# Dockerized PHP 5.6 with Apache

This Dockerfile sets up a PHP 5.6 environment with Apache, suitable for local development.
You can find the pre-built Docker image on Docker Hub at [jbeat/apache-php](https://hub.docker.com/repository/docker/jbeat/apache-php/general).
## Usage

1. **Pull the Docker image:**

    ```bash
    docker pull jbeat/apache-php:5.6.0
    ```
2. **Selective type docker-compose.yaml:**

   ```yaml
   version: '3'
   services:
    webserver:
    image: jbeat/apache-php:5.6.0
    container_name: container-name
    ports:
      - "8080:80"
    volumes:
      - ".:/var/www/html"
   ```
   
     ```bash
      docker-compose up -d --build
     ```

3. **Selective type Run the Docker container:**

   ```bash
    docker run -d --name [container-name] -p 8080:80 -v $(pwd):/var/www/html jbeat/apache-php:5.6.0
   ```

   Replace `[container-name]` with a desired name for your container and
   `8080` with the desired host port. The `-v` option mounts the current
   directory (`$(pwd)`) to the container's `/var/www/html` directory,
   allowing you to easily sync your local code with the container.


4. **Access the PHP application:**

   Open your web browser and go to [http://localhost:8080](http://localhost:8080) (or the port you specified).

## Features

- Apache configured for local development.
- PHP version: 5.6.
- Apache configured with rewrite module (enabled) and mpm_prefork.
- PHP extensions: mysqli, pdo_mysql, gettext, mbstring.
- Timezone set to Asia/Seoul.
- Short tags are enabled.
- Composer is installed for managing PHP dependencies.
- Options FollowSymLinks and AllowOverride All are set in the Apache configuration.
- Require all granted Give all users full access to the contents of the directory for development environment.

## Author

This Dockerfile is maintained by `jbeat`.

## Base Image

This Docker image is based on the official `php:5.6-apache` image.

## Apache Configuration

The Apache configuration is customized for local development.

## Cleanup

To minimize the image size, unnecessary files are removed during the Docker image build

