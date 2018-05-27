FROM php:5.6.36-apache
MAINTAINER levin7
RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng-dev \
        BZip2 libbz2-dev \
        libicu-dev \
        libxml2 libxml2-dev \
    && docker-php-ext-install -j$(nproc) mcrypt bcmath calendar bz2 intl mysqli pdo_mysql mysql soap sockets exif wddx zip gettext \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd
RUN pecl install igbinary-2.0.6 && docker-php-ext-enable igbinary
RUN apt-get install -y libmemcached-dev zlib1g-dev \
    && pecl install memcached-2.2.0 \
    && docker-php-ext-enable memcached
RUN pecl install xdebug-2.5.5 && docker-php-ext-enable xdebug
RUN pecl install redis-4.0.2 && docker-php-ext-enable redis
EXPOSE 80