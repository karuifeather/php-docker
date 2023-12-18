FROM php:8.3-fpm-alpine as app

# php extention installed image
COPY --from=mlocati/php-extension-installer /usr/bin/install-php-extensions /usr/local/bin/

# exit on errors, exit on unset variables, print every command as it is executed
RUN set -eux; \
  install-php-extensions pdo pdo_mysql;

# allow super user
ENV COMPOSER_ALLOW_SUPERUSER=1

# get composer
COPY --from=composer:2.6 /usr/bin/composer /usr/bin/composer

# using docker cache for composer install
COPY ./app/composer.* ./

# install
RUN composer install --prefer-dist --no-dev --no-scripts --no-progress --no-interaction

# copying source files to the working directory
COPY ./app .

# regenerate and optimize autoload files for better performance with Composer
RUN composer dump-autoload --optimize

############################
# second stage build for dev
FROM app as app_dev

# set to 'debug' when debugging
ENV XDEBUG_MODE=debug

# Copy xdebug config file into container
COPY ./php/conf.d/xdebug.ini /usr/local/etc/php/conf.d/xdebug.ini

# Install xdebug
RUN set -eux; \
  install-php-extensions xdebug

