## Docker for gas-api project

## to run:
### clone to parent directory gas-api
`cd gas-docker`

`docker-compose up nginx php-fpm postgres`

`docker-compose exec php-fpm bash`

`cd gas-api-operator-arm`
`composer install`
`php artisan migrate:refresh --seed --force`

`cd ../gas-api-operator-arm`
`composer install`
`php artisan migrate:refresh --seed --force`

## to run version-applier service:
`docker-compose up version-applier`
