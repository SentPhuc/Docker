FROM php:7.4.33-fpm-alpine3.16

# Add user
ARG uid
ARG user

# RUN addgroup -g 1000 cuongdang
# RUN adduser -D -u ${uid} -g 1000 ${user}

# Install dependency
RUN apk add zlib-dev libpng-dev oniguruma-dev imagemagick zip unzip libzip-dev icu-dev \
    && docker-php-ext-configure pcntl --enable-pcntl \
    && docker-php-ext-configure intl \
    && pecl install xdebug-3.1.5 \
    && docker-php-ext-enable xdebug \
    && docker-php-ext-install gd mbstring mysqli pdo pdo_mysql sockets exif zip pcntl intl

COPY ./ini/ /usr/local/etc/php/

RUN apk update && apk add nodejs npm && npm -g i yarn

# Create system user to run Composer and Artisan Commands
# Install composer
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
    && php composer-setup.php \
    && mv composer.phar /usr/local/bin/composer

# Default workdir
WORKDIR /srv