FROM composer:2.4.3 as composer

COPY composer.* ./

RUN set -xe \
 && composer install --no-scripts --no-suggest --no-interaction --prefer-dist --optimize-autoloader --ignore-platform-req=ext-sockets


FROM postgis/postgis:14-3.3
COPY --from=composer /app/vendor/laravel/sail/database/pgsql/create-testing-database.sql /docker-entrypoint-initdb.d/
