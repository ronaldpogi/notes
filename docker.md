# Commands

## Important Commands

## 🐳 Docker

### 🔹 Container Management
```bash
docker ps                     # list running containers
docker ps -a                  # list all containers (including stopped)
docker-compose up -d          # start all services in background
docker-compose up -d --build  # rebuild images and start services
docker-compose down           # stop and remove containers, networks, volumes
docker-compose restart        # restart all containers
docker-compose logs -f        # follow logs of all services
docker-compose logs -f backend  # follow logs of Laravel container
docker-compose logs -f frontend # follow logs of Vue container
```

### 🔹 Accessing Containers
```bash
docker exec -it backend bash      # enter Laravel container
docker exec -it frontend bash     # enter Vue container
docker exec -it pgdb psql -U youruser -d yourdb  # connect to Postgres DB
```

### 🔹 Laravel (inside container or via exec)
```bash
docker exec -it backend php artisan migrate     # run migrations
docker exec -it backend php artisan db:seed     # seed database
docker exec -it backend php artisan tinker      # interactive REPL
docker exec -it backend php artisan route:list  # show routes
docker exec -it backend composer install        # install dependencies
docker exec -it backend composer update         # update dependencies
```

### 🔹 Vue 3 (inside container or via exec)
```bash
docker exec -it frontend npm install   # install dependencies
docker exec -it frontend npm run dev   # run dev server
docker exec -it frontend npm run build # build production assets
docker exec -it frontend npm run lint  # run linter
```

### 🔹 Volumes & Images
```bash
docker volume ls                # list volumes
docker volume rm <volume_name>  # remove volume (useful if DB reset needed)
docker image ls                 # list images
docker image prune -a           # remove unused images
```

### 🔹 Database Reset (Postgres Example)
```bash
docker exec -it pgdb psql -U postgres -c "DROP DATABASE laravel;"
docker exec -it pgdb psql -U postgres -c "CREATE DATABASE laravel;"
docker exec -it backend php artisan migrate --seed
```
