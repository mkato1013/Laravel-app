FROM php:8.0-apache

ENV APACHE_DOCUMENT_ROOT /var/www/html/laravel/public
RUN sed -ri -e 's!/var/www/html!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/sites-available/*.conf
RUN sed -ri -e 's!/var/www/!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/apache2.conf /etc/apache2/conf-available/*.conf


RUN apt-get update && apt-get install -y libonig-dev && \
  docker-php-ext-install pdo_mysql mysqli mbstring

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN cd /etc/apache2/mods-enabled \
&& ln -s ../mods-available/rewrite.load

RUN apt-get update && apt-get install -y git zip unzip

# COPY ../000-default.conf /etc/apache2/sites-available/000-default.conf


# RUN sed -i 's!/var/www/html!/var/www/html/public!g' /etc/apache2/sites-available/000-default.conf