# Full-Stack FastAPI and React Template

Welcome to the Full-Stack FastAPI and React template repository. This repository serves as a demo application for interns, showcasing how to set up and run a full-stack application with a FastAPI backend and a ReactJS frontend using ChakraUI.

## Project Structure

The repository is organized into two main directories:

- **frontend**: Contains the ReactJS application.
- **backend**: Contains the FastAPI application and PostgreSQL database integration.

Each directory has its own README file with detailed instructions specific to that part of the application.

## Getting Started

To get started with this template, please follow the instructions in the respective directories:

- [Frontend README](./frontend/README.md)
- [Backend README](./backend/README.md)

## Services Overview

### Backend (FastAPI)

-   **Container Name**: `fastapi_app`
-   **Port**: `8000`
-   **Dependencies**: PostgreSQL (`db` service)
-   **Environment Variables**: Configured in `docker-compose.yml`

### Frontend (ReactJS)

-   **Container Name**: `nodejs_app`
-   **Port**: `5173`
-   **Environment Variables**: Configured in `docker-compose.yml`

### Database (PostgreSQL)

-   **Container Name**: `postgres_db`
-   **Port**: `5432`
-   **Volumes**: `postgres_data:/var/lib/postgresql/data`
-   **Environment Variables**: Configured in `docker-compose.yml`

### Adminer (Database Management)

-   **Container Name**: `adminer`
-   **Port**: `8080`

### Nginx Proxy Manager

-   **Container Name**: `nginx_proxy_manager`
-   **Ports**: `80 (HTTP)`, `443 (HTTPS)`, `81 (Proxy Manager)`
-   **Volumes**:
    -   `./proxy/data:/data`
    -   `./proxy/letsencrypt:/etc/letsencrypt`
-   **Dependencies**:
    -   PostgreSQL (`db` service)
    -   Backend (`fastapi_app`)
    -   Frontend (`nodejs_app`)
    -   Adminer

## Setup Instructions

### Prerequisites

-   Docker
-   Docker Compose

### Getting Started

1.  **Clone the repository:**
    
   
    
    `git clone https://github.com/Laban254/devops-stage-2
    cd devops-stage-2` 
    
2.  **Build and start the services:**
    
  
    
    `docker-compose up -d` 
    
3.  **Verify the services are running:**
    
    -   **FastAPI Backend**: [http://localhost:8000](http://localhost:8000)
    -   **ReactJS Frontend**: [http://localhost:5173](http://localhost:5173)
    -   **PostgreSQL Database**: Accessible on port `5432` (no direct browser access)
    -   **Adminer**: [http://localhost:8080](http://localhost:8080)
    -   **Nginx Proxy Manager**: [http://localhost:81](http://localhost:81)

## Accessing the Application

### Localhost

You can access the application via the above URLs for each service.

### Custom Domain

If you have set up a custom domain, configure it using the Nginx Proxy Manager:

1.  **Log in to Nginx Proxy Manager**: [http://localhost:81](http://localhost:81)
2.  **Add a new Proxy Host**:
    -   **Domain Names**: Enter your custom domain (e.g., `kibet.mooo.com`)
    -   **Forward Hostname / IP**: Enter the internal service name (e.g., `fastapi_app`)
    -   **Forward Port**: Enter the internal port (e.g., `8000`)
    -   **SSL**: Enable SSL and provide the necessary certificate files

### Environment Configuration

The services are configured using environment variables in the `docker-compose.yml` file. Make sure to review and update these variables as necessary for your setup.

-   **Backend Environment Variables**:
    -   `BACKEND_CORS_ORIGINS`: List of allowed origins for CORS
    -   `SECRET_KEY`: Secret key for the application
    -   `PROJECT_NAME`: Name of the project
    -   `FIRST_SUPERUSER`: Email of the first superuser
    -   `FIRST_SUPERUSER_PASSWORD`: Password for the first superuser
    -   `USERS_OPEN_REGISTRATION`: Allow open registration
    -   `POSTGRES_SERVER`: PostgreSQL server hostname
    -   `POSTGRES_PORT`: PostgreSQL server port
    -   `POSTGRES_DB`: PostgreSQL database name
    -   `POSTGRES_USER`: PostgreSQL username
    -   `POSTGRES_PASSWORD`: PostgreSQL user password

### Note on Volumes

-   Ensure the volumes specified in the `docker-compose.yml` file exist and have the correct permissions.
-   The volumes for Nginx and the Proxy Manager should be properly set up to ensure persistent data storage.
