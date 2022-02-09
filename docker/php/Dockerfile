FROM php:8.0-fpm

RUN apt-get update && apt-get install -y libcurl3-dev curl libzip-dev zip libwebp-dev libonig-dev libpq-dev libz-dev libmemcached-dev  git \
    && docker-php-ext-install iconv mbstring pdo_mysql zip curl exif && pecl install memcached && docker-php-ext-enable memcached

RUN apt-get install -y build-essential libssl-dev zlib1g-dev libpng-dev libjpeg-dev libfreetype6-dev
RUN docker-php-ext-configure gd --enable-gd --with-freetype --with-jpeg --with-webp && \
    docker-php-ext-install gd && \
    docker-php-ext-enable gd

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
ADD docker/php/php.ini /usr/local/etc/php/conf.d/40-custom.ini

WORKDIR /app
CMD ["php-fpm"]
