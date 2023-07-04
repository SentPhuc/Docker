FROM php:8.1.17-fpm-alpine3.16


# Add user
ARG uid
ARG user

# RUN adduser -D -u ${uid} -g 1000 ${user}
RUN addgroup --system --gid 1000 www-data
RUN adduser --system --uid 1000 www-data

# Install dependency
RUN apk add zlib-dev libpng-dev oniguruma-dev zip unzip libzip-dev \
    && docker-php-ext-configure pcntl --enable-pcntl \
    && pecl install xdebug-3.1.5 \
    && docker-php-ext-enable xdebug \
    && docker-php-ext-install gd mbstring mysqli pdo pdo_mysql sockets zip pcntl

COPY ./ini/ /usr/local/etc/php/

RUN apk update && apk add nodejs npm && npm -g i yarn

# Create system user to run Composer and Artisan Commands
# Install composer
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
    && php composer-setup.php \
    && mv composer.phar /usr/local/bin/composer


# Default workdir
WORKDIR /srv