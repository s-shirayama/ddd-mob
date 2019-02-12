FROM php:7.3.2-apache

RUN apt-get update && apt-get install -y git vim unzip \
  && docker-php-ext-install pdo_mysql mysqli mbstring \
  && apt-get clean

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

WORKDIR /opt/app

ADD composer.json /opt/app

RUN composer install
RUN rm -rf /var/www/html && ln -s /opt/app/slim/public /var/www/html
RUN a2enmod rewrite
