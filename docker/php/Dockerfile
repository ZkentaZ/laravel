FROM php:7.4-fpm

RUN cd /usr/bin && curl -s https://getcomposer.org/installer | php && ln -s /usr/bin/composer.phar /usr/bin/composer

RUN apt-get update && \
    apt-get install -y git unzip libzip-dev libicu-dev libonig-dev && \
    docker-php-ext-install intl pdo_mysql zip bcmath

COPY ./docker/php/php.ini /usr/local/etc/php/php.ini
COPY --from=composer:2.0 /usr/bin/composer /usr/bin/composer

RUN composer create-project laravel/laravel app

WORKDIR /usr/share/nginx/html/

## create laravel project ##
## ex ) composer create-project laravel/laravel project_name
# RUN composer create-project laravel/laravel app