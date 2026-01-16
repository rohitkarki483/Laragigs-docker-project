# LaraGigs - Dockerized Laravel Application

## Project Overview
This project is all about the DevOps & Orchestration of a Laravel-based job posting website. Although my application layer is built upon the existing work of the LaraGigs repository on Github maintained by Brad Traversy (https://github.com/bradtraversy/laragigs) , I have designed a customized containerized environment to run it on. It enables me to run the application on any system with ease using Docker.

---

##  Key Implementation Features:
**Docker Containerization:** Custom Docker images were created for the environment of the application.

**Orchestration:** Used Docker Compose to manage multi-container services.

**Nginx Reverse Proxy:** Configured Nginx to handle web requests and serve as a gateway to the PHP-FPM container.

**Database Integration:** Set up a persistent MySQL container for data storage.

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
└── ... (Rest of Laravel Application)
```

---

## Docker Setup
* **Docker** and **Docker Compose** installed on your machine.
* **Git** installed.
### 1. Installation & Environment Setup
I Cloned the repository and move into the directory:

```bash
git clone https://github.com/rohitkarki483/Laragigs-docker-project.git
cd Laragigs-docker-project
```
Prepare the environment file:
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

### 2. Build & Run the Containers

Build and start the application:

```bash
docker compose up -d
```
### 3. Application Initialization
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


### 4. Running The App

Once the containers are running, access the application in your browser:

http://localhost

---

### 5. To stop the containers:
```bash
docker compose down
```
