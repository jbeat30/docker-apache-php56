# Dockerized PHP 5.6 with Apache

This Dockerfile sets up a PHP 5.6 environment with Apache, suitable for local development.
You can find the pre-built Docker image on Docker Hub at [jbeat/apache-php56](https://hub.docker.com/repository/docker/jbeat/apache-php56/general).

## Usage

1. **Pull the Docker image:**

    ```bash
    docker pull jbeat/apache-php56:latest
    ```

2. **Run the Docker container:**

   ```bash
    docker run -d --name [container-name] -p 8080:80 -v $(pwd):/var/www/html jbeat/apache-php56:latest
   ```

   Replace `[container-name]` with a desired name for your container and
   `8080` with the desired host port. The `-v` option mounts the current
   directory (`$(pwd)`) to the container's `/var/www/html` directory,
   allowing you to easily sync your local code with the container.


3. **Access the PHP application:**

   Open your web browser and go to [http://localhost:8080](http://localhost:8080) (or the port you specified).

## Features

- Apache configured for local development.
- PHP version: 5.6.
- Apache configured with rewrite module (enabled) and mpm_prefork.
- PHP extensions: mysqli, pdo_mysql, gettext, mbstring.
- Timezone set to Asia/Seoul.
- Short tags are enabled.
- Composer is installed for managing PHP dependencies.

## Author

This Dockerfile is maintained by `jbeat`.

## Base Image

This Docker image is based on the official `php:5.6-apache` image.

## Apache Configuration

The Apache configuration is customized for local development.

## Cleanup

To minimize the image size, unnecessary files are removed during the Docker image build

