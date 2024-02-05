# laravel-docker
Build project laravel with docker use Apache, Nginx, CentOS

### PHP scripts
_Make sure the web service is running_

## If you are running docker-compose with Apache or Nginx, use the command below:

#### Installation dependencies
```
docker-compose exec web composer install
```

#### Generation APP_KEY
```
docker-compose exec web php artisan key:generate
```

#### Save configuration
```
docker-compose exec web php artisan config:cache
```

#### Migration
```
docker-compose exec web php artisan migrate
```

## If you are running docker-compose with centOS, use the command below:

#### Start bash shell in the specified directory
```
docker-compose exec web bash -c "cd /var/www/html/ && bash"
```

#### Installation dependencies
```
composer install
```

#### Generation APP_KEY
```
php artisan key:generate
```

#### Save configuration
```
php artisan config:cache
```

#### Migration
```
php artisan migrate
```

#### Exit bash
```
exit
```
