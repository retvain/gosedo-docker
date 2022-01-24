## Docker for gas-api project

## to run:
### clone to parent directory gas-api
`cd gas-docker`

`docker-compose up -d`

`docker-compose exec php-fpm composer install`

`docker-compose exec php-fpm php artisan migrate:refresh --seed --force`
