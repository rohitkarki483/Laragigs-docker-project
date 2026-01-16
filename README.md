# LaraGigs - Dockerized Laravel Application

## Project Overview
This project is all about the DevOps & Orchestration of a Laravel-based job posting website. Although my application layer is built upon the existing work of the LaraGigs repository on Github maintained by Brad Traversy (https://github.com/bradtraversy/laragigs) , The focus of this project is  deployed an application in a production-like environment where each service runs in its own container, ensuring scalability, portability, and consistency across different systems.

---

## Tech Stack
* **Backend Framework:** Laravel
* **Web Server:** Nginx
* **Application Runtime:** PHP-FPM
* **Database:** MySQL
* **Containerization & Orchestration:** Docker & Docker Compose

---
## Architecture Overview

Client Browser
      |
      v
   Nginx (Reverse Proxy)
      |
      v
  PHP-FPM (Laravel App)
      |
      v
   MySQL (Database)


---

## Project Structure

This project follows a standard Laravel structure, with the addition of custom orchestration and configuration files for Docker:

```text
├── nginx/                  # Nginx configuration (Reverse Proxy)
│   └── default.conf        # Server block setup for PHP-FPM
├── storage/                # Laravel storage (mapped as a volume)
├── Dockerfile              # Instructions for building the PHP-FPM image
├── docker-compose.yml      # Orchestration file for all services
├── .env.example            # Template for environment variables
├── artisan                 # Laravel CLI tool
├── README.md               # Project documentation
└── ... (Rest of Laravel Application)
```

---

## Prerequisites
 the following tools should be installed on your system:
* Docker
* Docker Compose
* Git

---

## Setup Instructions
### 1. Clone the repository

```bash
git clone https://github.com/rohitkarki483/Laragigs-docker-project.git
cd Laragigs-docker-project
```
### 2. Configure Environment Variables
Copy the example environment file:
```bash
cp .env.example .env
```

 Update database credentials in .env:
```bash
DB_CONNECTION=mysql
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=laravel_db
DB_USERNAME=laravel_user
DB_PASSWORD=laravel_pass
```
---

### 3. Build & Run the Containers
```bash
docker compose up -d
```
## 4. Application Initialization

Run the following commands to initialize the Laravel application inside the container: 
```bash
#Install PHP dependencies
docker exec -it laravel-app composer install

# Generate the application key:
docker exec -it laravel-app php artisan key:generate

# Run Migration
docker exec -it laravel-app php artisan migrate

#Seeding The Database
docker exec -it laravel-app php artisan db:seed

# Create storage symlink
docker exec -it laravel-app php artisan storage:link
```
---

### 5. Access the Application
access the application in your browser:
```bash
http://localhost
```

---

### 5. Stopping the Application
To stop and remove the containers:
```bash
docker compose down
```
---

## Conclusion
This project demonstrates the implementation of a DevOps process in deploying a Laravel web app utilizing Docker.The setup focuses on container orchestration and reproducibility, aligning with modern industry best practices for scalable and maintainable deployments.


