FROM php:7.3.0-apache

RUN docker-php-ext-install \
    pdo_mysql \
    && a2enmod \
    rewrite