# IA 
# Dockerfile (for backend)

The database files are stored in the `db` directory.

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
  

