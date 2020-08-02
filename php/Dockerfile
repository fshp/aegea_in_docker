FROM php:7.4-fpm-alpine
LABEL maintainer "Pavel Pavlenko <region23@gmail.com>, Maxim Moseychuk <franchesko.salias.hudro.pedros@gmail.com>"

RUN apk update && apk upgrade

RUN apk add --no-cache freetype libpng libjpeg-turbo freetype-dev libpng-dev libjpeg-turbo-dev oniguruma-dev && \
  docker-php-ext-configure gd \
  --with-freetype \
  --with-jpeg && \
  NPROC=$(grep -c ^processor /proc/cpuinfo 2>/dev/null || 1) && \
  docker-php-ext-install -j${NPROC} gd

RUN docker-php-source extract
RUN docker-php-ext-install mysqli pdo_mysql mbstring

RUN apk add --no-cache zlib-dev libzip-dev
RUN docker-php-ext-install zip

RUN mkdir -p /usr/local/etc/php/conf.d
COPY conf.d/settings.ini /usr/local/etc/php/conf.d/settings.ini

RUN mkdir -p /var/www/blog
