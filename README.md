# LaraGigs app

An app for listing Laravel gigs/jobs. This project is from a YouTuber.


---

## Usage (Docker)

This project is configured to run using **Docker**, **Docker Compose**, **Nginx**, **PHP-FPM**, and **MySQL**.

---

### Database Setup

This app uses **MySQL (Docker container)**.

To use something different, open up `config/database.php` and change the default driver.

For MySQL (Docker):

1. Copy the environment file:
   ```bash
   cp .env.example .env
    ```

2. Update database credentials in .env:
```bash
DB_CONNECTION=mysql
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=laravel_db
DB_USERNAME=laravel_user
DB_PASSWORD=laravel_pass
```
---

### Build & Run the Containers

1. Build and start the application:

```bash
docker compose up -d
```

2. Generate the application key:
```bash
docker exec -it laravel-app php artisan key:generate
```

3. Migrations

i. To create all the necessary tables and columns, run:

```bash
docker exec -it laravel-app php artisan migrate
```
ii. Seeding The Database

To add the dummy listings with a single user, run:
```bash
docker exec -it laravel-app php artisan db:seed
```
---

### File Uploading

When uploading listing files, they go to storage/app/public.

Create a symlink with the following command to make them publicly accessible:
```bash
docker exec -it laravel-app php artisan storage:link
```
### Running The App

Once the containers are running, access the application in your browser:

http://localhost


### To stop the containers:
```bash
docker compose down
```
