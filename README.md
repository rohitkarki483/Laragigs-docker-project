# LaraGigs - Dockerized Laravel Application

## Project Overview

This project focuses on the DevOps and Orchestration of a Laravel-based job listing platform. While the application layer (LaraGigs) is based on an existing Laravel project [LaraGigs repository by Brad Traversy](https://github.com/bradtraversy/laragigs) and implemented a custom-built containerized environment. This setup ensures that the application is portable, scalable, and easy to deploy across any system using Docker.

##  Key Implementation Features:
**Docker Containerization:** Created custom Docker images for the application environment.

**Orchestration:** Used Docker Compose to manage multi-container services.

**Nginx Reverse Proxy:** Configured Nginx to handle web requests and serve as a gateway to the PHP-FPM container.

**Database Integration:** Implemented a persistent MySQL container for data storage.

## Docker Setup
* **Docker** and **Docker Compose** installed on your machine.
* **Git** installed.
### 1. Installation & Environment Setup
I Clone the repository and move into the directory:

```bash
git clone [https://github.com/rohitkarki483/Laragigs-docker-project.git](https://github.com/rohitkarki483/Laragigs-docker-project.git)
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
```
#Seeding The Database

To add the dummy listings with a single user, run:
```bash
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
