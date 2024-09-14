FROM php:8.1-fpm
RUN apt-get update \
    && apt-get upgrade -y\
    && apt-get install libicu-dev libxml2-dev -y\
    && docker-php-ext-install -j$(nproc) intl soap opcache pdo_mysql mysqli 

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Install and enable xdebug 
RUN pecl install xdebug \
    && docker-php-ext-enable xdebug
RUN touch /tmp/xdebug.log
