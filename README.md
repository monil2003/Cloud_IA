# IA 
# Dockerfile (for backend)

1. `
   FROM ubuntu:20.04
   `

   - **FROM**: Specifies the base image to build upon. In this case, it's Ubuntu 20.04.

3. ```
   LABEL maintainer="monil.dce21@sot.pdpu.ac.in"
   LABEL description="Apache / PHP development environment"
   ```

   - **LABEL**: Adds metadata to the image. It provides information about the maintainer and a brief description of the image.

4. ```
   ARG DEBIAN_FRONTEND=newt
   RUN apt-get update && apt-get install -y lsb-release && apt-get clean all
   RUN apt install ca-certificates apt-transport-https software-properties-common -y
   RUN add-apt-repository ppa:ondrej/php
   ```

   - **ARG**: Defines a build argument that can be used during the image build process.
   - **RUN**: Executes commands in the image during the build process. These commands update the package lists, install required packages, and add a repository for PHP packages.

5. ```
   RUN apt-get -y update && apt-get install -y \
   apache2 \
   php8.0 \
   libapache2-mod-php8.0 \
   php8.0-bcmath \
   php8.0-gd \
   php8.0-sqlite \
   php8.0-mysql \
   php8.0-curl \
   php8.0-xml \
   php8.0-mbstring \
   php8.0-zip \
   mcrypt \
   nano
   ```

   - **RUN**: Installs necessary packages including Apache2, PHP 8.0, and various PHP extensions for common web development tasks.

6. ```
   RUN apt-get install locales
   RUN locale-gen fr_FR.UTF-8
   RUN locale-gen en_US.UTF-8
   RUN locale-gen de_DE.UTF-8
   ```

   - **RUN**: Installs locales package and generates locale settings for French, English, and German.

7. ```
   RUN sed -i -e 's/^error_reporting\s*=.*/error_reporting = E_ALL/' /etc/php/8.0/apache2/php.ini
   RUN sed -i -e 's/^display_errors\s*=.*/display_errors = On/' /etc/php/8.0/apache2/php.ini
   RUN sed -i -e 's/^zlib.output_compression\s*=.*/zlib.output_compression = Off/' /etc/php/8.0/apache2/php.ini
   ```

   - **RUN**: Modifies PHP configuration files to set error reporting to display all errors, turn on error display, and disable zlib output compression.

8. ```
   ENV TERM xterm
   ```

   - **ENV**: Sets an environment variable `TERM` to `xterm`.

10. ```
    RUN a2enmod rewrite
    RUN echo "ServerName localhost" >> /etc/apache2/apache2.conf
    RUN sed -i '/<Directory \/var\/www\/>/,/<\/Directory>/ s/AllowOverride None/AllowOverride All/' /etc/apache2/apache2.conf
    ```

   - **RUN**: Enables Apache `mod_rewrite`, adds a ServerName to Apache configuration, and allows `.htaccess` files to override settings.

11. ```
    RUN chgrp -R www-data /var/www
    RUN find /var/www -type d -exec chmod 775 {} +
    RUN find /var/www -type f -exec chmod 664 {} +
    ```

   - **RUN**: Sets appropriate permissions for the `/var/www` directory to ensure proper file access by the web server.

11. ```
    EXPOSE 80
    ```

    - **EXPOSE**: Exposes port 80 to allow access to the Apache web server running inside the container.

13. ```
    CMD ["/usr/sbin/apache2ctl","-DFOREGROUND"]
    ```

    - **CMD**: Specifies the command to run when the container starts. In this case, it starts the Apache2 server in the foreground.


# docker-compose.yml (for containerization and complete built)



***

# Dockerized Multi-Architecture Web Application (CLOUD IA)

This is a Dockerized web application project consisting of three main components:

1. **Frontend**: Apache HTTP Server serving static files.
2. **Backend**: Custom application backend built using a Dockerfile.
3. **Database**: MySQL database accessed via phpMyAdmin.

## Prerequisites

Before you begin, ensure you have the following installed on your system:

- Docker: [Installation guide](https://docs.docker.com/get-docker/)
- Docker Compose: [Installation guide](https://docs.docker.com/compose/install/)

## Getting Started

1. Clone this repository to your local machine:

    ```bash
    git clone https://github.com/your_username/your_repository.git
    cd your_repository
    ```

2. Place the provided `docker-compose.yml` and `Dockerfile` files in the root directory of the project.

3. Build and start the Docker containers:

    ```bash
    docker-compose up --build
    ```

4. Access the application in your web browser:

    - Frontend: [http://localhost:3000](http://localhost:3000)
    - Backend: [http://localhost:5000](http://localhost:5000)
    - phpMyAdmin: [http://localhost:8080](http://localhost:8080)

## Components

### Frontend

The frontend of the application is served by Apache HTTP Server. Place your static files (HTML, CSS, JavaScript, etc.) in the `frontend` directory.

### Backend

The backend files are stored in the `api` directory. The backend is a custom application built using the Dockerfile provided. You can modify the Dockerfile to suit your backend application's requirements.

### Database

The database used in this project is MySQL, which is accessed and managed via phpMyAdmin. The database files are stored in the `db` directory.

## Configuration

You can customize the configuration of each component by modifying the respective configuration files (`frontend/index.html` for frontend, `Dockerfile` for backend, `docker-compose.yml` for services configuration).

## License

This project is licensed under the [MIT License](LICENSE).

## Acknowledgements

- [Docker](https://www.docker.com/) - For containerization technology.
- [Apache HTTP Server](https://httpd.apache.org/) - For serving the frontend.
- [MySQL](https://www.mysql.com/) - For the database management system.
- [phpMyAdmin](https://www.phpmyadmin.net/) - For database administration.
- [Building a Simple 3-Tier Architecture with Docker Compose: A Hands-On Project Journey](https://medium.com/@kesaralive/getting-started-with-docker-compose-hands-on-project-experience-e562ab07e24c) - For refernce
  

