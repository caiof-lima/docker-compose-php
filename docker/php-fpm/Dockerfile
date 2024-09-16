FROM php:8.1-fpm

RUN apt-get update \
    && apt-get upgrade -y\
    && apt-get install libicu-dev libxml2-dev -y\
    && docker-php-ext-install -j$(nproc) intl soap opcache pdo_mysql mysqli 

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Install and configure xdebug 
RUN pecl install xdebug \
    && docker-php-ext-enable xdebug \
    && printf 'zend_extension=xdebug \n\
    xdebug.mode = debug \n\
    xdebug.discover_client_host = 1 \n\
    xdebug.log=/tmp/xdebug.log \n\
    xdebug.start_with_request=yes' > /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
    && touch /tmp/xdebug.log
