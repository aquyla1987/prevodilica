FROM php:8.1-fpm-alpine

RUN docker-php-ext-install pdo pdo_mysql

# dozvoli superuser-a env varijabla
ENV COMPOSER_ALLOW_SUPERUSER=1

# composer image
COPY --from=composer:2.4 /usr/bin/composer /usr/bin/composer

# composer.json i composer.lock datoteke
COPY ./app/composer.* ./

# instalacija
RUN composer install --prefer-dist --no-dev --no-scripts --no-progress --no-interaction

# kopiranje app datoteka u working folder
COPY ./app .

# composer dump-autoload
RUN composer dump-autoload --optimize