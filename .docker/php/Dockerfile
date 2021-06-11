FROM php:7.4-fpm-alpine
WORKDIR /var/www

RUN apk update && apk add build-base libzip-dev libjpeg-turbo-dev zip unzip jpegoptim optipng pngquant gifsicle vim unzip git curl libxml2-dev

RUN docker-php-ext-install pdo pdo_mysql pcntl bcmath exif mysqli xml soap

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

COPY .docker/php/local.ini /usr/local/etc/php/conf.d/local.ini
RUN rm -rf .git

RUN addgroup -g 1000 -S www && \
    adduser -u 1000 -S www -G www

USER 1000

COPY --chown=www:www . /var/www


EXPOSE 9000