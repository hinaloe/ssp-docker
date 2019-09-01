FROM php:7.3-fpm-alpine

RUN apk update && apk add --no-cache libzip-dev freetype libpng libpng-dev libjpeg-turbo freetype-dev libjpeg-turbo-dev git autoconf build-base\
  && pecl install xdebug\
  && docker-php-ext-configure gd \
    --with-gd \
    --with-freetype-dir=/usr/include/ \
    --with-png-dir=/usr/include/ \
    --with-jpeg-dir=/usr/include/ \
    && NPROC=$(grep -c ^processor /proc/cpuinfo 2>/dev/null || 1) \
    && docker-php-ext-install -j${NPROC} gd pdo_mysql bcmath zip\
    && docker-php-ext-enable xdebug \ 
    && rm -rf /var/cache/apk/*
