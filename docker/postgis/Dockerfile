FROM composer:2.4.3 as sail-vendor
COPY composer.* ./
RUN composer init --no-interaction --name temp/temp --require laravel/sail:^1.0.1 \
    && composer install --no-interaction --prefer-dist


FROM postgis/postgis:14-3.3
COPY --from=sail-vendor /app/vendor/laravel/sail/database/pgsql/create-testing-database.sql /docker-entrypoint-initdb.d/
