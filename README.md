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

-   **Container Name**: fastapi_app
-   **Port**: 8000
-   **Dependencies**: PostgreSQL (db service)
-   **Environment File**: ./backend/.env

### Frontend (ReactJS)

-   **Container Name**: nodejs_app
-   **Port**: 5173
-   **Environment File**: ./frontend/.env

### Database (PostgreSQL)

-   **Container Name**: postgres_db
-   **Port**: 5432
-   **Volumes**: postgres_data:/var/lib/postgresql/data
-   **Environment File**: ./backend/.env

### Adminer (Database Management)

-   **Container Name**: adminer
-   **Port**: 8080

### Nginx Proxy Manager

-   **Container Name**: nginx_proxy_manager
-   **Ports**: 80 (HTTP), 443 (HTTPS), 81 (Proxy Manager)
-   **Volumes**: ./data:/data, ./letsencrypt:/etc/letsencrypt
-   **Environment**: DB_SQLITE_FILE="/data/database.sqlite"
-   **Dependencies**: PostgreSQL (db service), Backend (fastapi_app), Frontend (nodejs_app), Adminer

## Setup Instructions

### Prerequisites

-   Docker
-   Docker Compose

### Getting Started

1.  **Clone the repository:**
    
   
    
    `git clone https://github.com/Laban254/devops-stage-2
    cd Laban254/devops-stage-2` 
    
2.  **Build and start the services:**
    
   
    
    `docker-compose up -d` 
    
3.  **Verify the services are running:**
    
    -   FastAPI Backend: [http://localhost:8000](http://localhost:8000)
    -   ReactJS Frontend: [http://localhost:5173](http://localhost:5173)
    -   PostgreSQL Database: Accessible on port 5432 (no direct browser access)
    -   Adminer: [http://localhost:8080](http://localhost:8080)
    -   Nginx Proxy Manager: http://localhost:81

## Accessing the Application

-   **Localhost**: You can access the application via the above URLs for each service.
-   **Custom Domain**: If you have set up a custom domain, configure it using the Nginx Proxy Manager.
